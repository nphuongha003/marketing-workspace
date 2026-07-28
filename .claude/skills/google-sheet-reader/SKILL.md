---
name: google-sheet-reader
description: Tool MÔ PHỎNG (simulated) đọc và phân tích dữ liệu hiệu suất quảng cáo từ Google Sheets phục vụ Account Performance Marketing — dùng cho mục đích demo/bài cuối khóa, chưa kết nối Google Sheets API thật. Dùng khi người dùng cung cấp dữ liệu CSV/XLSX hoặc bảng copy từ Google Sheets và cần kiểm tra dữ liệu đầu vào, tóm tắt KPI, phân tích hiệu quả chiến dịch quảng cáo, đưa ra nhận xét, đề xuất hướng tối ưu, hoặc sinh báo cáo Markdown (ví dụ Facebook Ads, Google Ads, TikTok Ads). Kích hoạt khi có các từ khóa như "đọc Google Sheet", "phân tích hiệu suất quảng cáo", "báo cáo KPI", "tối ưu chiến dịch".
---

# Google Sheet Reader — Account Performance Marketing (Tool Mô Phỏng)

## Mục đích

Đây là một **Tool mô phỏng (simulated tool)**, được xây dựng để **demo cho bài cuối khóa**, minh họa
quy trình một Google Sheet Reader thật sẽ vận hành ra sao khi phục vụ đội ngũ **Account Performance
Marketing**. Tool giả lập bước "đọc dữ liệu từ Google Sheets" bằng cách nhận dữ liệu do người dùng
cung cấp trực tiếp (CSV, XLSX, hoặc bảng copy từ Google Sheets), sau đó thực hiện toàn bộ pipeline
xử lý như thể dữ liệu đó vừa được đọc trực tiếp từ một Google Sheet thật:

1. "Đọc" dữ liệu hiệu suất quảng cáo (từ file CSV/XLSX hoặc bảng người dùng dán vào).
2. Kiểm tra tính hợp lệ và đầy đủ của dữ liệu đầu vào.
3. Tóm tắt các chỉ số KPI chính (Spend, Impression, Click, CTR, CPC, CPM, Conversion, CPA, ROAS...).
4. Phân tích hiệu quả chiến dịch quảng cáo theo thời gian, theo kênh, theo nhóm quảng cáo.
5. Đưa ra nhận xét dựa trên dữ liệu (điểm mạnh, điểm yếu, bất thường).
6. Đề xuất hướng tối ưu ngân sách, targeting, creative, bidding.
7. Sinh báo cáo dạng Markdown theo template có sẵn.

> **Lưu ý quan trọng — đây là Tool MÔ PHỎNG:**
> - **KHÔNG** kết nối Google Sheets API thật.
> - **KHÔNG** dùng MCP (Model Context Protocol) hay bất kỳ kết nối tool ngoài nào.
> - Bước "đọc Google Sheet" được **mô phỏng** bằng cách người dùng cung cấp dữ liệu dưới dạng
>   file CSV/XLSX đã export, hoặc bảng dữ liệu đã copy trực tiếp từ Google Sheets.
> - Toàn bộ xử lý phía sau (kiểm tra dữ liệu, tính KPI, phân tích, sinh báo cáo) được Claude thực hiện
>   thủ công dựa trên dữ liệu văn bản/bảng đó, giống hệt như quy trình sẽ áp dụng khi có kết nối thật.
> - Xem chi tiết hướng dẫn sử dụng, mô tả input/output, và luồng xử lý tại `docs/google-sheet-guide.md`.

## Khi nào sử dụng skill này

Sử dụng skill khi người dùng:

- Cung cấp một liên kết Google Sheet, một bảng dữ liệu, hoặc file export (CSV/Excel) chứa dữ liệu quảng cáo.
- Yêu cầu kiểm tra chất lượng/tính đầy đủ của dữ liệu trước khi phân tích.
- Yêu cầu tóm tắt các chỉ số KPI cho một khoảng thời gian hoặc một chiến dịch.
- Yêu cầu phân tích hiệu quả, so sánh giữa các chiến dịch/nhóm quảng cáo/kênh.
- Yêu cầu nhận xét, đánh giá hiệu suất hoặc phát hiện điểm bất thường.
- Yêu cầu đề xuất hướng tối ưu (ngân sách, targeting, creative...).
- Yêu cầu xuất báo cáo hoàn chỉnh dạng Markdown.

## Quy trình thực hiện (Workflow)

### Bước 1 — "Đọc" dữ liệu đầu vào (mô phỏng đọc Google Sheet)
- Vì Tool chưa kết nối API thật, bước "đọc Google Sheet" được mô phỏng bằng cách người dùng cung cấp
  dữ liệu dưới một trong các hình thức: file CSV đính kèm (export từ Google Sheets), file XLSX đính kèm,
  hoặc bảng dữ liệu copy trực tiếp từ Google Sheets dán vào hội thoại.
- Nếu chưa có dữ liệu cụ thể, hỏi người dùng cung cấp:
  - Khoảng thời gian phân tích.
  - Các cột dữ liệu hiện có (tên chiến dịch, ngày, chi phí, hiển thị, click, chuyển đổi...).
  - Mục tiêu chiến dịch (nhận diện thương hiệu, chuyển đổi, doanh thu...).
- Tham khảo chi tiết cách sử dụng Tool, mô tả input/output, và luồng xử lý tại `docs/google-sheet-guide.md`.

### Bước 2 — Kiểm tra dữ liệu đầu vào
- Áp dụng checklist tại `checklist/data-checklist.md` để rà soát:
  - Thiếu cột dữ liệu bắt buộc.
  - Giá trị trống, âm, hoặc không hợp lệ.
  - Trùng lặp dòng dữ liệu.
  - Đơn vị tiền tệ/định dạng số không nhất quán.
  - Khoảng thời gian dữ liệu có bị gián đoạn không.
- Báo cáo lại cho người dùng các vấn đề phát hiện được trước khi phân tích tiếp.

### Bước 3 — Tóm tắt KPI chính
- Tính toán và trình bày các KPI chính, tham khảo định nghĩa công thức tại `docs/metrics-guide.md`:
  - Tổng chi phí (Spend)
  - Impression, Reach
  - Click, CTR (Click-Through Rate)
  - CPC (Cost per Click), CPM (Cost per Mille)
  - Conversion, CPA (Cost per Acquisition)
  - Doanh thu, ROAS (Return on Ad Spend)
- Trình bày dưới dạng bảng tổng hợp dễ đọc.

### Bước 4 — Phân tích hiệu quả chiến dịch
- So sánh hiệu suất giữa các chiến dịch, nhóm quảng cáo, hoặc kênh (nếu có nhiều nguồn).
- Phân tích xu hướng theo thời gian (tăng/giảm theo ngày, tuần, tháng).
- Xác định chiến dịch/nhóm quảng cáo hoạt động tốt nhất và kém nhất.
- Phát hiện các điểm bất thường (spike chi phí, CTR giảm đột ngột, CPA tăng vọt...).

### Bước 5 — Đưa ra nhận xét
- Nhận xét khách quan, dựa trên số liệu cụ thể (không suy diễn cảm tính).
- Nêu rõ nguyên nhân có thể (nếu suy luận được từ dữ liệu) và giới hạn của nhận xét (nếu thiếu dữ liệu bổ trợ).

### Bước 6 — Đề xuất hướng tối ưu
- Dựa trên khung đề xuất tại `templates/optimization-template.md`, đưa ra đề xuất theo từng nhóm:
  - Tối ưu ngân sách (Budget)
  - Tối ưu đối tượng mục tiêu (Targeting)
  - Tối ưu nội dung/creative (Creative)
  - Tối ưu chiến lược đấu giá (Bidding)
  - Tối ưu trang đích/phễu chuyển đổi (Landing Page/Funnel), nếu dữ liệu cho phép.

### Bước 7 — Sinh báo cáo Markdown
- Dùng `templates/report-template.md` làm khung chuẩn để tổng hợp toàn bộ kết quả từ Bước 3–6.
- Lưu báo cáo hoàn chỉnh vào thư mục `outputs/` với tên file rõ ràng, ví dụ:
  `outputs/bao-cao-hieu-suat-<ten-chien-dich>-<yyyy-mm-dd>.md`
- Tham khảo ví dụ hoàn chỉnh tại `examples/sample-analysis.md`.

## Cấu trúc thư mục skill

```
google-sheet-reader/
├── SKILL.md                          # File hướng dẫn chính (file này)
├── templates/
│   ├── report-template.md            # Khung báo cáo Markdown chuẩn
│   └── optimization-template.md      # Khung đề xuất tối ưu
├── checklist/
│   └── data-checklist.md             # Checklist kiểm tra dữ liệu đầu vào
├── docs/
│   ├── metrics-guide.md              # Hướng dẫn định nghĩa & công thức KPI
│   └── google-sheet-guide.md         # Hướng dẫn đọc cấu trúc Google Sheet
├── examples/
│   ├── sample-analysis.md            # Ví dụ phân tích mẫu hoàn chỉnh (dữ liệu mô tả trong văn bản)
│   ├── sample-google-sheet.csv        # Dữ liệu mẫu mô phỏng một Google Sheet export ra CSV
│   └── sample-analysis-result.md      # Kết quả đầy đủ khi Tool "đọc" file CSV mẫu ở trên
└── outputs/                          # Nơi lưu các báo cáo được sinh ra
```

## Giới hạn hiện tại (Tool mô phỏng — dùng cho demo/bài cuối khóa)

- **Chưa kết nối Google Sheets API thật** — người dùng cần tự cung cấp dữ liệu (dán bảng, upload
  file CSV/XLSX export từ Google Sheets, hoặc mô tả bằng lời).
- **Chưa dùng MCP** hay bất kỳ cơ chế kết nối tool ngoài nào — mọi xử lý diễn ra thủ công trong hội thoại.
- Không tự động lấy dữ liệu real-time từ Google Sheets.
- Không thực hiện thay đổi trực tiếp trên tài khoản quảng cáo (chỉ phân tích và đề xuất).
- Đây là bước mô phỏng quy trình; khi có nhu cầu dùng dữ liệu thật theo thời gian thực, cần xây dựng
  thêm lớp kết nối thật (Google Sheets API hoặc MCP) ở giai đoạn sau.
