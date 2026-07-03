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

## Lưu ý về văn phong

- Nhận xét chỉ số cần gắn với **số liệu cụ thể** (tăng/giảm bao nhiêu %, so với kỳ nào), tránh nhận xét chung chung như "chỉ số ổn định".
- Ưu tiên diễn đạt ngắn gọn, rõ ràng, đúng thuật ngữ ngành ads; giữ giọng văn chuyên nghiệp khi trình bày cho khách hàng.
- Nếu kết quả kỳ này kém hơn kỳ trước, vẫn nêu thẳng số liệu và tập trung vào nguyên nhân + hướng khắc phục thay vì né tránh.
