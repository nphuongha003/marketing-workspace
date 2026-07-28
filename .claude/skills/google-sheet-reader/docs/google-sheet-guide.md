# Hướng dẫn sử dụng Tool — Google Sheet Reader (Mô Phỏng)

> **Đây là tài liệu hướng dẫn sử dụng cho Tool mô phỏng (simulated tool)**, phục vụ mục đích demo/bài
> cuối khóa. Tool **chưa kết nối Google Sheets API thật** và **chưa dùng MCP** — bước "đọc Google Sheet"
> được mô phỏng bằng cách người dùng tự cung cấp dữ liệu (CSV, XLSX, hoặc bảng copy từ Google Sheets).

## 1. Hướng dẫn sử dụng Tool

### Cách gọi Tool
Người dùng kích hoạt Tool bằng cách cung cấp dữ liệu quảng cáo kèm yêu cầu phân tích, ví dụ:

- "Đọc file CSV này và tóm tắt KPI giúp mình" (đính kèm file `.csv`)
- "Đây là bảng dữ liệu mình copy từ Google Sheet, phân tích hiệu quả chiến dịch giúp mình" (dán bảng)
- "Phân tích file Excel export từ Google Sheet này và đề xuất tối ưu" (đính kèm file `.xlsx`)

### Các hình thức cung cấp dữ liệu được hỗ trợ (mô phỏng "đọc Google Sheet")

| Hình thức | Mô tả | Cách lấy dữ liệu từ Google Sheets thật |
|-----------|-------|------------------------------------------|
| File CSV đính kèm | File `.csv` export từ Google Sheet | Google Sheet → `File > Download > Comma Separated Values (.csv)` |
| File XLSX đính kèm | File `.xlsx` export từ Google Sheet | Google Sheet → `File > Download > Microsoft Excel (.xlsx)` |
| Bảng dán trực tiếp | Copy vùng dữ liệu từ Google Sheet rồi dán vào hội thoại | Chọn vùng dữ liệu trong Sheet → Copy (`Ctrl+C`) → Dán vào chat |
| Mô tả bằng lời | Người dùng mô tả số liệu chính bằng văn bản | Chỉ dùng khi không có bảng đầy đủ, độ chính xác thấp hơn |

> Vì đây là Tool mô phỏng, **không có bước tự động truy cập link Google Sheet**. Nếu người dùng chỉ
> đưa link, cần hướng dẫn họ export/copy dữ liệu theo một trong các cách ở bảng trên.

### Các bước sử dụng Tool (tóm tắt nhanh)

1. Cung cấp dữ liệu (CSV/XLSX/bảng dán) theo đúng cấu trúc cột ở mục 2.
2. Tool kiểm tra dữ liệu theo `checklist/data-checklist.md`.
3. Tool tóm tắt KPI theo `docs/metrics-guide.md`.
4. Tool phân tích hiệu quả, đưa ra nhận xét và đề xuất tối ưu theo `templates/optimization-template.md`.
5. Tool sinh báo cáo Markdown hoàn chỉnh theo `templates/report-template.md`, lưu vào `outputs/`.

Xem ví dụ đầy đủ với dữ liệu mẫu tại `examples/sample-google-sheet.csv` và kết quả tương ứng tại
`examples/sample-analysis-result.md`.

---

## 2. Mô tả dữ liệu đầu vào (Input)

### Cấu trúc cột dữ liệu tiêu chuẩn

Tên cột có thể khác nhau tùy nền tảng/nguồn, cần ánh xạ (mapping) về nhóm chuẩn bên dưới trước khi phân tích:

| Nhóm chuẩn     | Tên cột thường gặp                          | Ghi chú |
|-----------------|-----------------------------------------------|---------|
| Ngày            | `Date`, `Ngày`, `Reporting starts`             | Định dạng YYYY-MM-DD hoặc DD/MM/YYYY |
| Kênh quảng cáo  | `Channel`, `Platform`, `Nguồn`                 | Facebook Ads, Google Ads, TikTok Ads... (không bắt buộc nếu chỉ 1 kênh) |
| Tên chiến dịch  | `Campaign`, `Campaign name`, `Tên chiến dịch`  | |
| Hiển thị        | `Impressions`, `Lượt hiển thị`                 | |
| Lượt nhấp       | `Clicks`, `Lượt click`                          | |
| CTR             | `CTR`, `Click-Through Rate`                     | Có thể tính lại từ Clicks/Impressions nếu thiếu |
| CPC             | `CPC`, `Cost per Click`                         | Có thể tính lại từ Spend/Clicks nếu thiếu |
| Chi phí         | `Spend`, `Cost`, `Chi phí`, `Amount spent`      | Cần thống nhất đơn vị tiền tệ |
| Chuyển đổi      | `Conversions`, `Results`, `Chuyển đổi`          | Cần xác định loại chuyển đổi (mua hàng, lead...) |
| CPA             | `CPA`, `Cost per Acquisition`                   | Có thể tính lại từ Spend/Conversions nếu thiếu |
| Doanh thu       | `Revenue`, `Doanh thu`, `Conversion value`       | Không bắt buộc — cần cho tính ROAS |

> File mẫu `examples/sample-google-sheet.csv` sử dụng đúng 9 cột: `Date, Campaign, Impressions, Clicks,
> CTR, CPC, Spend, Conversions, CPA` — đây là bộ cột tối thiểu khuyến nghị cho demo.

### Các dạng bảng dữ liệu thường gặp

- **Dữ liệu theo ngày (daily breakdown):** mỗi dòng là một ngày của một chiến dịch — phù hợp phân tích xu hướng.
- **Dữ liệu tổng hợp theo chiến dịch (campaign summary):** mỗi dòng là tổng số liệu của một chiến dịch
  trong cả khoảng thời gian — phù hợp so sánh nhanh giữa các chiến dịch.
- **Dữ liệu đa kênh (multi-channel):** gộp dữ liệu từ nhiều nền tảng quảng cáo — cần chuẩn hóa tên cột
  giữa các nền tảng trước khi so sánh.

### Yêu cầu tối thiểu để Tool xử lý được

- Có tối thiểu các cột: Ngày, Tên chiến dịch, Spend, Impressions, Clicks.
- Dữ liệu có ít nhất 1 khoảng thời gian liên tục (ví dụ 7 ngày) để phân tích xu hướng.
- Định dạng số và ngày tháng nhất quán trong toàn bộ bảng.

---

## 3. Mô tả dữ liệu đầu ra (Output)

Sau khi xử lý, Tool tạo ra các loại kết quả sau, theo đúng thứ tự pipeline ở mục 4:

| Giai đoạn | Loại output | Vị trí trình bày |
|-----------|-------------|-------------------|
| Hiển thị dữ liệu | Bảng dữ liệu gốc đã đọc được (dạng markdown table) | Hiển thị trực tiếp trong hội thoại |
| Kiểm tra dữ liệu | Kết luận tình trạng dữ liệu (Đạt yêu cầu / Có vấn đề / Không đủ) | Hiển thị trực tiếp, theo mẫu ở `checklist/data-checklist.md` |
| Tóm tắt KPI | Bảng tổng hợp Spend, Impressions, Clicks, CTR, CPC, Conversions, CPA (và ROAS nếu có Revenue) | Hiển thị trực tiếp, theo `docs/metrics-guide.md` |
| Phân tích | Nhận xét xu hướng theo ngày, so sánh giữa các chiến dịch, điểm bất thường | Hiển thị trực tiếp trong hội thoại |
| Đề xuất tối ưu | Bảng đề xuất theo nhóm Budget/Targeting/Creative/Bidding | Theo khung `templates/optimization-template.md` |
| Báo cáo cuối cùng | File Markdown hoàn chỉnh gộp toàn bộ các phần trên | Theo khung `templates/report-template.md`, lưu tại `outputs/` |

Ví dụ output đầy đủ (từ đọc dữ liệu → hiển thị → tóm tắt → phân tích KPI) xem tại
`examples/sample-analysis-result.md`.

---

## 4. Luồng xử lý (Pipeline)

```
┌─────────────────────────┐
│ 1. Đọc dữ liệu (mô phỏng)│  ← Người dùng cung cấp CSV/XLSX/bảng dán
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 2. Hiển thị dữ liệu       │  ← Tool render lại thành bảng markdown, xác nhận đã đọc đúng
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 3. Kiểm tra dữ liệu       │  ← Áp dụng checklist/data-checklist.md
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 4. Tóm tắt KPI            │  ← Áp dụng docs/metrics-guide.md
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 5. Phân tích hiệu quả      │  ← So sánh, xu hướng, bất thường
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 6. Nhận xét & đề xuất tối ưu│ ← Áp dụng templates/optimization-template.md
└────────────┬─────────────┘
             ▼
┌─────────────────────────┐
│ 7. Sinh báo cáo Markdown   │  ← Áp dụng templates/report-template.md, lưu vào outputs/
└─────────────────────────┘
```

### Diễn giải từng bước

1. **Đọc dữ liệu (mô phỏng):** Nhận file CSV/XLSX hoặc bảng dán từ người dùng, ánh xạ tên cột về
   nhóm chuẩn ở mục 2.
2. **Hiển thị dữ liệu:** Trình bày lại toàn bộ hoặc một phần dữ liệu đã đọc dưới dạng bảng markdown,
   giúp người dùng xác nhận Tool đã hiểu đúng dữ liệu trước khi phân tích sâu hơn.
3. **Kiểm tra dữ liệu:** Rà soát theo `checklist/data-checklist.md` — thiếu cột, giá trị bất hợp lý,
   trùng lặp, sai định dạng.
4. **Tóm tắt KPI:** Tính các chỉ số tổng hợp theo công thức chuẩn tại `docs/metrics-guide.md`.
5. **Phân tích hiệu quả:** So sánh giữa các chiến dịch, phát hiện xu hướng theo thời gian và các
   điểm bất thường.
6. **Nhận xét & đề xuất tối ưu:** Đưa ra nhận xét khách quan dựa trên số liệu, đề xuất tối ưu theo
   từng nhóm (Budget, Targeting, Creative, Bidding).
7. **Sinh báo cáo Markdown:** Tổng hợp toàn bộ kết quả các bước trên vào một báo cáo hoàn chỉnh theo
   `templates/report-template.md`, lưu vào thư mục `outputs/`.

## 5. Lưu ý khi sử dụng

- Luôn xác nhận lại khoảng thời gian dữ liệu (từ ngày → đến ngày) với người dùng.
- Nếu dữ liệu có nhiều tab/sheet (khi copy từ Google Sheet có nhiều trang tính), hỏi rõ người dùng
  muốn phân tích tab nào.
- Nếu số liệu có dấu hiệu bị cắt (ví dụ dòng cuối không đầy đủ), cần hỏi lại trước khi tổng hợp.
- Vì là Tool mô phỏng, mọi số liệu đều dựa hoàn toàn vào dữ liệu người dùng cung cấp — Tool không
  tự bổ sung hoặc suy đoán số liệu còn thiếu.
