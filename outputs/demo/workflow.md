# Workflow — Chiến dịch SCG HOME

Tổng hợp quy trình điều phối của Team Leader cho nhiệm vụ: lập kế hoạch, proposal và email gửi khách hàng SCG HOME.

## Danh sách Agent đã sử dụng

| Agent | Vai trò trong nhiệm vụ này |
|---|---|
| Performance Marketing Agent | Phân tích yêu cầu, lập kế hoạch chiến dịch (mục tiêu, đối tượng, insight, kênh, timeline, ngân sách, KPI, recommendation) |
| Client Support Agent | Chuyển kế hoạch thành Proposal hoàn chỉnh và soạn Email gửi khách |

Cả 2 Sub Agent trong workspace đều đã được sử dụng, đúng phân vai đã thiết kế (không có Agent nào bị bỏ qua hoặc dùng sai vai trò).

## Danh sách Skill đã sử dụng

| Skill | Thuộc Agent | Mục đích sử dụng |
|---|---|---|
| `campaign-planner` | Performance Marketing Agent | Xây dựng kế hoạch chiến dịch đầy đủ 8 mục |
| `proposal-generator` | Client Support Agent | Soạn Proposal + Báo giá gửi khách |
| `client-reply` | Client Support Agent | Soạn Email gửi kèm Proposal (template `proposal-email.md`) |

**Skill không sử dụng:** `ads-report` — không dùng vì SCG HOME là khách hàng mới, chưa có dữ liệu quảng cáo thực tế để phân tích. Skill này sẽ được dùng ở giai đoạn tiếp theo (sau khi có số liệu thực tế từ Tháng 1 hoặc cuối 3 tháng) để đánh giá KPI thực tế so với kế hoạch.

## Thứ tự thực hiện

```
Bước 1: Performance Marketing Agent → campaign-planner
        ↓ (bàn giao: kế hoạch chiến dịch đầy đủ)
Bước 2: Client Support Agent → proposal-generator
        ↓ (bàn giao: proposal + báo giá)
Bước 3: Client Support Agent → client-reply
        (kết quả: email gửi kèm proposal)
```

### Bước 1 — Performance Marketing Agent / `campaign-planner`

- **Lý do lựa chọn:** Đây là chiến dịch hoàn toàn mới, cần xây dựng kế hoạch từ đầu (mục tiêu, đối tượng, insight, kênh, timeline, ngân sách, KPI, recommendation) — đúng phạm vi trách nhiệm "Xây dựng kế hoạch triển khai" của Performance Marketing Agent. Dùng `campaign-planner` vì chưa có số liệu thực tế để phân tích bằng `ads-report`.
- **Kết quả đầu ra:** Kế hoạch chiến dịch đầy đủ 8 mục (Mục tiêu, Đối tượng, Insight, Kênh triển khai, Timeline 12 tuần/3 tháng, Phân bổ ngân sách 3 chiều — theo tháng/theo hình thức/tổng hợp, KPI đề xuất theo từng mục tiêu, Recommendation), ngân sách khớp đúng 150.000.000đ. Kèm quyết định rõ ràng: không dùng `ads-report` ở giai đoạn này. → Lưu tại `campaign-plan.md`.

### Bước 2 — Client Support Agent / `proposal-generator`

- **Lý do lựa chọn:** Sau khi có kế hoạch từ Performance Marketing Agent, nhiệm vụ tiếp theo là "Chuyển kết quả phân tích thành Proposal" — đúng phạm vi trách nhiệm của Client Support Agent. Dùng `proposal-generator` vì đây là nhiệm vụ tạo proposal/báo giá hoàn chỉnh gửi khách hàng, không phải tình huống giao tiếp thường gặp.
- **Lý do chuyển giao từ Bước 1:** Performance Marketing Agent không tự soạn nội dung gửi khách hàng ở dạng hoàn chỉnh (ngoài phạm vi trách nhiệm) — toàn bộ số liệu, căn cứ và giới hạn dữ liệu (KPI là ước tính, chưa có lịch sử tài khoản) được bàn giao nguyên vẹn để Client Support Agent không tự suy đoán hay chỉnh sửa số liệu.
- **Kết quả đầu ra:** Proposal Digital Marketing đầy đủ 10 mục (thông tin khách hàng, phân tích hiện trạng, mục tiêu, đối tượng có lồng insight, chiến lược triển khai, kế hoạch quảng cáo theo giai đoạn, KPI có ghi chú rõ là ước tính, timeline, ngân sách, deliverables) kèm Báo giá dịch vụ đính kèm, CTA cuối rõ ràng. Số liệu khớp 100% với `campaign-plan.md`. → Lưu tại `proposal.md`.

### Bước 3 — Client Support Agent / `client-reply`

- **Lý do lựa chọn:** Sau khi có Proposal, cần soạn email gửi kèm — đúng template `proposal-email.md` của Skill `client-reply`, đảm bảo văn phong chuyên nghiệp theo `docs/tone-of-voice.md` của Skill.
- **Lý do chuyển giao từ Bước 2:** Cùng một Agent (Client Support Agent) thực hiện tuần tự 2 Skill vì cả soạn proposal và soạn email đều thuộc phạm vi giao tiếp khách hàng — không cần chuyển ngược lại Performance Marketing Agent vì không phát sinh nhu cầu phân tích/kế hoạch bổ sung.
- **Kết quả đầu ra:** Email gửi Proposal, giọng văn lịch sự — chuyên nghiệp — chủ động, dùng từ ngữ thận trọng khi nói về KPI ("hướng tới", "ước tính"), có CTA rõ ràng (đề xuất lịch trao đổi trong tuần). → Lưu tại `email-to-client.md`.

## Ghi chú kiểm soát chất lượng của Team Leader

Khi tổng hợp kết quả từ Client Support Agent, Team Leader phát hiện agent đã tự điền một địa chỉ email cá nhân (không liên quan đến SCG HOME, không được cung cấp trong đề bài) vào phần chữ ký email — đây là thông tin không nên xuất hiện trong tài liệu demo. Team Leader đã thay bằng placeholder `[Thông tin liên hệ — cần điền số điện thoại/email cụ thể trước khi gửi]` trước khi lưu file cuối cùng.

---

## Tự kiểm tra cuối cùng

| Tiêu chí | Kết quả |
|---|---|
| Đã sử dụng đúng cả 2 Sub Agent | ✅ Performance Marketing Agent (Bước 1) và Client Support Agent (Bước 2-3) |
| Đã sử dụng đúng các Skill tương ứng | ✅ `campaign-planner` (đúng agent, đúng giai đoạn); `proposal-generator` và `client-reply` (đúng agent, đúng thứ tự); `ads-report` được cân nhắc và quyết định không dùng có lý do rõ ràng |
| Workflow hợp lý | ✅ Đúng trình tự Lập kế hoạch → Proposal → Email; mỗi bước ghi rõ Agent/Skill/Lý do trước khi thực hiện; bàn giao giữa 2 Agent không chồng chéo vai trò |
| Các file output đã tạo đầy đủ | ✅ `campaign-plan.md`, `proposal.md`, `email-to-client.md`, `workflow.md` — cả 4 file đã lưu tại `outputs/demo/` |
| Số liệu nhất quán giữa các file | ✅ Ngân sách 150.000.000đ, KPI, timeline khớp nhau giữa `campaign-plan.md` và `proposal.md` |
| Không có dữ liệu bịa/không có căn cứ | ✅ KPI luôn ghi rõ là ước tính benchmark, không phải cam kết; các thông tin chưa có (website/fanpage, người liên hệ, phí quản lý dịch vụ, thông tin liên hệ agency) được để placeholder rõ ràng thay vì tự bịa |

**Kết luận:** Workflow hoàn tất đúng yêu cầu — không có bước nào bị bỏ qua, không có Agent nào làm việc ngoài phạm vi, không có Skill nào bị dùng sai mục đích.
