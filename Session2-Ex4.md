# Session2-Bài 4: Chẩn đoán và "Phẫu thuật" Prompt Sơ sài thành Chuẩn CREATE

# PHẦN 1: PHÂN TÍCH CHẨN ĐOÁN LỖI

## 1.1. Bộ phận CSKH

**Câu lệnh sơ sài:** *"Viết tin nhắn xin lỗi khách vì hàng giao chậm."*

| Thành phần | Trạng thái | Chẩn đoán chi tiết |
|---|---|---|
| **C – Character** | ❌ Thiếu | Không nói AI là ai. AI không biết mình đang đại diện TechShop, nên viết kiểu chung chung, không có "giọng thương hiệu". |
| **R – Request** | ⚠️ Có nhưng sơ sài | Chỉ nói "xin lỗi", không yêu cầu nêu lý do, phương án đền bù, thời gian giao dự kiến mới. |
| **E – Examples** | ⚠️ Thiếu | Không có mẫu tin nhắn tốt để AI học cách viết. |
| **A – Adjustment** | ❌ Thiếu | Không quy định giọng điệu (chân thành, không sáo rỗng), độ dài, xưng hô, điều cấm (đổ lỗi cho shipper, hứa suông). |
| **T – Type of Output** | ❌ Thiếu | Không rõ là SMS, Zalo hay email; không rõ độ dài, cấu trúc. |
| **E – Extras** | ⚠️ Thiếu | Không có số đơn, lý do chậm, mã voucher, hotline, thời gian giao mới. |

**Hậu quả:** Tin nhắn ngắn, sáo rỗng, không có đền bù, không có thời gian giao dự kiến → khách vẫn bực, phải gọi hotline hỏi lại.

**Kết luận:** Thiếu rõ nhất **Character, Adjustment, Type** (đúng như bảng đề bài), ngoài ra còn yếu ở Extras và Examples.

---

## 1.2. Bộ phận Bán hàng

**Câu lệnh sơ sài:** *"Tư vấn cho anh khách mua laptop gaming."*

| Thành phần | Trạng thái | Chẩn đoán chi tiết |
|---|---|---|
| **C – Character** | ⚠️ Thiếu | Không giao vai "chuyên viên tư vấn" nên AI trả lời như tra cứu danh mục sản phẩm. |
| **R – Request** | ⚠️ Quá chung | "Tư vấn" mà không nói tư vấn theo tiêu chí nào (tầm giá, game chơi, nhu cầu), nên AI liệt kê tràn lan. |
| **E – Examples** | ❌ Thiếu | Không có mẫu cách trình bày một đề xuất tư vấn (điểm nhấn cấu hình, lý do chọn). |
| **A – Adjustment** | ⚠️ Thiếu | Không giới hạn số lượng đề xuất (AI liệt kê 10 dòng máy), không yêu cầu tập trung vào 2–3 lựa chọn. |
| **T – Type of Output** | ⚠️ Thiếu | Không chỉ định dạng (bảng so sánh, lời thoại tư vấn). |
| **E – Extras** | ❌ Thiếu | Không có tầm giá, game khách chơi, linh kiện ưu tiên, chính sách khuyến mãi/trả góp của TechShop. |

**Hậu quả:** Danh sách 10 dòng máy từ rẻ đến đắt, không rõ tầm giá, không có điểm nhấn cấu hình → nhân viên không dùng được để chốt đơn.

**Kết luận:** Thiếu rõ nhất **Extras, Request chi tiết, Examples**.

---

## 1.3. Bộ phận Kỹ thuật bảo hành

**Câu lệnh sơ sài:** *"Báo giá thay màn hình laptop vỡ cho khách."*

| Thành phần | Trạng thái | Chẩn đoán chi tiết |
|---|---|---|
| **C – Character** | ❌ Thiếu | AI không đóng vai kỹ thuật viên/nhân viên bảo hành của TechShop nên trả lời chung chung. |
| **R – Request** | ⚠️ Thiếu | Không nói rõ cần báo giá theo dòng máy nào, kích thước, loại tấm nền, thời gian sửa. |
| **E – Examples** | ⚠️ Thiếu | Không có mẫu bảng báo giá chuẩn. |
| **A – Adjustment** | ❌ Thiếu | Không ép AI báo giá cụ thể theo khoảng, không cấm câu trả lời né tránh "tùy model". |
| **T – Type of Output** | ❌ Thiếu | Không yêu cầu dạng **bảng báo giá**; AI trả lời văn xuôi chung chung. |
| **E – Extras** | ⚠️ Thiếu | Không có bảng giá linh kiện, quy định bảo hành (vỡ do va đập là lỗi người dùng, không thuộc bảo hành), thời gian sửa. |

**Hậu quả:** AI chỉ trả lời "tùy model giá khác nhau", không có bảng giá mẫu hay quy định bảo hành.

**Kết luận:** Thiếu rõ nhất **Character, Type of Output, Adjustment**.

---

## 1.4. Bảng tổng hợp chẩn đoán

| Bộ phận | C | R | E (Examples) | A | T | E (Extras) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| CSKH | ❌ | ⚠️ | ⚠️ | ❌ | ❌ | ⚠️ |
| Bán hàng | ⚠️ | ⚠️ | ❌ | ⚠️ | ⚠️ | ❌ |
| Bảo hành | ❌ | ⚠️ | ⚠️ | ❌ | ❌ | ⚠️ |

> Chú thích: ❌ = thiếu hoàn toàn / lỗi nặng nhất; ⚠️ = có nhưng mơ hồ hoặc thiếu.

---

# PHẦN 2: NÂNG CẤP CHUẨN HÓA CÂU LỆNH ("PHẪU THUẬT")

> Lưu ý: Các số liệu (giá, mã voucher, hotline, chính sách…) dưới đây là **dữ liệu giả định** để minh họa bối cảnh TechShop. Khi dùng thật, nhân viên thay bằng số liệu thực tế của công ty.

---

## 2.1. Master Prompt 1 – CSKH: Tin nhắn xin lỗi giao hàng chậm

### Các khối CREATE

**C – Character**
Bạn là chuyên viên Chăm sóc khách hàng cấp cao của chuỗi bán lẻ công nghệ TechShop, có 5 năm kinh nghiệm xử lý khiếu nại. Bạn giao tiếp lịch sự, đồng cảm, chuyên nghiệp và luôn đặt lợi ích của khách lên trước.

**R – Request**
Viết một tin nhắn xin lỗi gửi khách hàng có đơn hàng bị giao chậm. Tin nhắn phải: (1) mở đầu bằng lời xin lỗi chân thành, gọi đúng tên khách; (2) nêu ngắn gọn, trung thực lý do chậm; (3) thông báo thời gian giao dự kiến mới cụ thể; (4) đưa ra phương án đền bù; (5) cung cấp kênh liên hệ nếu khách cần hỗ trợ.

**E – Examples**
Mẫu tham khảo về giọng văn và cấu trúc:
> "Chào anh Minh, TechShop xin lỗi anh vì đơn hàng #TS1024 chưa đến tay anh đúng hẹn. Do lượng đơn tăng đột biến dịp khuyến mãi, kho xuất hàng chậm 2 ngày. Đơn của anh dự kiến giao trước 17h ngày 15/11. Để bù đắp, TechShop xin gửi anh mã giảm 10% cho lần mua tiếp theo…"

**A – Adjustment**
- Giọng điệu: chân thành, ấm áp, không máy móc; **tránh** các câu sáo rỗng như "Chúng tôi vô cùng tiếc nuối về sự bất tiện này".
- Xưng "TechShop/em" – gọi khách "anh/chị".
- Không đổ lỗi cho đơn vị vận chuyển; không hứa những điều ngoài chính sách.
- Độ dài tối đa 120 từ.

**T – Type of Output**
Một tin nhắn Zalo/SMS hoàn chỉnh, chia 3–4 đoạn ngắn, kết thúc bằng lời cảm ơn. Không dùng tiêu đề hay bảng.

**E – Extras**
- Tên khách: *[Tên khách]*; mã đơn: *[Mã đơn]*.
- Lý do chậm: *[ví dụ: kho quá tải do chương trình khuyến mãi]*.
- Thời gian giao mới: *[ví dụ: trước 17h ngày 15/11]*.
- Chính sách đền bù: voucher giảm 10% (tối đa 300.000đ) cho đơn kế tiếp, hoặc miễn phí vận chuyển đơn này nếu chậm trên 3 ngày.
- Hotline: *1900 xxxx* (8h–21h hằng ngày).

### ✅ MASTER PROMPT 1 (hoàn chỉnh)

```text
Bạn là chuyên viên Chăm sóc khách hàng cấp cao của chuỗi bán lẻ công nghệ TechShop, có 5 năm kinh nghiệm xử lý khiếu nại. Bạn giao tiếp lịch sự, đồng cảm, chuyên nghiệp và luôn đặt lợi ích của khách lên trước.

Nhiệm vụ: Viết một tin nhắn xin lỗi gửi khách hàng có đơn hàng bị giao chậm. Tin nhắn phải: (1) mở đầu bằng lời xin lỗi chân thành, gọi đúng tên khách; (2) nêu ngắn gọn, trung thực lý do chậm; (3) thông báo thời gian giao dự kiến mới cụ thể; (4) đưa ra phương án đền bù; (5) cung cấp kênh liên hệ nếu khách cần hỗ trợ.

Thông tin đơn hàng:
- Tên khách: [Tên khách] | Mã đơn: [Mã đơn]
- Lý do chậm: [Lý do, ví dụ: kho quá tải do chương trình khuyến mãi]
- Thời gian giao mới: [Ngày/giờ dự kiến]
- Đền bù: voucher giảm 10% (tối đa 300.000đ) cho đơn kế tiếp; nếu chậm trên 3 ngày thì miễn phí vận chuyển đơn này.
- Hotline: 1900 xxxx (8h–21h hằng ngày).

Mẫu tham khảo về giọng văn và cấu trúc:
"Chào anh Minh, TechShop xin lỗi anh vì đơn hàng #TS1024 chưa đến tay anh đúng hẹn. Do lượng đơn tăng đột biến dịp khuyến mãi, kho xuất hàng chậm 2 ngày. Đơn của anh dự kiến giao trước 17h ngày 15/11. Để bù đắp, TechShop xin gửi anh mã giảm 10% cho lần mua tiếp theo…"

Yêu cầu điều chỉnh:
- Giọng điệu chân thành, ấm áp; tránh câu sáo rỗng kiểu "vô cùng tiếc nuối về sự bất tiện này".
- Xưng "TechShop/em", gọi khách "anh/chị".
- Không đổ lỗi cho đơn vị vận chuyển, không hứa ngoài chính sách.
- Tối đa 120 từ.

Định dạng đầu ra: một tin nhắn Zalo/SMS hoàn chỉnh, 3–4 đoạn ngắn, kết thúc bằng lời cảm ơn; không dùng tiêu đề hay bảng.
```

---

## 2.2. Master Prompt 2 – Bán hàng: Tư vấn laptop gaming

### Các khối CREATE

**C – Character**
Bạn là chuyên viên tư vấn bán hàng laptop gaming của TechShop, hiểu rõ cấu hình phần cứng, hiệu năng chơi game và biết đặt câu hỏi để chốt đúng nhu cầu khách.

**R – Request**
Tư vấn cho một khách nam mua laptop gaming: chọn **đúng 3 mẫu** phù hợp tầm giá, mỗi mẫu nêu điểm nhấn cấu hình (CPU, GPU, RAM, màn hình tần số quét), lý do hợp với nhu cầu chơi game của khách, ưu/nhược điểm, rồi chỉ ra mẫu nên chọn nhất và cách chốt.

**E – Examples**
Mẫu một đề xuất:
> "**Mẫu A – ABC Gaming 15 (24.990.000đ)**: Core i5-13500H, RTX 4050 6GB, RAM 16GB, màn 144Hz. Chơi mượt Valorant, LoL, GTA V ở cấu hình cao. Phù hợp ngân sách vừa phải. Nhược điểm: pin chỉ khoảng 4 giờ."

**A – Adjustment**
- Không liệt kê quá 3 mẫu; tuyệt đối không liệt kê tràn lan từ rẻ đến đắt.
- Chỉ đề xuất máy nằm trong tầm giá khách đưa ra (cho phép lệch tối đa ±10%).
- Ngôn ngữ dễ hiểu, hạn chế thuật ngữ; nếu dùng thì giải thích ngắn.
- Không nói quá, không so sánh tiêu cực với đối thủ.

**T – Type of Output**
Gồm: (1) 1 bảng so sánh 3 mẫu theo các tiêu chí giá, CPU, GPU, RAM, màn hình, pin; (2) phần nhận xét ngắn cho từng mẫu; (3) 1 câu khuyên chọn mẫu tốt nhất; (4) 1 câu hỏi gợi mở để chốt đơn.

**E – Extras**
- Tầm giá: *[ví dụ 20–30 triệu]*; game khách chơi: *[ví dụ Valorant, GTA V, Cyberpunk]*; ưu tiên: *[hiệu năng / độ bền / pin]*.
- Ưu đãi TechShop: trả góp 0% 6 tháng, tặng chuột + balo gaming, bảo hành chính hãng 24 tháng, 1 đổi 1 trong 30 ngày.

### ✅ MASTER PROMPT 2 (hoàn chỉnh)

```text
Bạn là chuyên viên tư vấn bán hàng laptop gaming của chuỗi bán lẻ công nghệ TechShop, hiểu rõ cấu hình phần cứng, hiệu năng chơi game và biết đặt câu hỏi để chốt đúng nhu cầu khách.

Nhiệm vụ: Tư vấn cho một khách nam muốn mua laptop gaming. Hãy chọn ĐÚNG 3 mẫu phù hợp tầm giá của khách. Với mỗi mẫu, nêu điểm nhấn cấu hình (CPU, GPU, RAM, màn hình tần số quét), lý do phù hợp với nhu cầu chơi game của khách, ưu điểm và nhược điểm. Sau đó chỉ ra mẫu nên chọn nhất và gợi ý cách chốt.

Thông tin khách hàng:
- Tầm giá: [ví dụ 20–30 triệu đồng]
- Game thường chơi: [ví dụ Valorant, GTA V, Cyberpunk 2077]
- Ưu tiên: [hiệu năng / độ bền / pin / thiết kế]

Ưu đãi hiện có tại TechShop: trả góp 0% trong 6 tháng, tặng chuột + balo gaming, bảo hành chính hãng 24 tháng, 1 đổi 1 trong 30 ngày.

Mẫu tham khảo cho một đề xuất:
"Mẫu A – ABC Gaming 15 (24.990.000đ): Core i5-13500H, RTX 4050 6GB, RAM 16GB, màn 144Hz. Chơi mượt Valorant, LoL, GTA V ở cấu hình cao. Phù hợp ngân sách vừa phải. Nhược điểm: pin chỉ khoảng 4 giờ."

Yêu cầu điều chỉnh:
- Tuyệt đối không liệt kê quá 3 mẫu, không liệt kê tràn lan từ rẻ đến đắt.
- Chỉ đề xuất máy nằm trong tầm giá khách đưa ra (lệch tối đa ±10%).
- Ngôn ngữ dễ hiểu, thuật ngữ nào dùng thì giải thích ngắn.
- Không nói quá sự thật, không chê bai đối thủ.

Định dạng đầu ra: (1) bảng so sánh 3 mẫu gồm Giá, CPU, GPU, RAM, Màn hình, Pin; (2) nhận xét ngắn cho từng mẫu; (3) một câu khuyên chọn mẫu tốt nhất; (4) một câu hỏi gợi mở để chốt đơn.
```

---

## 2.3. Master Prompt 3 – Kỹ thuật bảo hành: Báo giá thay màn hình laptop vỡ

### Các khối CREATE

**C – Character**
Bạn là kỹ thuật viên trưởng kiêm nhân viên tiếp nhận bảo hành của TechShop, nắm rõ bảng giá linh kiện và quy định bảo hành của công ty, báo giá minh bạch, chính xác.

**R – Request**
Lập báo giá thay màn hình laptop bị vỡ cho khách: xác định loại sự cố và có thuộc diện bảo hành hay không; báo giá theo từng hạng mục (linh kiện + công thay + phí kiểm tra); nêu thời gian sửa dự kiến, thời hạn bảo hành sau sửa và lưu ý cho khách.

**E – Examples**
Mẫu một dòng báo giá:
> "Màn hình 15.6" FHD IPS 60Hz – Linh kiện: 1.800.000đ – Công thay: 200.000đ – Tổng: 2.000.000đ – Thời gian: 1–2 ngày – Bảo hành sau sửa: 3 tháng."

**A – Adjustment**
- **Cấm** trả lời chung chung kiểu "tùy model giá khác nhau"; nếu thiếu thông tin thì phải **báo giá theo khoảng** dựa trên bảng giá mẫu rồi hỏi lại dòng máy.
- Nêu rõ vỡ màn do va đập/rơi là lỗi người dùng, **không thuộc bảo hành miễn phí**.
- Giọng điệu minh bạch, lịch sự, không gây áp lực.
- Báo giá đã gồm VAT; ghi rõ giá có thể thay đổi sau khi kiểm tra thực tế.

**T – Type of Output**
Một **bảng báo giá** gồm các cột: Hạng mục | Chi tiết | Đơn giá (VNĐ) | Thời gian sửa | Bảo hành sau sửa; kèm 3 gạch đầu dòng lưu ý và 1 câu mời khách xác nhận.

**E – Extras**
- Thông tin khách/máy: *[Dòng máy, kích thước màn hình, thời điểm mua, còn bảo hành hãng hay không]*.
- Bảng giá mẫu (giả định): màn 14"–15.6" HD/FHD: 1.500.000–2.200.000đ; màn 15.6" 144Hz: 2.500.000–3.500.000đ; màn 17.3": 2.800.000–4.000.000đ; công thay: 200.000đ; phí kiểm tra: 100.000đ (miễn phí nếu khách đồng ý sửa).
- Quy định: bảo hành linh kiện thay thế 3 tháng; vỡ do tác động vật lý, vào nước không thuộc bảo hành miễn phí; thời gian sửa 1–3 ngày làm việc.

### ✅ MASTER PROMPT 3 (hoàn chỉnh)

```text
Bạn là kỹ thuật viên trưởng kiêm nhân viên tiếp nhận bảo hành của chuỗi bán lẻ công nghệ TechShop, nắm rõ bảng giá linh kiện và quy định bảo hành của công ty, luôn báo giá minh bạch và chính xác.

Nhiệm vụ: Lập báo giá thay màn hình laptop bị vỡ cho khách. Hãy: (1) xác định loại sự cố và cho biết có thuộc diện bảo hành hay không; (2) báo giá theo từng hạng mục (linh kiện + công thay + phí kiểm tra); (3) nêu thời gian sửa dự kiến, thời hạn bảo hành sau sửa và các lưu ý cho khách.

Thông tin khách/máy: [Dòng máy, kích thước màn hình, thời điểm mua, còn bảo hành hãng hay không]

Bảng giá mẫu của TechShop (đã gồm VAT):
- Màn 14"–15.6" HD/FHD: 1.500.000–2.200.000đ
- Màn 15.6" tần số quét 144Hz: 2.500.000–3.500.000đ
- Màn 17.3": 2.800.000–4.000.000đ
- Công thay: 200.000đ | Phí kiểm tra: 100.000đ (miễn phí nếu khách đồng ý sửa)

Quy định bảo hành:
- Linh kiện thay thế được bảo hành 3 tháng.
- Vỡ do va đập/rơi, vào nước thuộc lỗi người dùng, không được bảo hành miễn phí.
- Thời gian sửa: 1–3 ngày làm việc.

Mẫu một dòng báo giá:
"Màn hình 15.6" FHD IPS 60Hz – Linh kiện: 1.800.000đ – Công thay: 200.000đ – Tổng: 2.000.000đ – Thời gian: 1–2 ngày – Bảo hành sau sửa: 3 tháng."

Yêu cầu điều chỉnh:
- Cấm trả lời chung chung kiểu "tùy model giá khác nhau". Nếu thiếu thông tin, hãy báo giá theo khoảng dựa trên bảng giá mẫu rồi hỏi lại dòng máy.
- Nêu rõ vỡ màn do va đập là lỗi người dùng, không thuộc bảo hành miễn phí.
- Giọng điệu minh bạch, lịch sự, không gây áp lực.
- Ghi rõ giá có thể thay đổi sau khi kiểm tra thực tế.

Định dạng đầu ra: một bảng báo giá gồm các cột Hạng mục | Chi tiết | Đơn giá (VNĐ) | Thời gian sửa | Bảo hành sau sửa; kèm 3 gạch đầu dòng lưu ý và 1 câu mời khách xác nhận.
```

---

# PHẦN 3: ĐỐI CHIẾU TRƯỚC – SAU

| Bộ phận | Trước (sơ sài) | Sau (Master Prompt CREATE) |
|---|---|---|
| CSKH | Tin nhắn ngắn, sáo rỗng, không đền bù | Tin nhắn đủ xin lỗi – lý do – thời gian giao mới – voucher – hotline, giọng chân thành |
| Bán hàng | Liệt kê 10 dòng máy lan man | 3 mẫu đúng tầm giá, có bảng so sánh, điểm nhấn cấu hình, mẫu nên chọn |
| Bảo hành | "Tùy model giá khác nhau" | Bảng báo giá cụ thể, có quy định bảo hành và thời gian sửa |

**Kết luận:** Một prompt tốt không nằm ở độ dài mà ở việc cung cấp đủ **vai trò – nhiệm vụ – mẫu – ràng buộc – định dạng – bối cảnh**. Khi đủ 6 thành phần CREATE, AI giảm hẳn việc trả lời chung chung và nhân viên đỡ mất thời gian chỉnh sửa.
