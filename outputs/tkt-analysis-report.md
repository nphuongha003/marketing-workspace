# Báo Cáo Hiệu Suất Chiến Dịch Quảng Cáo

- **Tài khoản/Khách hàng:** ⚠️ Cần xác nhận lại — xem cảnh báo ở mục 1.2
- **Chiến dịch/Phạm vi phân tích:** 96 chiến dịch Facebook Ads, mục tiêu **Reach** (100%), toàn bộ mang tên "Aeon Mall Tân Phú | Reach | ..."
- **Kênh quảng cáo:** Facebook Ads
- **Khoảng thời gian:** 11/03/2026 – 27/07/2026 (theo phạm vi báo cáo trong file); ngày tạo chiến dịch trải từ 11/03/2026 đến 23/07/2026 (17 đợt tạo chiến dịch khác nhau)
- **Ngày lập báo cáo:** 2026-07-28
- **Người thực hiện:** Tool `google-sheet-reader`, đọc trực tiếp file CSV thật

---

## 1. Tổng quan dữ liệu đầu vào

- **Nguồn dữ liệu:** File CSV thật, export từ Facebook Ads Manager —
  `data/Nhà-Hát-Tuổi-Trẻ-(TKT)-Chiến-dịch-11-Tháng-3-2026-27-Tháng-7-2026.csv` (27 cột, 97 dòng dữ liệu:
  96 dòng chiến dịch + 1 dòng tổng toàn tài khoản).
- **Tình trạng dữ liệu sau kiểm tra:** ⚠️ **Có vấn đề nghiêm trọng cần xác nhận với người dùng trước khi
  dùng cho báo cáo gửi khách** (chi tiết mục 1.2) — dữ liệu kỹ thuật bên trong file nhất quán và đủ tin
  cậy để phân tích, nhưng **không khớp với tên khách hàng trong tên file**.
- **Ghi chú về dữ liệu:** Đây là chiến dịch mục tiêu Reach (nhận diện/tiếp cận), không phải mục tiêu
  Chuyển đổi — không có sẵn cột CTR/CPC/Conversions/CPA/Revenue/ROAS như file mẫu thông thường. Đã điều
  chỉnh bộ KPI ở mục 2 cho phù hợp với bản chất dữ liệu thật, thay vì áp khung KPI chuẩn không phù hợp.

### 1.1. Dữ liệu gốc đã đọc (xem trước — file đầy đủ có 96 dòng chiến dịch)

**Cấu trúc cột (27 cột):** Lượt bắt đầu/kết thúc báo cáo, Tên chiến dịch, Lượt phân phối chiến dịch,
Kết quả, Chỉ báo kết quả, Chi phí trên mỗi kết quả, Ngân sách nhóm quảng cáo, Loại ngân sách, Số tiền đã
chi tiêu (VND), Kết thúc, Cài đặt ghi nhận, Lượt mua, Giá trị chuyển đổi từ lượt mua, ROAS của lượt mua,
Người liên hệ nhắn tin mới (+chi phí), Lượt bắt đầu cuộc trò chuyện (+chi phí), Đơn đặt hàng đã tạo/đã
vận chuyển, Ngày tạo, Người tiếp cận, Lượt hiển thị, Lượt tương tác với bài viết, Tần suất, Lượt click
vào liên kết.

**Dòng tổng toàn tài khoản (dòng 2 trong file, không có tên chiến dịch):**

| Số tiền đã chi tiêu (VND) | Người tiếp cận | Lượt hiển thị | Tần suất |
|---:|---:|---:|---:|
| 38.690.616 | 2.545.726 | 6.926.488 | 2,72083 |

**5 dòng chiến dịch đầu tiên (trong tổng số 96 dòng):**

| Tên chiến dịch | Trạng thái | Kết quả (Reach) | Chi phí/1.000 kết quả | Spend (VND) | Impressions | Tần suất |
|---|---|---:|---:|---:|---:|---:|
| Aeon Mall Tân Phú \| Reach \| CẢM ƠN NGƯỜI ĐÃ ĐỒNG HÀNH \| 50.000 \| 16/3-22/3 | inactive | 50.305 | 5.807 | 292.126 | 59.867 | 1,19 |
| Aeon Mall Tân Phú \| Reach \| KỶ NIỆM 1 NĂM AEON MALL TÂN PHÚ CELADON \| 150.000 \| 16/3-22/3 | inactive | 150.469 | 6.908 | 1.039.440 | 195.488 | 1,30 |
| Aeon Mall Tân Phú \| Reach \| ƯU ĐÃI 50% VÉ KHI ĐẶT VÉ ONLINE \| 100.000 \| 23/3-1/4 | inactive | 97.172 | 8.079 | 785.066 | 128.378 | 1,32 |
| Aeon Mall Tân Phú \| Reach \| CƠ HỘI GIA NHẬP "ĐẠI GIA ĐÌNH" \| 150.000 \| 23/3-31/3 | inactive | 152.568 | 7.515 | 1.146.564 | 189.435 | 1,24 |
| Aeon Mall Tân Phú \| Reach \| PHIM SUPER MARIO THIÊN HÀ \| 50.000 \| 3/4-8/4 | inactive | 53.370 | 4.784 | 255.336 | 57.491 | 1,08 |

*(91 dòng còn lại có cấu trúc tương tự, đã được dùng đầy đủ trong các bước tính toán bên dưới — không
liệt kê hết để tránh báo cáo quá dài; toàn bộ số liệu tổng hợp ở mục 2–3 được tính trên đúng 96 dòng.)*

### 1.2. Kết quả kiểm tra dữ liệu (theo `checklist/data-checklist.md`)

```
Tình trạng dữ liệu: CÓ VẤN ĐỀ NGHIÊM TRỌNG CẦN XÁC NHẬN TRƯỚC KHI DÙNG BÁO CÁO NÀY CHO KHÁCH HÀNG

Vấn đề phát hiện:
1. [NGHIÊM TRỌNG] Tên file là "Nhà Hát Tuổi Trẻ (TKT)" nhưng 96/96 dòng dữ liệu (100%) đều là chiến
   dịch mang tên "Aeon Mall Tân Phú" — không có bất kỳ dòng nào nhắc đến "Nhà Hát Tuổi Trẻ" hay "TKT".
   Đây có thể là file bị đặt sai tên, bị nhầm giữa 2 tài khoản khách hàng, hoặc export nhầm dữ liệu.
2. Cột "Ngân sách nhóm quảng cáo" (budget kế hoạch) trống/= 0 ở toàn bộ 96 dòng — không có cơ sở để so
   sánh Spend thực tế với ngân sách kế hoạch.
3. Cột "Lượt mua", "Giá trị chuyển đổi từ lượt mua", "ROAS", "Đơn đặt hàng đã tạo/đã vận chuyển" trống
   hoàn toàn ở cả 96 dòng — tài khoản không track được bất kỳ giao dịch/doanh thu nào trong 4,5 tháng.
4. Chỉ 27/96 chiến dịch (28%) có dữ liệu tương tác Messenger; 69% còn lại không track kênh này.
5. Cộng dồn "Người tiếp cận" (Reach) của 96 chiến dịch cho ra 5.542.690 — CAO HƠN GẤP ĐÔI Reach thực tế
   toàn tài khoản (2.545.726, lấy từ dòng tổng) do trùng lặp người dùng giữa các chiến dịch chạy chồng
   lấn thời gian. Không được cộng dồn Reach cấp chiến dịch để suy ra Reach toàn tài khoản.
6. Không có cột CTR/CPC/CPA có sẵn (khác cấu trúc file mẫu) vì đây là chiến dịch Reach, không phải
   Conversion — đã tự tính lại các chỉ số tương đương phù hợp (xem mục 2).
7. Đây là báo cáo gộp một giai đoạn dài (4,5 tháng), không chia theo kỳ/tuần có sẵn — không có "kỳ
   trước" để so sánh thay đổi.

Không phát hiện: giá trị âm, dòng trùng lặp, hay sai định dạng ngày/số trong 96 dòng chiến dịch — cấu
trúc 27 cột nhất quán trên toàn bộ file.

Ảnh hưởng đến phân tích:
- Vấn đề (1) không ảnh hưởng đến độ chính xác của các con số kỹ thuật bên dưới (dữ liệu vẫn nhất quán
  nội bộ), nhưng ảnh hưởng trực tiếp đến việc DÙNG BÁO CÁO NÀY CHO ĐÚNG KHÁCH HÀNG — cần xác nhận trước
  khi gửi cho "Nhà Hát Tuổi Trẻ" hoặc dùng để ra quyết định ngân sách.
- Vấn đề (2)(3) khiến không thể đánh giá ROI/ROAS của toàn bộ 38.690.616đ đã chi.

Đề xuất xử lý trước khi tiếp tục:
- Xác nhận lại với người dùng: file này thực sự là dữ liệu của khách hàng nào ("Aeon Mall Tân Phú" hay
  "Nhà Hát Tuổi Trẻ")? Nếu là nhầm lẫn, cần lấy đúng file của "Nhà Hát Tuổi Trẻ (TKT)" để phân tích lại.
- Trong khi chờ xác nhận, báo cáo này vẫn được hoàn thiện đầy đủ (theo đúng yêu cầu) dựa trên dữ liệu
  thật có trong file, để phục vụ mục đích kiểm thử Tool — nhưng KHÔNG nên gửi trực tiếp cho khách hàng
  cho đến khi xác nhận xong danh tính tài khoản.
```

---

## 2. Tóm tắt KPI chính

*Bộ KPI dưới đây được điều chỉnh phù hợp với chiến dịch mục tiêu Reach (không có Clicks/CTR/CPC/CPA/
Revenue/ROAS chuẩn như chiến dịch Conversion).*

| Chỉ số | Giá trị |
|---|---:|
| Tổng ngân sách đã chi (Spend) | 38.690.616 VND |
| Số chiến dịch | 96 (60 inactive · 30 completed · 5 active · 1 recently_completed) |
| Reach — người tiếp cận duy nhất, toàn tài khoản | 2.545.726 |
| Impressions (tổng, cộng dồn được) | 6.926.488 |
| Tần suất (Impressions / Reach) | 2,72 |
| CPM — chi phí trên mỗi 1.000 impression | 5.586 VND |
| Chi phí trên mỗi 1.000 người tiếp cận (Reach) | 15.198 VND |
| Tổng lượt tương tác bài viết (Post Engagement) | 69.446 |
| Tỷ lệ tương tác toàn tài khoản (Engagement/Impressions) | 1,00% (trung vị từng chiến dịch chỉ 0,16%) |
| Tổng lượt click vào liên kết | 3.555 |
| Link CTR (Click/Impressions) | 0,051% |
| Người liên hệ nhắn tin mới | 59 (chỉ 27/96 chiến dịch có track kênh này) |
| Lượt bắt đầu cuộc trò chuyện qua tin nhắn | 65 |
| Lượt mua / Giá trị chuyển đổi / ROAS | **Không có dữ liệu** — 0/96 chiến dịch track được giao dịch mua hàng |

*(CPM và Engagement Rate tính trên Impressions vì đây là chỉ số cộng dồn chính xác được; "Chi phí/1.000
Reach" tính trên Reach DUY NHẤT của toàn tài khoản (2.545.726), không phải tổng cộng dồn Reach từng
chiến dịch — theo đúng lưu ý ở mục 1.2.)*

---

## 3. Phân tích hiệu quả chiến dịch

### 3.1. Theo thời gian (nhóm theo tháng tạo chiến dịch)

| Tháng | Số chiến dịch | Spend (VND) | Impressions | CPM (VND) | Engagement | Tỷ lệ tương tác |
|---|---:|---:|---:|---:|---:|---:|
| 03/2026 | 14 | 12.432.404 | 2.042.155 | 6.088 | 4.169 | 0,20% |
| 04/2026 | 13 | 5.922.140 | 1.134.040 | 5.222 | 6.340 | 0,56% |
| 05/2026 | 35 | 10.296.201 | 1.954.771 | 5.267 | 38.936 | **1,99%** |
| 06/2026 | 18 | 5.287.446 | 933.094 | 5.667 | 15.575 | 1,67% |
| 07/2026 | 16 | 4.752.425 | 862.428 | 5.511 | 4.426 | 0,51% |

- Tháng 3 vừa chi nhiều nhất (12,43 triệu, chiếm 32% tổng ngân sách) vừa có CPM cao nhất (6.088đ/1.000
  impression) và tỷ lệ tương tác thấp nhất (0,20%) — giai đoạn khởi động kém hiệu quả nhất về chi phí
  tiếp cận.
- Tháng 5 có số chiến dịch nhiều nhất (35/96, do chạy nhiều mini-campaign ngắn ngày) và tỷ lệ tương tác
  vượt trội (1,99%, gấp ~4 lần tháng 4 và ~10 lần tháng 3) dù CPM ở mức trung bình — đây là tháng có
  content hiệu quả nhất trong toàn giai đoạn.
- Tháng 6 duy trì được đà tương tác tốt (1,67%) dù ngân sách giảm mạnh so với tháng 5.

### 3.2. Chiến dịch chi tiêu nhiều nhất / ít nhất

**Top 5 chiến dịch có Spend cao nhất:**

| Spend (VND) | Chiến dịch |
|---:|---|
| 1.925.003 | TOUCH SPRING 2026 \| 150.000 \| 11/3-22/3 |
| 1.559.508 | VIỆC LÀM TRAO TAY - CÓ NGAY THU NHẬP HẤP DẪN \| 200.000 \| 12/3-31/3 |
| 1.244.581 | SHOPPING LIỀN TAY - KHÔNG LO VỀ GIÁ \| 150.000 \| 16/3-30/3 |
| 1.190.933 | Khởi động đường đua "F5" \| 150.000 \| 15/3-30/3 |
| 1.170.400 | MỪNG ĐẠI LỄ - SALE SẬP SÀN \| 150.000 \| 14/4-3/5 |

4 trong 5 chiến dịch tốn ngân sách nhất đều được tạo trong tháng 3 — trùng khớp với việc tháng 3 có
CPM cao nhất và tỷ lệ tương tác thấp nhất ở mục 3.1.

**5 chiến dịch có Spend thấp nhất:** dao động 27.023đ – 41.418đ, đều là các mini-campaign ngắn ngày
(thường 3-7 ngày) chạy trong tháng 5-6.

### 3.3. Điểm bất thường / nổi bật phát hiện được

- **Outlier tích cực rõ rệt:** Chiến dịch *"ĐẶC QUYỀN RIÊNG CHO 'NGƯỜI NHÀ' | 50.000 | 14/4-20/4"* (tạo
  ngày 07/05/2026) đạt tỷ lệ tương tác **36,91%** (20.490 lượt tương tác / 55.511 impressions) — gấp
  ~230 lần trung vị toàn tài khoản (0,159%), trong khi Spend chỉ ở mức trung bình (256.399đ). Đây là
  outlier lớn nhất trong toàn bộ 96 chiến dịch.
- Các chiến dịch tương tác cao khác (đều ≥3%, so với trung vị 0,159%): *"CÒN GÌ TUYỆT HƠN ĐƯỢC ĐI CHƠI
  NHÀ TUYẾT..."* (13,27%), *"Cả nhà có ai đã trượt thử zipline..."* (12,42%), *"Có một tiện ích bạn sẽ
  cực thích..."* (10,78%), *"ARTIST DAY ĐÃ QUAY TRỞ LẠI!"* (10,59%). Tổng cộng chỉ 9/96 chiến dịch
  (9,4%) đạt tỷ lệ tương tác ≥3%, còn lại 86/96 (90%) dưới 1%.
- Điểm chung của các chiến dịch tương tác cao: nội dung dạng "đặc quyền/ưu đãi dành riêng cho thành
  viên" hoặc trải nghiệm tại chỗ (zipline, tiện ích mới) — khác hẳn phong cách thông báo sự kiện/sale
  thông thường chiếm đa số các chiến dịch còn lại.
- Link CTR toàn tài khoản rất thấp (0,051%) — phù hợp với đặc thù chiến dịch mục tiêu Reach (thuật toán
  ưu tiên phân phối rộng, không tối ưu cho click), không nên so sánh trực tiếp với benchmark của chiến
  dịch Traffic/Conversion.

---

## 4. Nhận xét

- **Điểm tích cực:**
  - Một nhóm nhỏ chiến dịch (đặc biệt tháng 5) chứng minh được nội dung dạng "ưu đãi/đặc quyền thành
    viên" có thể đạt tỷ lệ tương tác vượt trội gấp hàng chục đến hàng trăm lần mức trung bình, với chi
    phí không hề cao hơn các chiến dịch khác.
  - CPM toàn tài khoản (5.586đ) ổn định ở mức hợp lý từ tháng 4 trở đi, sau khi cải thiện so với tháng 3.

- **Điểm cần lưu ý/hạn chế:**
  - Toàn bộ 96 chiến dịch (100%) chỉ chạy theo mục tiêu Reach — không có bất kỳ chiến dịch nào track
    được Lượt mua/Doanh thu trong suốt 4,5 tháng, nên **không có cách nào chứng minh hiệu quả kinh
    doanh (ROAS)** của 38.690.616đ đã chi.
  - 90% chiến dịch (86/96) có tỷ lệ tương tác dưới 1% — phần lớn ngân sách đang dùng để "hiển thị" hơn
    là tạo tương tác thực sự với người xem.
  - Tháng 3 vừa chi nhiều ngân sách nhất vừa kém hiệu quả nhất (CPM cao, tương tác thấp) — giai đoạn
    đầu triển khai có dấu hiệu chưa tối ưu.

- **Nguyên nhân có thể (dựa trên dữ liệu):**
  - CTR/tương tác thấp ở đa số chiến dịch phù hợp với đặc thù mục tiêu Reach (không tối ưu cho click),
    nên đây nhiều khả năng là lựa chọn objective có chủ đích chứ không hẳn là "hiệu quả kém" theo nghĩa
    Conversion — cần xác nhận lại mục tiêu kinh doanh thực sự của tài khoản này với người phụ trách.

⚠️ **Trước khi trình bày các nhận xét trên cho bất kỳ khách hàng nào, bắt buộc phải xác nhận lại danh
tính tài khoản theo cảnh báo ở mục 1.2** — toàn bộ phân tích này áp dụng cho dữ liệu "Aeon Mall Tân
Phú", chưa chắc là dữ liệu của "Nhà Hát Tuổi Trẻ (TKT)" như tên file thể hiện.

---

## 5. Đề xuất hướng tối ưu

> Chi tiết đầy đủ theo khung `templates/optimization-template.md`

### 5.1. Tối ưu ngân sách (Budget)

- **Quan sát:** Tháng 3 chiếm 32% tổng ngân sách nhưng có CPM cao nhất và tương tác thấp nhất; ngược
  lại tháng 5 dùng ngân sách vừa phải nhưng đạt tương tác cao nhất.
- **Đề xuất:** Giảm tỷ trọng ngân sách dồn vào giai đoạn khởi động (kiểu tháng 3), phân bổ đều hơn hoặc
  ưu tiên các giai đoạn/loại nội dung đã chứng minh hiệu quả tương tác tốt (kiểu tháng 5).
- **Ưu tiên:** Trung bình
- **Kỳ vọng:** Giảm CPM trung bình toàn tài khoản, tăng tỷ lệ tương tác chung.

### 5.2. Tối ưu đối tượng mục tiêu (Targeting)

- **Quan sát:** Dữ liệu hiện tại không có breakdown theo đối tượng/độ tuổi nên chưa thể xác định chính
  xác nhóm đối tượng nào phản hồi tốt với các chiến dịch outlier ở mục 3.3.
- **Đề xuất:** Bổ sung báo cáo phân theo đối tượng (demographics/placement) ở kỳ tới để xác định chính
  xác ai đang phản hồi tốt với nội dung "đặc quyền thành viên", từ đó nhân rộng đúng đối tượng.
- **Ưu tiên:** Thấp — *giả thuyết cần kiểm chứng thêm, hiện chưa đủ dữ liệu.*
- **Kỳ vọng:** Xác định được chân dung đối tượng hiệu quả nhất để tối ưu targeting.

### 5.3. Tối ưu nội dung quảng cáo (Creative)

- **Quan sát:** Chiến dịch "ĐẶC QUYỀN RIÊNG CHO 'NGƯỜI NHÀ'" đạt tỷ lệ tương tác 36,91%, gấp ~230 lần
  trung vị toàn tài khoản (0,159%), với chi phí không cao hơn các chiến dịch khác.
- **Đề xuất:** Nhân rộng phong cách nội dung "ưu đãi/đặc quyền dành riêng cho thành viên" và trải
  nghiệm tại chỗ (đã chứng minh hiệu quả ở mục 3.3), giảm dần các mẫu thông báo sự kiện/sale thông
  thường đang chiếm đa số nhưng có tương tác thấp.
- **Ưu tiên:** Cao
- **Kỳ vọng:** Nâng tỷ lệ tương tác trung bình toàn tài khoản lên gần mức của nhóm chiến dịch tốt nhất.

### 5.4. Tối ưu chiến lược đấu giá / mục tiêu chiến dịch (Bidding & Objective)

- **Quan sát:** 100% chiến dịch (96/96) đang chạy mục tiêu Reach, không có chiến dịch Conversion nào để
  đối chiếu hiệu quả kinh doanh trong suốt 4,5 tháng.
- **Đề xuất:** Nếu mục tiêu kinh doanh thực sự cần đo lường doanh số/lead, cân nhắc thử nghiệm một phần
  ngân sách (ví dụ 10-20%) sang mục tiêu Traffic hoặc Conversion để có cơ sở đối chiếu ROAS.
- **Ưu tiên:** Trung bình — *cần xác nhận mục tiêu kinh doanh thực sự của tài khoản trước khi đổi.*
- **Kỳ vọng:** Có dữ liệu ROAS làm căn cứ phân bổ ngân sách ở các kỳ báo cáo tiếp theo.

### 5.5. Tối ưu trang đích/phễu chuyển đổi (Landing Page/Funnel)

- **Quan sát:** Không có dữ liệu Lượt mua/Đơn hàng nào được track trong toàn bộ dataset.
- **Đề xuất:** Bổ sung Facebook Pixel/Conversion API và cột "Lượt mua"/"Giá trị chuyển đổi" cho các
  chiến dịch có landing page ở kỳ báo cáo tiếp theo, nếu tài khoản có mục tiêu bán hàng/đăng ký.
- **Ưu tiên:** Thấp (với mục tiêu Reach hiện tại) / Cao (nếu tài khoản thực sự cần đo ROAS)
- **Kỳ vọng:** Có đủ dữ liệu để đánh giá hiệu quả kinh doanh ở lần phân tích sau.

### 5.6. Bảng tổng hợp ưu tiên hành động

| Thứ tự | Hành động | Nhóm | Ưu tiên |
|---|---|---|---|
| 1 | **Xác nhận lại danh tính khách hàng thật của file dữ liệu này** trước khi dùng cho bất kỳ mục đích nào khác | Chất lượng dữ liệu | **Cao nhất** |
| 2 | Nhân rộng phong cách content "ưu đãi/đặc quyền thành viên" đã chứng minh hiệu quả | Creative | Cao |
| 3 | Rà soát lại cách phân bổ ngân sách giai đoạn khởi động (tháng 3) | Budget | Trung bình |
| 4 | Xác nhận mục tiêu kinh doanh thực sự, cân nhắc thử nghiệm mục tiêu Conversion | Bidding/Objective | Trung bình |
| 5 | Bổ sung tracking Lượt mua/Doanh thu (Pixel) nếu cần đo ROAS | Landing Page/Funnel | Thấp–Cao (tuỳ mục tiêu) |

---

## 6. Kết luận

Trong giai đoạn 11/03 – 27/07/2026, tài khoản đã chi 38.690.616đ cho 96 chiến dịch Facebook Ads mục
tiêu Reach, tiếp cận 2.545.726 người với 6.926.488 lượt hiển thị (CPM 5.586đ). Một nhóm nhỏ chiến dịch
theo phong cách "ưu đãi/đặc quyền thành viên" nổi bật với tỷ lệ tương tác vượt trội (tới 36,91%, so với
trung vị 0,159%), trong khi phần lớn ngân sách (90% số chiến dịch) chỉ đạt tương tác dưới 1% và không
có bất kỳ dữ liệu doanh thu/ROAS nào trong suốt 4,5 tháng.

**Quan trọng nhất:** trước khi sử dụng báo cáo này cho bất kỳ quyết định hay giao tiếp khách hàng nào,
cần xác nhận lại vì sao file được đặt tên theo khách hàng "Nhà Hát Tuổi Trẻ (TKT)" nhưng toàn bộ 96
chiến dịch bên trong đều thuộc về "Aeon Mall Tân Phú" — đây có thể là nhầm lẫn file giữa hai khách hàng.

---

*Báo cáo được tạo bởi Tool `google-sheet-reader`, đọc trực tiếp dữ liệu thật từ file CSV export Facebook
Ads Manager (`data/Nhà-Hát-Tuổi-Trẻ-(TKT)-Chiến-dịch-11-Tháng-3-2026-27-Tháng-7-2026.csv`), không dùng
bất kỳ số liệu giả lập nào. Toàn bộ số liệu được tính bằng script phân tích CSV (Python), đối chiếu chéo
với dòng tổng của file để đảm bảo độ chính xác.*
