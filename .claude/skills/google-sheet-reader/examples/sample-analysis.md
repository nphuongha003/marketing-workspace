# Ví dụ: Phân tích mẫu hiệu suất chiến dịch (Dữ liệu minh họa)

> Đây là ví dụ minh họa cho toàn bộ quy trình mô tả trong `SKILL.md`, sử dụng dữ liệu giả định
> để minh họa cách áp dụng checklist, tính KPI, phân tích và đề xuất tối ưu.

## Dữ liệu đầu vào (giả định)

Người dùng cung cấp bảng dữ liệu daily breakdown của 2 chiến dịch Facebook Ads trong 7 ngày:

| Ngày | Chiến dịch | Spend (VND) | Impressions | Clicks | Conversions | Revenue (VND) |
|------|-----------|-------------|-------------|--------|--------------|----------------|
| 2026-07-20 | Chiến dịch A - Mùa hè | 1.200.000 | 60.000 | 900 | 18 | 5.400.000 |
| 2026-07-21 | Chiến dịch A - Mùa hè | 1.250.000 | 62.000 | 880 | 16 | 4.800.000 |
| 2026-07-22 | Chiến dịch A - Mùa hè | 1.300.000 | 61.500 | 850 | 15 | 4.500.000 |
| 2026-07-20 | Chiến dịch B - Sale sốc | 800.000 | 45.000 | 700 | 25 | 8.750.000 |
| 2026-07-21 | Chiến dịch B - Sale sốc | 850.000 | 46.500 | 690 | 24 | 8.400.000 |
| 2026-07-22 | Chiến dịch B - Sale sốc | 900.000 | 47.000 | 650 | 20 | 7.000.000 |

## Bước 2 — Kết quả kiểm tra dữ liệu (theo `checklist/data-checklist.md`)

```
Tình trạng dữ liệu: Đạt yêu cầu

Vấn đề phát hiện: Không có
Ảnh hưởng đến phân tích: Không có
Đề xuất xử lý: Có thể tiến hành phân tích ngay
```

## Bước 3 — Tóm tắt KPI chính (tổng 3 ngày)

| Chỉ số | Chiến dịch A - Mùa hè | Chiến dịch B - Sale sốc |
|--------|------------------------|---------------------------|
| Tổng Spend | 3.750.000 VND | 2.550.000 VND |
| Tổng Impressions | 183.500 | 138.500 |
| Tổng Clicks | 2.630 | 2.040 |
| CTR | 1,43% | 1,47% |
| CPC | 1.426 VND | 1.250 VND |
| Tổng Conversions | 49 | 69 |
| CPA | 76.531 VND | 36.957 VND |
| Tổng Revenue | 14.700.000 VND | 24.150.000 VND |
| ROAS | 3,92x | 9,47x |

## Bước 4 — Phân tích hiệu quả

- **Chiến dịch B - Sale sốc** có CPA thấp hơn đáng kể (~52%) và ROAS cao gấp ~2,4 lần so với Chiến dịch A,
  dù chi phí thấp hơn.
- Cả hai chiến dịch có xu hướng **Conversions giảm dần theo từng ngày** (A: 18 → 16 → 15;
  B: 25 → 24 → 20), trong khi Spend vẫn tăng nhẹ — cho thấy dấu hiệu hiệu suất đang giảm.
- CTR của cả hai chiến dịch tương đối ổn định quanh mức 1,4–1,5%, chưa có dấu hiệu bất thường ở chỉ số này.

## Bước 5 — Nhận xét

- **Điểm tích cực:** Chiến dịch B đang mang lại hiệu quả đầu tư tốt hơn rõ rệt (ROAS 9,47x).
- **Điểm cần lưu ý:** Conversions của cả hai chiến dịch giảm dần trong khi Spend tăng, làm CPA có xu hướng
  tăng theo thời gian — cần theo dõi thêm để xác nhận đây có phải xu hướng dài hạn hay biến động ngắn hạn.
- **Giới hạn:** Dữ liệu mẫu chỉ có 3 ngày, chưa đủ để khẳng định chắc chắn xu hướng dài hạn.

## Bước 6 — Đề xuất tối ưu (rút gọn)

| Nhóm tối ưu | Đề xuất | Ưu tiên |
|-------------|---------|---------|
| Ngân sách | Ưu tiên tăng ngân sách cho Chiến dịch B nhờ ROAS vượt trội | Cao |
| Targeting | Rà soát lại đối tượng của Chiến dịch A do CPA cao hơn 2 lần so với B | Trung bình |
| Creative | Theo dõi thêm 3–5 ngày tới để xác nhận xu hướng giảm Conversions có liên quan đến ad fatigue | Trung bình |
| Bidding | Giữ nguyên chiến lược đấu giá hiện tại, chưa có dấu hiệu bất thường ở CPC | Thấp |

## Bước 7 — Sinh báo cáo

Báo cáo hoàn chỉnh cho ví dụ này sẽ được trình bày theo khung `templates/report-template.md` và
lưu tại `outputs/bao-cao-hieu-suat-mua-he-sale-soc-2026-07-22.md` (ví dụ minh họa, không có file
thực tế được tạo sẵn trong thư mục `outputs/`).
