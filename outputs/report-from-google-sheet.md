# Báo cáo hiệu quả quảng cáo

**Khách hàng:** Demo Client (dữ liệu chạy thử end-to-end workflow cuối khóa)
**Kênh:** Facebook Ads
**Giai đoạn báo cáo:** 21/07/2026 - 27/07/2026
**Người thực hiện:** Performance Marketing Agent (qua Tool `google-sheet-reader` + Skill `ads-report`)

---

## 1. Tổng quan

- Mục tiêu chiến dịch trong giai đoạn này: "FB Ads - Sale Thang 7" tập trung chuyển đổi/doanh số; "FB Ads - Nhan Dien Thuong Hieu" tập trung nhận diện thương hiệu kèm chuyển đổi phụ.
- Ngân sách đã chi: 13.700.000đ (7.880.000đ cho Sale Thang 7 + 5.820.000đ cho Nhan Dien Thuong Hieu) / Ngân sách kế hoạch: không có (dữ liệu demo, chưa có ngân sách kế hoạch để đối chiếu).
- Tóm tắt nhanh kết quả: Kết quả trái chiều giữa 2 chiến dịch — "FB Ads - Nhan Dien Thuong Hieu" hiệu quả và cải thiện dần, trong khi "FB Ads - Sale Thang 7" có dấu hiệu giảm hiệu quả rõ rệt (CTR giảm, CPA tăng gần gấp đôi) trong 7 ngày.

## 2. Phân tích chỉ số

*Nguồn dữ liệu: File CSV mô phỏng Google Sheet (`examples/sample-google-sheet.csv`), đọc qua Tool `google-sheet-reader` — 21/07/2026 - 27/07/2026*

| Chỉ số | Mục tiêu (nếu có) | Kỳ này | Kỳ trước | Thay đổi |
|---|---|---|---|---|
| Impression | — | 646.000 | Không có dữ liệu | — |
| CTR | — | 1,55% | Không có dữ liệu | — |
| CPC | — | 1.371đ | Không có dữ liệu | — |
| CPM | — | 21.207đ | Không có dữ liệu | — |
| Conversion | — | 270 | Không có dữ liệu | — |
| Conversion Rate | — | 2,70% | Không có dữ liệu | — |
| CPA | — | 50.741đ | Không có dữ liệu | — |

> Ghi chú: Đã bỏ dòng Reach, Frequency và ROAS so với template chuẩn vì dữ liệu nguồn không có cột
> Reach và Doanh thu (Revenue). Đây là lần chạy đầu tiên trên bộ dữ liệu demo nên chưa có kỳ trước
> để so sánh — cột "Thay đổi" sẽ áp dụng từ kỳ báo cáo tiếp theo.

### Chi tiết theo từng chiến dịch (bổ sung để làm rõ nhận xét bên dưới)

| Chỉ số | FB Ads - Sale Thang 7 | FB Ads - Nhan Dien Thuong Hieu |
|---|---:|---:|
| Impression | 358.000 | 288.000 |
| CTR | 1,42% | 1,71% |
| CPC | 1.551đ | 1.184đ |
| CPM | 22.011đ | 20.208đ |
| Spend | 7.880.000đ | 5.820.000đ |
| Conversion | 95 | 175 |
| Conversion Rate | 1,87% | 3,56% |
| CPA | 82.947đ | 33.257đ |

Nhận xét chi tiết từng chỉ số:

- **CTR:** CTR trung bình toàn tài khoản đạt 1,55%, nhưng chênh lệch rõ giữa 2 chiến dịch: "Nhan Dien
  Thuong Hieu" giữ ổn định 1,69–1,73% suốt 7 ngày, trong khi "Sale Thang 7" giảm liên tục từ 1,50%
  xuống còn 1,35%.
- **CPC:** CPC trung bình 1.371đ. "Sale Thang 7" có CPC tăng dần đều (1.346đ → 1.846đ), cao hơn hẳn
  "Nhan Dien Thuong Hieu" (dao động quanh 1.170–1.200đ).
- **CPM:** CPM toàn tài khoản 21.207đ, không có biến động bất thường giữa hai chiến dịch (22.011đ so
  với 20.208đ) — mức độ cạnh tranh tiếp cận tương đối ổn định.
- **Conversion / Conversion Rate:** Conversion Rate của "Nhan Dien Thuong Hieu" (3,56%) cao gần gấp
  đôi so với "Sale Thang 7" (1,87%), dù đây không phải chiến dịch được đặt mục tiêu chuyển đổi chính.
- **CPA:** CPA của "Sale Thang 7" (82.947đ) cao hơn "Nhan Dien Thuong Hieu" (33.257đ) khoảng 2,5 lần;
  đáng lo ngại hơn là CPA của "Sale Thang 7" tăng liên tục theo từng ngày trong tuần (65.625đ → 120.000đ).

## 3. Insight

- "FB Ads - Sale Thang 7" có dấu hiệu **ad fatigue** rõ rệt: CTR giảm liên tục 7 ngày liên tiếp, CPC
  và CPA tăng đồng thời, trong khi Spend theo ngày vẫn tiếp tục tăng — ngân sách ngày càng kém hiệu quả.
- "FB Ads - Nhan Dien Thuong Hieu" đang trong đà cải thiện: CTR ổn định, CPA giảm nhẹ theo từng ngày
  (35.455đ → 31.429đ), Conversion tăng dần đều (22 → 28) — đáng để tăng đầu tư.
- Không có đủ dữ liệu về đối tượng mục tiêu hoặc khung giờ hiển thị trong bộ dữ liệu hiện tại nên chưa
  thể xác định chính xác nhóm đối tượng nào đang kéo hiệu quả "Sale Thang 7" đi xuống — cần bổ sung
  dữ liệu chi tiết hơn (theo audience/placement) ở kỳ báo cáo tới nếu muốn đào sâu insight này.

## 4. Recommendation

- Dịch chuyển một phần ngân sách từ "FB Ads - Sale Thang 7" sang "FB Ads - Nhan Dien Thuong Hieu" —
  vì CPA chênh lệch ~2,5 lần và "Nhan Dien Thuong Hieu" vẫn đang trong đà cải thiện.
- Làm mới creative cho "FB Ads - Sale Thang 7" ngay trong tuần tới để xử lý dấu hiệu ad fatigue trước
  khi CPA tiếp tục tăng thêm.
- Rà soát/mở rộng lại đối tượng mục tiêu của "FB Ads - Sale Thang 7", ưu tiên loại trừ nhóm đã tiếp
  cận nhiều lần trong 7 ngày qua.
- Theo dõi CPC của "FB Ads - Sale Thang 7" sau khi làm mới creative trước khi cân nhắc đổi chiến lược
  đấu giá — hiện chưa đủ cơ sở để khẳng định nguyên nhân là do cạnh tranh đấu giá tăng.
- Đề xuất khách hàng bổ sung cột Doanh thu (Revenue) theo từng chiến dịch ở lần cung cấp dữ liệu tiếp
  theo để có thể tính ROAS và đánh giá đầy đủ hiệu quả kinh doanh.

## 5. Việc cần làm tiếp theo

- [ ] Làm mới creative cho "FB Ads - Sale Thang 7" — Đội Content — trước 04/08/2026
- [ ] Điều chỉnh phân bổ ngân sách sang "FB Ads - Nhan Dien Thuong Hieu" — Đội Media — trước 01/08/2026
- [ ] Xác nhận với khách hàng về phương án điều chỉnh ngân sách/creative trước khi triển khai — Account/Performance Marketing Agent — trước 31/07/2026
- [ ] Yêu cầu khách hàng bổ sung dữ liệu Doanh thu theo từng chiến dịch cho kỳ báo cáo tiếp theo — Account — trước kỳ báo cáo kế tiếp

---

*Báo cáo được tạo bởi Performance Marketing Agent, sử dụng Tool `google-sheet-reader` để đọc dữ liệu
từ `examples/sample-google-sheet.csv` và Skill `ads-report` để phân tích, sinh báo cáo theo đúng
`templates/report-template.md` của Skill này. Đã rà soát theo `checklist/qa-checklist.md` của `ads-report`
trước khi bàn giao cho Client Support Agent.*
