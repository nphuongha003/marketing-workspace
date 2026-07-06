# Tích hợp Google Sheets cho Skill ads-report

## Mục đích tích hợp

- Cho phép Claude phân tích và lên báo cáo hiệu quả quảng cáo trực tiếp từ dữ liệu đang được lưu trên Google Sheets, thay vì người dùng phải copy/paste số liệu thủ công.
- Rút ngắn thời gian chuẩn bị báo cáo khi dữ liệu quảng cáo (export từ Ads Manager/Google Ads) đã được tổng hợp sẵn trong một Google Sheet dùng chung của team/khách hàng.
- Đảm bảo báo cáo sinh ra từ dữ liệu Google Sheets vẫn tuân theo đúng cấu trúc và tiêu chuẩn chất lượng như khi làm báo cáo thủ công (dùng chung `templates/report-template.md`, `docs/metrics-guide.md`, `checklist/qa-checklist.md`).

## Dữ liệu đầu vào mong muốn

- Người dùng cung cấp **URL Google Sheet** (dạng `https://docs.google.com/spreadsheets/d/...`) hoặc **Spreadsheet ID** (chuỗi ký tự trong URL).
- Nếu sheet có nhiều tab, người dùng nên chỉ rõ tên tab cần phân tích; nếu không chỉ rõ, Claude hỏi lại trước khi đọc dữ liệu.
- Dữ liệu nên ở dạng bảng, mỗi dòng là một chiến dịch/nhóm quảng cáo, mỗi cột là một chỉ số (Campaign, Impression, Click, CTR, CPC, CPM, Conversion, CPA, ROAS...).
- Nếu cần so sánh theo kỳ, dữ liệu nên có cột xác định giai đoạn/ngày để Claude phân biệt được kỳ này và kỳ trước.

## Cách Claude đọc dữ liệu

1. Xác minh có thể truy cập được Google Sheet từ URL/Spreadsheet ID được cung cấp.
2. Đọc dữ liệu thô của tab/khoảng dữ liệu liên quan (dòng tiêu đề cột + các dòng dữ liệu).
3. Không chỉnh sửa/ghi đè dữ liệu gốc trên Google Sheet — Skill chỉ đọc dữ liệu để phân tích, không tự động thay đổi nội dung sheet trừ khi người dùng yêu cầu rõ ràng.
4. Nếu dữ liệu quá lớn hoặc trải nhiều tab, ưu tiên xác nhận lại phạm vi cần phân tích với người dùng thay vì tự ý đọc toàn bộ file.

## Các cột KPI được hỗ trợ

Claude sẽ cố gắng nhận diện các cột sau (không phân biệt hoa/thường, chấp nhận một số cách viết phổ biến/viết tắt):

| Chỉ số chuẩn | Một số tên cột thường gặp |
|---|---|
| Campaign | Campaign, Chiến dịch, Tên chiến dịch |
| Impression | Impression, Impressions, Hiển thị |
| Click | Click, Clicks, Lượt click |
| CTR | CTR, Click-through rate |
| CPC | CPC, Cost per click |
| CPM | CPM, Cost per mille |
| Conversion | Conversion, Conversions, Chuyển đổi |
| CPA | CPA, Cost per acquisition, CPL, Cost per lead |
| ROAS | ROAS, Return on ad spend |

Nếu sheet có tên cột không khớp danh sách trên (viết tắt lạ, sai chính tả, ngôn ngữ khác...), Claude sẽ suy luận hợp lý dựa trên ngữ cảnh; nếu không chắc chắn, sẽ hỏi lại người dùng để xác nhận trước khi phân tích, tránh diễn giải sai lệch số liệu.

## Workflow xử lý

```
Người dùng cung cấp URL Google Sheet hoặc Spreadsheet ID
        ↓
Claude kiểm tra quyền truy cập
        ↓
Đọc dữ liệu từ Google Sheets
        ↓
Xác định các cột KPI (Campaign, Click, Impression, CTR, CPC, CPM, Conversion, CPA, ROAS...)
        ↓
Phân tích dữ liệu theo template của Skill
        ↓
Sinh báo cáo và recommendation
```

Sau khi đọc và xác định dữ liệu, Claude tiếp tục theo đúng "Quy trình gợi ý khi viết báo cáo từ đầu đến cuối" đã mô tả trong `SKILL.md`: điền `templates/report-template.md`, đối chiếu `examples/sample-report.md` khi cần, tra `docs/metrics-guide.md` để giải thích chỉ số đúng nghĩa, rà soát theo `checklist/qa-checklist.md`, và soạn `templates/client-message-template.md` nếu cần gửi khách.

## Các trường hợp lỗi và cách xử lý

| Trường hợp lỗi | Cách xử lý |
|---|---|
| Không có quyền truy cập Google Sheet (private, chưa được chia sẻ) | Thông báo cho người dùng và yêu cầu chia sẻ quyền truy cập (tối thiểu quyền xem), hoặc xuất dữ liệu ra CSV/XLSX để gửi trực tiếp. |
| URL/Spreadsheet ID không hợp lệ hoặc không tìm thấy file | Báo lại cho người dùng, xin cung cấp lại URL/ID chính xác. |
| Sheet tồn tại nhưng không có dữ liệu, hoặc tab được chỉ định trống | Thông báo cho người dùng, xác nhận lại đúng tab/phạm vi dữ liệu cần phân tích. |
| Không xác định được cột KPI nào khớp với dữ liệu cần phân tích | Liệt kê các cột đọc được và hỏi lại người dùng để ánh xạ đúng cột trước khi phân tích, không tự suy đoán khi có rủi ro sai lệch cao. |
| Dữ liệu thiếu một số chỉ số cần thiết cho báo cáo (ví dụ thiếu Conversion) | Ghi nhận rõ trong báo cáo là "không có dữ liệu"/"không áp dụng", không tự bịa số liệu để lấp đầy. |
| Lỗi kỹ thuật khi đọc dữ liệu (timeout, định dạng không đọc được...) | Báo lỗi cụ thể cho người dùng và đề xuất phương án thay thế (thử lại, hoặc xuất CSV/XLSX). |

**Nguyên tắc chung khi gặp lỗi:** luôn minh bạch báo lại cho người dùng biết chuyện gì đang xảy ra và chờ hướng xử lý, không tự suy đoán hoặc bịa số liệu thay cho dữ liệu không đọc được.
