# Checklist kiểm tra dữ liệu đầu vào

Sử dụng checklist này ở **Bước 2** của quy trình (xem `SKILL.md`) trước khi tiến hành tóm tắt KPI
và phân tích. Mục tiêu là đảm bảo dữ liệu đủ tin cậy trước khi đưa ra nhận xét/đề xuất.

## 1. Kiểm tra cấu trúc dữ liệu

- [ ] Đã xác định được toàn bộ tên cột trong dữ liệu gốc.
- [ ] Đã ánh xạ (mapping) các cột về nhóm chuẩn theo `docs/google-sheet-guide.md`.
- [ ] Đã xác nhận khoảng thời gian dữ liệu (ngày bắt đầu — ngày kết thúc) với người dùng.
- [ ] Đã xác nhận cấp độ dữ liệu (theo ngày / theo chiến dịch / theo nhóm quảng cáo / đa kênh).

## 2. Kiểm tra tính đầy đủ

- [ ] Không có cột KPI bắt buộc nào bị thiếu hoàn toàn (Spend, Impressions, Clicks tối thiểu).
- [ ] Nếu thiếu cột Doanh thu/Chuyển đổi, đã ghi chú rõ các KPI liên quan (ROAS, CPA, CVR) sẽ không
      tính được hoặc cần loại trừ khỏi báo cáo.
- [ ] Không có khoảng trống ngày bất thường (ví dụ mất dữ liệu giữa chừng) mà không có lý do rõ ràng.
- [ ] Số dòng dữ liệu khớp với kỳ vọng (số ngày x số chiến dịch, nếu là dữ liệu daily breakdown).

## 3. Kiểm tra tính hợp lệ của giá trị

- [ ] Không có giá trị âm ở các cột số lượng (Spend, Impressions, Clicks, Conversions, Revenue).
- [ ] Không có giá trị Clicks/Conversions lớn hơn Impressions/Clicks tương ứng (vô lý về logic).
- [ ] Không có giá trị trống (null/blank) ở các cột KPI chính mà không có giải thích.
- [ ] Định dạng số nhất quán (không lẫn dấu phẩy/dấu chấm thập phân giữa các dòng).
- [ ] Định dạng ngày tháng nhất quán trên toàn bộ bảng dữ liệu.

## 4. Kiểm tra trùng lặp & nhất quán

- [ ] Không có dòng dữ liệu trùng lặp hoàn toàn (cùng ngày, cùng chiến dịch, cùng số liệu).
- [ ] Tên chiến dịch/nhóm quảng cáo được viết nhất quán (không bị lỗi chính tả tạo thành 2 chiến dịch khác nhau).
- [ ] Đơn vị tiền tệ nhất quán trên toàn bộ dữ liệu (không lẫn VND và USD nếu không quy đổi).
- [ ] Nếu dữ liệu đa kênh, tên các nhóm chỉ số đã được chuẩn hóa giữa các nền tảng.

## 5. Kết luận sau kiểm tra

Sau khi rà soát, tổng hợp kết quả theo mẫu sau trước khi báo cáo lại cho người dùng:

```
Tình trạng dữ liệu: [Đạt yêu cầu / Có vấn đề cần lưu ý / Không đủ để phân tích]

Vấn đề phát hiện (nếu có):
- ...
- ...

Ảnh hưởng đến phân tích:
- ...

Đề xuất xử lý trước khi tiếp tục:
- ...
```

> **Nguyên tắc:** Nếu phát hiện vấn đề nghiêm trọng (ví dụ thiếu quá nhiều dữ liệu, sai lệch logic
> rõ ràng), cần dừng lại và trao đổi với người dùng trước khi tiếp tục sang bước tóm tắt KPI, thay vì
> tự ý bỏ qua hoặc suy diễn số liệu còn thiếu.
