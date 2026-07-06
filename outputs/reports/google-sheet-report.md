> **Ghi chú quan trọng — Mô phỏng quy trình:**
> Không thể truy cập Google Sheet thật tại link được cung cấp (`https://docs.google.com/spreadsheets/d/xxxxxxxx`). Khi kiểm tra quyền truy cập qua Google Drive, hệ thống trả về lỗi **"Entity not found"** — nguyên nhân là `xxxxxxxx` chỉ là Spreadsheet ID giả lập/placeholder trong yêu cầu, không phải ID của một file thật trên Google Drive.
>
> Theo đúng "Điều kiện sử dụng" trong `docs/google-sheets-integration.md` của Skill ads-report, đáng lẽ ở bước này Claude sẽ dừng lại và yêu cầu người dùng chia sẻ quyền truy cập hoặc xuất CSV/XLSX. Tuy nhiên theo yêu cầu của người dùng, toàn bộ quy trình bên dưới được **mô phỏng bằng dữ liệu giả lập** để minh hoạ cách Skill xử lý từ bước đọc dữ liệu đến khi xuất báo cáo. **Số liệu trong báo cáo này không đến từ Google Sheet thật.**

---

## Mô phỏng các bước xử lý của Skill

1. **Kiểm tra quyền truy cập** — Đã thực hiện thật: gọi công cụ truy cập Google Drive với ID `xxxxxxxx` → nhận lỗi "Entity not found". Từ bước này trở đi, quy trình chuyển sang **mô phỏng**.
2. **Đọc dữ liệu từ Google Sheets (mô phỏng)** — Giả định sheet có 1 tab dữ liệu chiến dịch Google Ads với bảng thô như sau:

   | Campaign | Impression | Click | CTR | CPC | Conversion |
   |---|---|---|---|---|---|
   | Search_Brand | 50.000 | 2.500 | 5,00% | 5.000đ | 120 |
   | Search_NonBrand | 120.000 | 3.000 | 2,50% | 8.000đ | 90 |
   | Shopping_AllProducts | 80.000 | 2.000 | 2,50% | 6.500đ | 110 |
   | Display_Awareness | 200.000 | 1.500 | 0,75% | 4.000đ | 10 |

3. **Xác định cột KPI (mô phỏng)** — Ánh xạ cột trong sheet vào chỉ số chuẩn của Skill:

   | Cột trong sheet | Chỉ số chuẩn |
   |---|---|
   | Campaign | Campaign |
   | Impression | Impression |
   | Click | Click |
   | CTR | CTR |
   | CPC | CPC |
   | Conversion | Conversion |

   Sheet giả lập **không có cột CPM và ROAS** — hai chỉ số này sẽ được ghi là "không có dữ liệu trong sheet" ở phần phân tích, không tự suy đoán hay bịa số liệu.

4. **Phân tích dữ liệu theo template của Skill** — Áp dụng `templates/report-template.md` và `docs/metrics-guide.md` để tổng hợp số liệu toàn tài khoản từ 4 chiến dịch trên.
5. **Sinh báo cáo và recommendation** — Xem báo cáo hoàn chỉnh bên dưới.

---

# Báo cáo hiệu quả quảng cáo

**Khách hàng:** [Tên khách hàng — chưa được cung cấp trong yêu cầu này]
**Kênh:** Google Ads
**Giai đoạn báo cáo:** [Chưa xác định — dữ liệu mô phỏng không có cột ngày/giai đoạn]
**Người thực hiện:** [Tên người thực hiện]

---

## 1. Tổng quan

- Mục tiêu chiến dịch trong giai đoạn này: kết hợp Search (Brand/Non-brand), Shopping và Display nhằm vừa thu hút chuyển đổi vừa tăng nhận diện thương hiệu.
- Tổng ngân sách suy ra từ dữ liệu (Click × CPC theo từng chiến dịch): **55.500.000đ**.
- Tóm tắt nhanh kết quả: Tổng cộng 330 chuyển đổi từ 9.000 click, CPA trung bình toàn tài khoản khoảng 168.182đ. Hiệu quả không đồng đều giữa các chiến dịch — Search_Brand và Shopping_AllProducts hoạt động tốt, trong khi Display_Awareness có chi phí trên mỗi chuyển đổi rất cao.

## 2. Phân tích chỉ số

*Nguồn dữ liệu: Google Sheet (mô phỏng) — không phải dữ liệu thật.*

| Chỉ số | Giá trị toàn tài khoản | Ghi chú |
|---|---|---|
| Impression | 450.000 | Tổng 4 chiến dịch |
| Click | 9.000 | |
| CTR | 2,00% | = 9.000 / 450.000 |
| CPC | 6.167đ | = 55.500.000đ / 9.000 click |
| CPM | Không có dữ liệu trong sheet | Sheet không có cột Impression cost/CPM riêng để đối chiếu |
| Conversion | 330 | |
| Conversion Rate | 3,67% | = 330 / 9.000 |
| CPA | 168.182đ | = 55.500.000đ / 330 |
| ROAS | Không có dữ liệu trong sheet | Sheet không có cột doanh thu để tính ROAS |

Chi tiết theo từng chiến dịch:

| Campaign | Impression | Click | CTR | CPC | Conversion | CPA |
|---|---|---|---|---|---|---|
| Search_Brand | 50.000 | 2.500 | 5,00% | 5.000đ | 120 | 104.167đ |
| Search_NonBrand | 120.000 | 3.000 | 2,50% | 8.000đ | 90 | 266.667đ |
| Shopping_AllProducts | 80.000 | 2.000 | 2,50% | 6.500đ | 110 | 118.182đ |
| Display_Awareness | 200.000 | 1.500 | 0,75% | 4.000đ | 10 | 600.000đ |

Nhận xét chi tiết từng chỉ số:

- **CTR:** CTR trung bình toàn tài khoản 2,00%, nhưng chênh lệch lớn giữa các chiến dịch — Search_Brand đạt 5,00% (rất tốt, đúng như kỳ vọng với từ khoá thương hiệu), trong khi Display_Awareness chỉ 0,75% (khá thấp, đặc trưng của định dạng display).
- **CPC:** CPC trung bình 6.167đ. Search_Brand có CPC thấp nhất (5.000đ) nhờ CTR cao và mức độ liên quan tốt; Search_NonBrand có CPC cao nhất (8.000đ) do cạnh tranh từ khoá không thương hiệu thường gay gắt hơn.
- **CPM:** Không có dữ liệu trong sheet mô phỏng để tính hoặc đối chiếu chỉ số này.
- **Conversion/Conversion Rate:** Tổng 330 chuyển đổi, tỷ lệ chuyển đổi trung bình 3,67%. Search_Brand và Shopping_AllProducts đóng góp phần lớn chuyển đổi với chi phí hợp lý; Display_Awareness chỉ đóng góp 10 chuyển đổi dù chiếm tới 200.000 impression, cho thấy kênh này đang đóng vai trò nhận diện thương hiệu nhiều hơn là thúc đẩy chuyển đổi trực tiếp.
- **CPA:** CPA trung bình 168.182đ, nhưng Display_Awareness có CPA rất cao (600.000đ) — cần đánh giá lại xem chi phí này có phù hợp với vai trò "nhận diện thương hiệu" của kênh hay đang lãng phí ngân sách.
- **ROAS:** Không có dữ liệu trong sheet mô phỏng để tính chỉ số này.

## 3. Insight

- Search_Brand là chiến dịch hiệu quả nhất trên mọi mặt (CTR cao nhất, CPC và CPA thấp nhất) — đúng như đặc điểm chung của quảng cáo từ khoá thương hiệu.
- Display_Awareness có CPA cao gấp gần 6 lần mức trung bình toàn tài khoản, trong khi chiếm tới ~44% tổng impression — cần làm rõ với khách hàng liệu ngân sách này đang được kỳ vọng cho mục tiêu nhận diện (không nên đánh giá bằng CPA) hay cần tối ưu lại nhắm mục tiêu/creative.
- Không có dữ liệu CPM và ROAS trong sheet khiến chưa thể đánh giá đầy đủ hiệu quả chi phí hiển thị và hiệu quả kinh doanh thực tế của toàn chiến dịch.

## 4. Recommendation

- Ưu tiên tăng ngân sách cho Search_Brand và Shopping_AllProducts — hai chiến dịch có CPA thấp nhất và đang hoạt động ổn định.
- Rà soát lại targeting/creative của Display_Awareness; nếu mục tiêu là nhận diện thương hiệu, nên đánh giá bằng Reach/Impression thay vì CPA, đồng thời cân nhắc giảm ngân sách nếu không phục vụ mục tiêu chuyển đổi.
- Đề xuất khách hàng bổ sung cột doanh thu (để tính ROAS) và chi phí hiển thị (để tính CPM) vào Google Sheet cho các kỳ báo cáo tiếp theo, giúp đánh giá đầy đủ và chính xác hơn.
- Xem xét thử nghiệm thêm từ khoá non-brand có liên quan chặt hơn để cải thiện CPC của nhóm Search_NonBrand.

## 5. Việc cần làm tiếp theo

- [ ] Điều chỉnh phân bổ ngân sách ưu tiên Search_Brand và Shopping_AllProducts — Team Ads — trước 14/07/2026
- [ ] Rà soát targeting/creative của Display_Awareness — Team Ads — trước 14/07/2026
- [ ] Trao đổi với khách hàng để bổ sung cột doanh thu và chi phí hiển thị vào Google Sheet — Người phụ trách khách hàng — trước 10/07/2026
- [ ] Xác nhận lại link Google Sheet thật (link hiện tại không truy cập được) để các kỳ báo cáo sau dùng đúng dữ liệu thực — Người phụ trách khách hàng — trước 08/07/2026
