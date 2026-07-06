---
name: ads-report
description: Hỗ trợ tạo và kiểm tra báo cáo hiệu quả quảng cáo Facebook Ads / Google Ads (phân tích chỉ số, insight, recommendation) và soạn tin nhắn gửi khách sau báo cáo. Dùng khi người dùng yêu cầu viết/đánh giá báo cáo ads, phân tích CTR/CPC/CPM/CPA/ROAS, hoặc soạn message gửi client kèm báo cáo.
---

# Ads Report

## Mục đích

Skill này giúp Claude hỗ trợ đội ngũ Digital Marketing:

- Xây dựng báo cáo đánh giá hiệu quả quảng cáo (Facebook Ads / Google Ads) theo cấu trúc chuẩn.
- Đảm bảo báo cáo đủ nội dung quan trọng (chỉ số, insight, recommendation, việc cần làm tiếp theo) trước khi gửi khách.
- Soạn tin nhắn thông báo/gửi kèm báo cáo cho khách hàng với giọng văn chuyên nghiệp.

## Khi nào nên dùng Skill này

- Khi người dùng yêu cầu viết báo cáo quảng cáo (weekly/monthly report, performance review...).
- Khi người dùng cần rà soát lại một báo cáo đã viết (QA trước khi gửi khách).
- Khi người dùng cần soạn tin nhắn/email ngắn gửi khách kèm báo cáo.
- Khi người dùng hỏi về ý nghĩa các chỉ số quảng cáo (CTR, CPC, CPM, CPA, ROAS...).
- Khi người dùng cung cấp URL/Spreadsheet ID của một Google Sheet chứa dữ liệu quảng cáo và muốn Claude phân tích, lên báo cáo trực tiếp từ đó (xem mục "Kết nối nền tảng ngoài").

## Cách sử dụng các tài nguyên trong Skill

Không cần đọc hết mọi file — chỉ đọc file phù hợp với tác vụ đang làm:

- **Viết báo cáo mới**: đọc `templates/report-template.md` để lấy cấu trúc, tham khảo `examples/sample-report.md` để hình dung một báo cáo hoàn chỉnh trông như thế nào.
- **Soạn tin nhắn gửi khách sau báo cáo**: đọc `templates/client-message-template.md`.
- **Kiểm tra chất lượng báo cáo trước khi gửi**: đọc `checklist/qa-checklist.md` và rà soát báo cáo theo từng mục.
- **Cần giải thích hoặc tra cứu ý nghĩa chỉ số**: đọc `docs/metrics-guide.md`.

Luôn ưu tiên đọc file tương ứng trước khi tạo nội dung, thay vì tự suy đoán cấu trúc hoặc định nghĩa chỉ số.

## Quy trình gợi ý khi viết báo cáo từ đầu đến cuối

1. Thu thập số liệu quảng cáo từ người dùng (hoặc hỏi lại nếu thiếu số liệu cần thiết).
2. Đọc `templates/report-template.md` và điền số liệu, nhận xét theo đúng cấu trúc.
3. Nếu chưa chắc cách nhận xét hoặc trình bày, đối chiếu với `examples/sample-report.md`.
4. Khi cần giải thích ý nghĩa một chỉ số cho đúng, tra `docs/metrics-guide.md` thay vì tự suy đoán.
5. Trước khi xem là hoàn tất, rà lại báo cáo theo `checklist/qa-checklist.md`; bổ sung phần còn thiếu.
6. Nếu người dùng cần gửi báo cáo cho khách, dùng `templates/client-message-template.md` để soạn tin nhắn/email kèm theo.

## Kết nối nền tảng ngoài (Google Sheets)

Khi người dùng cung cấp URL Google Sheet hoặc Spreadsheet ID thay vì dán số liệu trực tiếp, thực hiện theo workflow sau (chi tiết đầy đủ về dữ liệu đầu vào, cột KPI hỗ trợ và cách xử lý lỗi xem tại `docs/google-sheets-integration.md`):

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

Diễn giải từng bước:

1. **Nhận URL/Spreadsheet ID**: xác nhận lại với người dùng phạm vi dữ liệu cần phân tích (toàn bộ sheet hay một tab/khoảng thời gian cụ thể) nếu chưa rõ.
2. **Kiểm tra quyền truy cập**: xác minh có thể mở/đọc được Google Sheet trước khi tiến hành các bước tiếp theo (xem "Điều kiện sử dụng" bên dưới).
3. **Đọc dữ liệu**: lấy dữ liệu thô từ sheet (tên chiến dịch, các chỉ số theo từng dòng/cột).
4. **Xác định cột KPI**: khớp tên cột trong sheet với các chỉ số chuẩn của Skill (Campaign, Impression, Click, CTR, CPC, CPM, Conversion, CPA, ROAS...); nếu tên cột không khớp chuẩn (viết tắt, sai chính tả, ngôn ngữ khác...), suy luận hợp lý và xác nhận lại với người dùng nếu không chắc chắn.
5. **Phân tích dữ liệu theo template của Skill**: dùng đúng cấu trúc và cách nhận xét như khi làm báo cáo thủ công — đọc `templates/report-template.md` và `docs/metrics-guide.md` như bình thường, không tạo quy trình phân tích riêng cho dữ liệu từ Google Sheets.
6. **Sinh báo cáo và recommendation**: hoàn thiện báo cáo theo đúng quy trình đã mô tả ở mục "Quy trình gợi ý khi viết báo cáo từ đầu đến cuối" (điền template, đối chiếu ví dụ, rà soát checklist, soạn tin nhắn gửi khách nếu cần).

Xem ví dụ minh hoạ đầy đủ tại `examples/google-sheets-usage-example.md`.

### Điều kiện sử dụng

- Google Sheet cần được chia sẻ với quyền truy cập phù hợp (tối thiểu quyền xem) thì Claude mới đọc được dữ liệu.
- Nếu không đọc được dữ liệu (thiếu quyền truy cập, sheet ở chế độ riêng tư, lỗi định dạng...), yêu cầu người dùng thực hiện một trong hai cách:
  - Cấp quyền truy cập phù hợp cho Google Sheet, hoặc
  - Xuất dữ liệu ra file CSV/XLSX và gửi trực tiếp để phân tích.
- Không tự suy đoán hoặc bịa số liệu khi không truy cập được dữ liệu — luôn báo lại cho người dùng và chờ hướng xử lý.

## Lưu ý về văn phong

- Nhận xét chỉ số cần gắn với **số liệu cụ thể** (tăng/giảm bao nhiêu %, so với kỳ nào), tránh nhận xét chung chung như "chỉ số ổn định".
- Ưu tiên diễn đạt ngắn gọn, rõ ràng, đúng thuật ngữ ngành ads; giữ giọng văn chuyên nghiệp khi trình bày cho khách hàng.
- Nếu kết quả kỳ này kém hơn kỳ trước, vẫn nêu thẳng số liệu và tập trung vào nguyên nhân + hướng khắc phục thay vì né tránh.
