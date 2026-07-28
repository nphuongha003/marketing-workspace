# Hướng dẫn định nghĩa & công thức KPI (Performance Marketing)

Tài liệu này định nghĩa các chỉ số KPI thường dùng khi phân tích hiệu suất quảng cáo, kèm công thức
tính toán để đảm bảo tính nhất quán khi tóm tắt và phân tích dữ liệu.

## 1. Nhóm chỉ số về chi phí & quy mô

| Chỉ số | Tên đầy đủ | Công thức | Ý nghĩa |
|--------|-----------|-----------|---------|
| Spend | Tổng chi phí | Tổng cộng dồn cột chi phí | Tổng ngân sách đã chi trong kỳ |
| Impressions | Lượt hiển thị | Tổng cộng dồn cột hiển thị | Số lần quảng cáo được hiển thị |
| Reach | Lượt tiếp cận | Tổng/duy nhất theo dữ liệu gốc | Số người dùng duy nhất tiếp cận được |
| Frequency | Tần suất hiển thị | `Impressions / Reach` | Trung bình mỗi người thấy quảng cáo bao nhiêu lần |

## 2. Nhóm chỉ số về tương tác

| Chỉ số | Tên đầy đủ | Công thức | Ý nghĩa |
|--------|-----------|-----------|---------|
| Clicks | Lượt nhấp | Tổng cộng dồn cột click | Số lượt người dùng nhấp vào quảng cáo |
| CTR | Click-Through Rate | `Clicks / Impressions * 100%` | Tỷ lệ nhấp trên hiển thị, đo mức độ hấp dẫn của creative |
| CPC | Cost per Click | `Spend / Clicks` | Chi phí trung bình cho mỗi lượt nhấp |
| CPM | Cost per Mille | `Spend / Impressions * 1000` | Chi phí cho mỗi 1.000 lượt hiển thị |

## 3. Nhóm chỉ số về chuyển đổi & hiệu quả kinh doanh

| Chỉ số | Tên đầy đủ | Công thức | Ý nghĩa |
|--------|-----------|-----------|---------|
| Conversions | Chuyển đổi | Tổng cộng dồn cột chuyển đổi | Số hành động mục tiêu (mua hàng, đăng ký, lead...) |
| CVR | Conversion Rate | `Conversions / Clicks * 100%` | Tỷ lệ chuyển đổi trên lượt nhấp |
| CPA | Cost per Acquisition | `Spend / Conversions` | Chi phí trung bình cho mỗi chuyển đổi |
| Revenue | Doanh thu | Tổng cộng dồn cột doanh thu/giá trị chuyển đổi | Doanh thu ghi nhận được từ quảng cáo |
| ROAS | Return on Ad Spend | `Revenue / Spend` | Tỷ suất doanh thu trên chi phí quảng cáo (thường biểu thị theo lần, ví dụ 3.5x) |
| AOV | Average Order Value | `Revenue / Conversions` | Giá trị đơn hàng trung bình |

## 4. Ngưỡng tham khảo khi nhận xét (mang tính tương đối)

> Các ngưỡng dưới đây chỉ mang tính tham khảo chung, cần điều chỉnh theo ngành hàng, kênh quảng cáo
> và mục tiêu chiến dịch cụ thể của khách hàng. Luôn ưu tiên so sánh với dữ liệu lịch sử của chính
> tài khoản/chiến dịch đó thay vì áp đặt ngưỡng cố định.

- **CTR thấp bất thường:** giảm liên tục qua nhiều kỳ so với trung bình lịch sử → dấu hiệu creative
  bị "mỏi" (ad fatigue) hoặc nhắm sai đối tượng.
- **CPA/CPC tăng đột biến:** tăng mạnh so với kỳ trước trong khi CTR không đổi → có thể do cạnh tranh
  đấu giá tăng hoặc chất lượng landing page giảm.
- **Frequency quá cao:** thường trên 4–6 lần trong một khoảng thời gian ngắn có thể là dấu hiệu ad fatigue,
  cần thay đổi creative hoặc mở rộng đối tượng.
- **ROAS dưới mục tiêu (target ROAS) của khách hàng:** cần rà soát lại phân bổ ngân sách giữa các
  chiến dịch/nhóm quảng cáo.

## 5. Nguyên tắc khi tính toán

1. Luôn tính KPI tổng hợp dựa trên tổng số (sum) của tử số và mẫu số, **không** tính trung bình cộng
   của các tỷ lệ theo từng ngày (tránh sai lệch do trọng số).
   - Ví dụ CTR trung bình kỳ = `Tổng Clicks / Tổng Impressions`, không phải trung bình cộng CTR từng ngày.
2. Làm tròn số hợp lý khi trình bày (ví dụ CTR làm tròn 2 chữ số thập phân, ROAS làm tròn 2 chữ số).
3. Nêu rõ đơn vị tiền tệ khi trình bày Spend, CPC, CPM, CPA, Revenue.
4. Nếu thiếu dữ liệu để tính một chỉ số (ví dụ thiếu Revenue), ghi chú rõ "Không đủ dữ liệu" thay vì bỏ qua.
