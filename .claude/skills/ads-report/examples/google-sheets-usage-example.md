# Ví dụ: Sử dụng Skill ads-report với Google Sheets

> Đây là ví dụ minh hoạ (dữ liệu và link đều là giả lập) để hình dung cách Skill xử lý khi người dùng cung cấp Google Sheet thay vì dán số liệu trực tiếp.

## Link Google Sheet giả lập

```
https://docs.google.com/spreadsheets/d/1AbCDeFGhiJKLmnoPQRstuVWXyz1234567890/edit#gid=0
```

Sheet giả lập có 1 tab tên **"Thang6_2026"**, cấu trúc dạng bảng:

| Campaign | Impression | Click | CTR | CPC | Conversion | CPA |
|---|---|---|---|---|---|---|
| Serum_Search_Brand | 60.000 | 1.800 | 3,0% | 6.500đ | 70 | 167.000đ |
| Serum_Search_NonBrand | 90.000 | 1.900 | 2,1% | 7.800đ | 50 | 296.000đ |
| Serum_Display_Remarketing | 30.000 | 500 | 1,7% | 6.000đ | 15 | 200.000đ |

## Prompt người dùng

```
Đây là Google Sheet chứa dữ liệu chiến dịch Google Ads tháng 6/2026 của khách hàng Hồng Quân:
https://docs.google.com/spreadsheets/d/1AbCDeFGhiJKLmnoPQRstuVWXyz1234567890/edit#gid=0
(tab "Thang6_2026")

Hãy dùng Skill ads-report để đọc dữ liệu và lên báo cáo giúp mình.
```

## Các bước Claude thực hiện

1. **Xác nhận phạm vi dữ liệu**: nhận diện đây là Google Sheet, ghi nhận tab cần đọc là "Thang6_2026" (đã được người dùng chỉ rõ nên không cần hỏi lại).
2. **Kiểm tra quyền truy cập**: xác minh có thể mở và đọc được sheet ở link trên. Nếu không truy cập được, dừng lại và làm theo hướng xử lý trong `docs/google-sheets-integration.md` (xin quyền hoặc yêu cầu xuất CSV/XLSX) thay vì tự suy đoán số liệu.
3. **Đọc dữ liệu**: lấy toàn bộ bảng dữ liệu trong tab "Thang6_2026" (3 dòng chiến dịch, 7 cột chỉ số).
4. **Xác định cột KPI**: ánh xạ các cột đọc được vào chỉ số chuẩn của Skill — Campaign, Impression, Click, CTR, CPC, Conversion, CPA đều khớp trực tiếp với tên cột chuẩn nên không cần hỏi lại người dùng. Ghi nhận sheet không có cột CPM/ROAS — sẽ đánh dấu "không có dữ liệu" trong báo cáo thay vì tự tính hoặc bịa số liệu.
5. **Phân tích dữ liệu theo template của Skill**: đọc `templates/report-template.md` để lấy cấu trúc, tổng hợp số liệu 3 chiến dịch thành số liệu chung của cả tài khoản, đối chiếu `docs/metrics-guide.md` khi cần diễn giải đúng ý nghĩa từng chỉ số.
6. **Sinh báo cáo và recommendation**: điền đầy đủ báo cáo theo cấu trúc chuẩn, nêu insight (ví dụ: nhóm "Serum_Search_Brand" có CPA thấp nhất) và đề xuất tối ưu, sau đó rà soát theo `checklist/qa-checklist.md` trước khi xem là hoàn tất.

## Kết quả đầu ra mong muốn

Một báo cáo hoàn chỉnh theo đúng cấu trúc `templates/report-template.md`, trong đó:

- **Tổng quan**: tổng hợp từ 3 chiến dịch — tổng Impression 180.000, tổng Click 4.200, tổng Conversion 135 (khớp với dữ liệu trong sheet).
- **Phân tích chỉ số**: bảng chỉ số tổng hợp toàn tài khoản (CTR, CPC, Conversion, CPA), có ghi chú rõ "CPM: không có dữ liệu trong sheet" và "ROAS: không có dữ liệu trong sheet" thay vì bỏ trống không giải thích.
- **Insight**: nêu rõ chiến dịch nào (theo từng dòng trong sheet) đang hiệu quả nhất/kém nhất, ví dụ "Serum_Search_Brand" có CPA thấp nhất (167.000đ) nên ưu tiên phân bổ thêm ngân sách, còn "Serum_Display_Remarketing" có CTR thấp nhất (1,7%) cần xem lại creative.
- **Recommendation**: đề xuất cụ thể gắn với từng chiến dịch trong sheet (tăng ngân sách nhóm hiệu quả, tối ưu/tạm dừng nhóm kém hiệu quả).
- **Việc cần làm tiếp theo**: danh sách công việc cụ thể kèm người phụ trách và thời hạn.
- Nếu người dùng yêu cầu gửi khách, kèm theo phần **Nội dung gửi khách** soạn từ `templates/client-message-template.md`.

Nếu ở bước 2 Claude không có quyền truy cập sheet, kết quả đầu ra mong muốn thay vào đó là một phản hồi ngắn gọn thông báo không đọc được dữ liệu và đề nghị người dùng chia sẻ quyền truy cập hoặc gửi file CSV/XLSX, chứ không tự tạo báo cáo bằng số liệu suy đoán.
