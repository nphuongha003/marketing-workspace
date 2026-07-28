# Báo Cáo Hiệu Suất Chiến Dịch Quảng Cáo

- **Tài khoản/Khách hàng:** Demo Client (chạy thử Tool `google-sheet-reader`)
- **Chiến dịch/Phạm vi phân tích:** 2 chiến dịch — "FB Ads - Sale Thang 7" và "FB Ads - Nhan Dien Thuong Hieu"
- **Kênh quảng cáo:** Facebook Ads
- **Khoảng thời gian:** 2026-07-21 — 2026-07-27 (7 ngày)
- **Ngày lập báo cáo:** 2026-07-28
- **Người thực hiện:** Tool `google-sheet-reader` (chạy thử end-to-end từ `examples/sample-google-sheet.csv`)

---

## 1. Tổng quan dữ liệu đầu vào

- **Nguồn dữ liệu:** File CSV mô phỏng export từ Google Sheet — `examples/sample-google-sheet.csv`
- **Tình trạng dữ liệu sau kiểm tra:** Đạt yêu cầu (chi tiết kết quả checklist ở mục 1.2)
- **Ghi chú về dữ liệu:** Không có cột Doanh thu (Revenue) → không tính được ROAS/AOV cho các mục KPI liên quan

### 1.1. Dữ liệu gốc đã đọc từ CSV (14 dòng)

| Date | Campaign | Impressions | Clicks | CTR | CPC | Spend | Conversions | CPA |
|------|----------|------------:|-------:|----:|----:|------:|------------:|----:|
| 2026-07-21 | FB Ads - Sale Thang 7 | 52.000 | 780 | 1,50% | 1.346 | 1.050.000 | 16 | 65.625 |
| 2026-07-22 | FB Ads - Sale Thang 7 | 54.000 | 760 | 1,41% | 1.447 | 1.100.000 | 15 | 73.333 |
| 2026-07-23 | FB Ads - Sale Thang 7 | 51.000 | 740 | 1,45% | 1.459 | 1.080.000 | 14 | 77.143 |
| 2026-07-24 | FB Ads - Sale Thang 7 | 53.500 | 770 | 1,44% | 1.455 | 1.120.000 | 17 | 65.882 |
| 2026-07-25 | FB Ads - Sale Thang 7 | 50.500 | 700 | 1,39% | 1.643 | 1.150.000 | 12 | 95.833 |
| 2026-07-26 | FB Ads - Sale Thang 7 | 49.000 | 680 | 1,39% | 1.735 | 1.180.000 | 11 | 107.273 |
| 2026-07-27 | FB Ads - Sale Thang 7 | 48.000 | 650 | 1,35% | 1.846 | 1.200.000 | 10 | 120.000 |
| 2026-07-21 | FB Ads - Nhan Dien Thuong Hieu | 38.000 | 650 | 1,71% | 1.200 | 780.000 | 22 | 35.455 |
| 2026-07-22 | FB Ads - Nhan Dien Thuong Hieu | 39.500 | 670 | 1,70% | 1.194 | 800.000 | 24 | 33.333 |
| 2026-07-23 | FB Ads - Nhan Dien Thuong Hieu | 40.000 | 690 | 1,73% | 1.188 | 820.000 | 25 | 32.800 |
| 2026-07-24 | FB Ads - Nhan Dien Thuong Hieu | 41.000 | 700 | 1,71% | 1.186 | 830.000 | 23 | 36.087 |
| 2026-07-25 | FB Ads - Nhan Dien Thuong Hieu | 42.500 | 720 | 1,69% | 1.181 | 850.000 | 26 | 32.692 |
| 2026-07-26 | FB Ads - Nhan Dien Thuong Hieu | 43.000 | 735 | 1,71% | 1.170 | 860.000 | 27 | 31.852 |
| 2026-07-27 | FB Ads - Nhan Dien Thuong Hieu | 44.000 | 750 | 1,70% | 1.173 | 880.000 | 28 | 31.429 |

*(Đơn vị: Spend/CPC/CPA/CPM theo VND)*

### 1.2. Kết quả kiểm tra dữ liệu (theo `checklist/data-checklist.md`)

```
Tình trạng dữ liệu: Đạt yêu cầu

Vấn đề phát hiện:
- Không có ô trống ở 9 cột bắt buộc (Date, Campaign, Impressions, Clicks, CTR, CPC, Spend, Conversions, CPA).
- Không có giá trị âm, không có Clicks > Impressions hay Conversions > Clicks ở bất kỳ dòng nào.
- Không có dòng trùng lặp (14 dòng = 2 chiến dịch x 7 ngày, đúng kỳ vọng).
- Tên chiến dịch nhất quán trên toàn bộ 7 dòng của mỗi chiến dịch.
- Định dạng ngày (YYYY-MM-DD) và định dạng số nhất quán trên toàn bộ bảng.
- Thiếu cột Doanh thu (Revenue) → không tính được ROAS/AOV.

Ảnh hưởng đến phân tích:
- Không ảnh hưởng đến việc tính CTR, CPC, CPM, CPA và phân tích xu hướng/so sánh hiệu quả.
- Không thể đánh giá hiệu quả kinh doanh cuối cùng (doanh thu, ROAS) ở báo cáo này.

Đề xuất xử lý trước khi tiếp tục:
- Tiến hành tóm tắt KPI và phân tích ngay với các chỉ số hiện có; khuyến nghị bổ sung cột Doanh thu
  ở lần cung cấp dữ liệu tiếp theo.
```

---

## 2. Tóm tắt KPI chính

### 2.1. Theo từng chiến dịch (tổng 7 ngày)

| Chỉ số | FB Ads - Sale Thang 7 | FB Ads - Nhan Dien Thuong Hieu |
|--------|----------------------:|-------------------------------:|
| Tổng Impressions | 358.000 | 288.000 |
| Tổng Clicks | 5.080 | 4.915 |
| CTR trung bình | 1,42% | 1,71% |
| CPC trung bình | 1.551 VND | 1.184 VND |
| CPM trung bình | 22.011 VND | 20.208 VND |
| Tổng Spend | 7.880.000 VND | 5.820.000 VND |
| Tổng Conversions | 95 | 175 |
| CPA trung bình | 82.947 VND | 33.257 VND |

### 2.2. Tổng hợp toàn bộ (dùng cho bảng chuẩn của báo cáo)

| Chỉ số | Giá trị kỳ này | Giá trị kỳ trước | Thay đổi |
|--------|----------------:|:-----------------:|:---------:|
| Tổng chi phí (Spend) | 13.700.000 VND | Không có dữ liệu kỳ trước | — |
| Impressions | 646.000 | Không có dữ liệu kỳ trước | — |
| Clicks | 9.995 | Không có dữ liệu kỳ trước | — |
| CTR | 1,55% | Không có dữ liệu kỳ trước | — |
| CPC | 1.371 VND | Không có dữ liệu kỳ trước | — |
| CPM | 21.207 VND | Không có dữ liệu kỳ trước | — |
| Conversions | 270 | Không có dữ liệu kỳ trước | — |
| CPA | 50.741 VND | Không có dữ liệu kỳ trước | — |
| Doanh thu (Revenue) | Không đủ dữ liệu (thiếu cột Doanh thu) | — | — |
| ROAS | Không đủ dữ liệu (thiếu cột Doanh thu) | — | — |

*(CTR/CPC/CPM/CPA tổng hợp được tính từ tổng tử số/mẫu số theo đúng nguyên tắc ở `docs/metrics-guide.md`,
không phải trung bình cộng các dòng riêng lẻ. Đây là lần chạy đầu tiên trên bộ dữ liệu mẫu nên chưa có
kỳ trước để so sánh.)*

---

## 3. Phân tích hiệu quả chiến dịch

### 3.1. So sánh giữa các chiến dịch/nhóm quảng cáo

"FB Ads - Nhan Dien Thuong Hieu" hiệu quả hơn rõ rệt so với "FB Ads - Sale Thang 7":

- CPA thấp hơn ~60% (33.257đ so với 82.947đ).
- CTR cao hơn (1,71% so với 1,42%).
- Tổng Conversions cao hơn gần gấp đôi (175 so với 95), trong khi tổng Spend lại **thấp hơn**
  (5,82 triệu so với 7,88 triệu).

### 3.2. Xu hướng theo thời gian

- **FB Ads - Sale Thang 7:** CTR giảm dần liên tục suốt 7 ngày (1,50% → 1,35%), CPA tăng dần mạnh
  (65.625đ → 120.000đ, tăng ~83%) trong khi Spend theo ngày vẫn tăng đều — đây là dấu hiệu điển hình
  của **ad fatigue** (creative "mỏi").
- **FB Ads - Nhan Dien Thuong Hieu:** CTR ổn định quanh 1,69–1,73% trong suốt 7 ngày, Conversions tăng
  dần đều (22 → 28), CPA có xu hướng giảm nhẹ (35.455đ → 31.429đ) — hiệu suất đang cải thiện theo thời gian.

### 3.3. Điểm bất thường phát hiện được

- Ở "FB Ads - Sale Thang 7", 3 ngày cuối kỳ (25–27/07) Conversions giảm liên tục (12 → 11 → 10) trong
  khi Spend vẫn tiếp tục tăng — ngân sách ngày càng kém hiệu quả, cần can thiệp sớm.
- Không phát hiện bất thường ở "FB Ads - Nhan Dien Thuong Hieu" trong kỳ dữ liệu này.

---

## 4. Nhận xét

- **Điểm tích cực:**
  - "FB Ads - Nhan Dien Thuong Hieu" vận hành hiệu quả và có xu hướng cải thiện dần theo thời gian
    (CTR ổn định, CPA giảm nhẹ, Conversions tăng đều).
- **Điểm cần lưu ý/hạn chế:**
  - "FB Ads - Sale Thang 7" có dấu hiệu ad fatigue rõ ràng: CTR giảm liên tục, CPA tăng gần gấp đôi
    chỉ trong 7 ngày, trong khi ngân sách vẫn tiếp tục tăng.
  - Thiếu cột Doanh thu nên chưa thể khẳng định hiệu quả kinh doanh thực tế (ROAS/AOV) của cả hai
    chiến dịch — nhận xét trên chỉ dựa trên chi phí và số lượng chuyển đổi.
- **Nguyên nhân có thể (dựa trên dữ liệu):**
  - CTR giảm và CPA tăng đồng thời ở "FB Ads - Sale Thang 7" trong khi CPC cũng tăng dần (1.346đ →
    1.846đ) gợi ý creative đang giảm sức hút với cùng một nhóm đối tượng, không phải do cạnh tranh
    đấu giá tăng đột biến từ bên ngoài.

---

## 5. Đề xuất hướng tối ưu

> Chi tiết đầy đủ theo khung `templates/optimization-template.md`

### 5.1. Tối ưu ngân sách (Budget)

- **Quan sát:** "FB Ads - Nhan Dien Thuong Hieu" có CPA thấp hơn ~60% và Conversions cao hơn gần gấp
  đôi so với "FB Ads - Sale Thang 7", dù Spend thấp hơn.
- **Đề xuất:** Dịch chuyển một phần ngân sách từ "FB Ads - Sale Thang 7" sang "FB Ads - Nhan Dien
  Thuong Hieu".
- **Ưu tiên:** Cao
- **Kỳ vọng:** Tăng tổng số Conversions mà không cần tăng tổng ngân sách.

### 5.2. Tối ưu đối tượng mục tiêu (Targeting)

- **Quan sát:** CTR của "FB Ads - Sale Thang 7" giảm liên tục 7 ngày, có thể do đối tượng đang bị
  lặp lại/thu hẹp.
- **Đề xuất:** Rà soát và mở rộng lại đối tượng mục tiêu của "FB Ads - Sale Thang 7", cân nhắc loại
  trừ nhóm đã tiếp cận nhiều lần.
- **Ưu tiên:** Trung bình
- **Kỳ vọng:** Khôi phục CTR về gần mức ban đầu (~1,50%).

### 5.3. Tối ưu nội dung quảng cáo (Creative)

- **Quan sát:** CTR giảm liên tục kèm CPA tăng gần gấp đôi trong 7 ngày ở "FB Ads - Sale Thang 7" —
  dấu hiệu ad fatigue.
- **Đề xuất:** Làm mới creative (hình ảnh/video/copy) cho "FB Ads - Sale Thang 7" càng sớm càng tốt.
- **Ưu tiên:** Cao
- **Kỳ vọng:** Khôi phục CTR và kéo CPA về gần mức đầu kỳ (~65.000 VND).

### 5.4. Tối ưu chiến lược đấu giá (Bidding)

- **Quan sát:** CPC của "FB Ads - Sale Thang 7" tăng dần đều (1.346đ → 1.846đ) cùng lúc với CTR giảm,
  nhiều khả năng do chất lượng quảng cáo giảm chứ không phải do cạnh tranh đấu giá.
- **Đề xuất:** Chưa cần đổi chiến lược đấu giá ngay; theo dõi thêm sau khi làm mới creative (mục 5.3)
  để xác nhận CPC có tự điều chỉnh về mức hợp lý hay không.
- **Ưu tiên:** Thấp — *giả thuyết cần kiểm chứng thêm sau khi áp dụng đề xuất Creative.*
- **Kỳ vọng:** Ổn định lại CPC quanh mức 1.300–1.400 VND.

### 5.5. Tối ưu trang đích/phễu chuyển đổi (Landing Page/Funnel)

- **Quan sát:** Không có dữ liệu về hành vi sau click (bounce rate, thời gian trên trang) trong bộ
  dữ liệu hiện tại.
- **Đề xuất:** Bổ sung dữ liệu phễu chuyển đổi ở lần thu thập tiếp theo để đánh giá liệu Conversions
  giảm ở "FB Ads - Sale Thang 7" có liên quan đến trang đích hay không.
- **Ưu tiên:** Thấp — *giả thuyết cần kiểm chứng thêm, hiện chưa đủ dữ liệu.*
- **Kỳ vọng:** Xác định thêm nguyên nhân ngoài creative/targeting nếu có.

### 5.6. Bảng tổng hợp (theo cấu trúc chuẩn của báo cáo)

| Nhóm tối ưu | Đề xuất | Ưu tiên |
|-------------|---------|---------|
| Ngân sách (Budget) | Dịch chuyển ngân sách từ "Sale Thang 7" sang "Nhan Dien Thuong Hieu" | Cao |
| Đối tượng mục tiêu (Targeting) | Mở rộng/rà soát lại đối tượng của "Sale Thang 7" | Trung bình |
| Nội dung quảng cáo (Creative) | Làm mới creative cho "Sale Thang 7" | Cao |
| Chiến lược đấu giá (Bidding) | Theo dõi thêm sau khi làm mới creative, chưa cần đổi ngay | Thấp |
| Trang đích/Phễu chuyển đổi (Landing Page/Funnel) | Bổ sung dữ liệu phễu chuyển đổi ở kỳ sau | Thấp |

### 5.7. Bảng tổng hợp ưu tiên hành động

| Thứ tự | Hành động | Nhóm | Ưu tiên |
|--------|-----------|------|---------|
| 1 | Làm mới creative cho "FB Ads - Sale Thang 7" | Creative | Cao |
| 2 | Dịch chuyển một phần ngân sách sang "FB Ads - Nhan Dien Thuong Hieu" | Budget | Cao |
| 3 | Rà soát/mở rộng đối tượng mục tiêu của "FB Ads - Sale Thang 7" | Targeting | Trung bình |
| 4 | Theo dõi CPC sau khi làm mới creative trước khi đổi chiến lược đấu giá | Bidding | Thấp |
| 5 | Bổ sung cột Doanh thu và dữ liệu phễu chuyển đổi ở kỳ thu thập tiếp theo | Dữ liệu/Funnel | Thấp |

---

## 6. Kết luận

Trong 7 ngày (21–27/07/2026), "FB Ads - Nhan Dien Thuong Hieu" là chiến dịch hiệu quả hơn rõ rệt và
đang cải thiện dần, trong khi "FB Ads - Sale Thang 7" có dấu hiệu ad fatigue rõ ràng (CTR giảm, CPA
tăng gần gấp đôi) dù ngân sách vẫn tăng đều mỗi ngày. Bước tiếp theo được đề xuất: **làm mới creative
và dịch chuyển một phần ngân sách** cho "FB Ads - Sale Thang 7" ngay trong kỳ tới, đồng thời bổ sung
cột Doanh thu ở lần cung cấp dữ liệu sau để có thể đánh giá đầy đủ ROAS.

---

*Báo cáo được tạo tự động bởi Tool mô phỏng `google-sheet-reader`, đọc dữ liệu thật từ file CSV
`examples/sample-google-sheet.csv` (chưa qua kết nối API hay MCP thời gian thực).*
