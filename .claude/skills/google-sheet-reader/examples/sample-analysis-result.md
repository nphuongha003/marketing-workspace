# Kết Quả Phân Tích — Đọc File `examples/sample-google-sheet.csv`

> File này minh họa **output thật** của Tool mô phỏng Google Sheet Reader khi "đọc" file
> `sample-google-sheet.csv` (2 chiến dịch Facebook Ads, 7 ngày: 2026-07-21 → 2026-07-27).
> Đây là ví dụ end-to-end theo đúng luồng xử lý mô tả tại `docs/google-sheet-guide.md`:
> Đọc dữ liệu → Hiển thị dữ liệu → Kiểm tra dữ liệu → Tóm tắt KPI → Phân tích → Nhận xét → Đề xuất tối ưu.

---

## Bước 1–2: Đọc & Hiển thị dữ liệu

Đã "đọc" thành công file CSV, gồm **14 dòng dữ liệu**, **2 chiến dịch**, khoảng thời gian
**21/07/2026 – 27/07/2026**. Dữ liệu được hiển thị lại như sau:

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

*(Đơn vị: Spend/CPC/CPA theo VND)*

---

## Bước 3: Kiểm tra dữ liệu (theo `checklist/data-checklist.md`)

```
Tình trạng dữ liệu: Đạt yêu cầu

Vấn đề phát hiện: Không có
- Đủ 9 cột bắt buộc, không có ô trống.
- Không có giá trị âm hoặc vô lý (Clicks < Impressions, Conversions < Clicks ở mọi dòng).
- Không có dòng trùng lặp.
- Định dạng ngày (YYYY-MM-DD) và số nhất quán trên toàn bộ 14 dòng.
- Không có cột Revenue → không tính được ROAS, đã ghi nhận là giới hạn của dữ liệu.

Đề xuất xử lý: Có thể tiến hành tóm tắt KPI và phân tích ngay.
```

---

## Bước 4: Tóm tắt KPI chính

### Theo từng chiến dịch (tổng 7 ngày)

| Chỉ số | FB Ads - Sale Thang 7 | FB Ads - Nhan Dien Thuong Hieu |
|--------|----------------------:|-------------------------------:|
| Tổng Impressions | 358.000 | 288.000 |
| Tổng Clicks | 5.080 | 4.915 |
| CTR trung bình | 1,42% | 1,71% |
| CPC trung bình | 1.551 VND | 1.184 VND |
| Tổng Spend | 7.880.000 VND | 5.820.000 VND |
| Tổng Conversions | 95 | 175 |
| CPA trung bình | 82.947 VND | 33.257 VND |

### Tổng hợp toàn bộ 2 chiến dịch

| Chỉ số | Giá trị |
|--------|--------:|
| Tổng Impressions | 646.000 |
| Tổng Clicks | 9.995 |
| CTR trung bình | 1,55% |
| Tổng Spend | 13.700.000 VND |
| CPC trung bình | 1.371 VND |
| Tổng Conversions | 270 |
| CPA trung bình | 50.741 VND |
| ROAS | Không đủ dữ liệu (thiếu cột Doanh thu) |

*(CTR/CPC/CPA tổng hợp được tính từ tổng tử số/mẫu số theo đúng nguyên tắc ở `docs/metrics-guide.md`,
không phải trung bình cộng các dòng.)*

---

## Bước 5: Phân tích hiệu quả chiến dịch

- **"FB Ads - Nhan Dien Thuong Hieu"** hiệu quả hơn rõ rệt: CPA thấp hơn ~60% (33.257đ so với
  82.947đ) và CTR cao hơn (1,71% so với 1,42%) so với **"FB Ads - Sale Thang 7"**, dù tổng chi phí
  thấp hơn (5.82 triệu so với 7.88 triệu).
- **Xu hướng theo thời gian trái ngược nhau:**
  - *FB Ads - Sale Thang 7*: CTR giảm dần (1,50% → 1,35%), CPA tăng dần mạnh (65.625đ → 120.000đ,
    tăng ~83% sau 7 ngày) trong khi Spend vẫn tăng đều mỗi ngày. Đây là dấu hiệu **ad fatigue** rõ rệt.
  - *FB Ads - Nhan Dien Thuong Hieu*: CTR ổn định quanh 1,69–1,73%, Conversions tăng dần (22 → 28),
    CPA có xu hướng giảm nhẹ (35.455đ → 31.429đ) — hiệu suất đang cải thiện theo thời gian.
- **Điểm bất thường đáng chú ý:** Ở "FB Ads - Sale Thang 7", 3 ngày cuối (25–27/07) có Conversions
  giảm liên tục (12 → 11 → 10) trong khi Spend vẫn tăng — chi phí bỏ ra ngày càng kém hiệu quả.

---

## Bước 6: Nhận xét

- **Điểm tích cực:** Chiến dịch "FB Ads - Nhan Dien Thuong Hieu" đang vận hành hiệu quả và có xu
  hướng cải thiện dần theo thời gian, đáng để tăng đầu tư.
- **Điểm cần lưu ý:** Chiến dịch "FB Ads - Sale Thang 7" có dấu hiệu ad fatigue rõ ràng — CTR giảm,
  CPA tăng liên tục trong khi ngân sách vẫn tăng, dẫn đến hiệu quả sử dụng ngân sách ngày càng kém.
- **Giới hạn của phân tích:** Không có cột Doanh thu nên chưa thể đánh giá ROAS/AOV; nhận xét trên
  chỉ dựa trên chi phí và số lượng chuyển đổi, chưa phản ánh giá trị đơn hàng thực tế.

---

## Bước 7: Đề xuất hướng tối ưu

| Nhóm tối ưu | Đề xuất | Ưu tiên |
|-------------|---------|---------|
| Ngân sách | Dịch chuyển một phần ngân sách từ "FB Ads - Sale Thang 7" sang "FB Ads - Nhan Dien Thuong Hieu" do CPA chênh lệch lớn | Cao |
| Creative | Làm mới creative cho "FB Ads - Sale Thang 7" để khắc phục CTR giảm liên tục 7 ngày | Cao |
| Targeting | Rà soát lại đối tượng mục tiêu của "FB Ads - Sale Thang 7", có thể đang bị thu hẹp/lặp lại đối tượng đã tiếp cận | Trung bình |
| Bidding | Theo dõi thêm "FB Ads - Nhan Dien Thuong Hieu" để cân nhắc tăng ngân sách mà vẫn giữ CPA thấp | Trung bình |
| Dữ liệu | Bổ sung cột Doanh thu (Revenue) ở lần export tiếp theo để tính được ROAS chính xác | Thấp |

---

*Kết quả trên được tạo bởi Tool mô phỏng `google-sheet-reader` từ dữ liệu CSV thật đính kèm
(`examples/sample-google-sheet.csv`), không qua kết nối API hay MCP.*
