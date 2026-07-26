# TÀI LIỆU YÊU CẦU NGHIỆP VỤ & USE CASE
## Website Bán Máy Tính Trực Tuyến — Clone HACOM (hacom.vn)
> Phân tích thực tế từ: https://hacom.vn  
> Ngày scan: 02/06/2026  
> Dùng cho: Luận án tốt nghiệp

---

## I. TỔNG QUAN HỆ THỐNG

### 1.1 Giới thiệu
HACOM là chuỗi bán lẻ điện tử chính hãng với hệ thống website thương mại điện tử chuyên bán máy tính, laptop, linh kiện, phụ kiện và các thiết bị công nghệ. Website phục vụ đồng thời khách hàng cá nhân và doanh nghiệp, kết hợp bán hàng online và hệ thống 21 showroom toàn quốc.

### 1.2 Các tác nhân (Actors)

| Actor | Mô tả |
|-------|-------|
| **Khách vãng lai (Guest)** | Người chưa đăng nhập, có thể xem sản phẩm, thêm giỏ hàng, tra cứu đơn hàng |
| **Khách hàng cá nhân (Customer)** | Đã đăng ký tài khoản, mua hàng, quản lý đơn hàng, bảo hành |
| **Khách hàng doanh nghiệp (B2B Customer)** | Mua số lượng lớn, có chính sách giá riêng |
| **Nhân viên kinh doanh (Staff)** | Xác nhận đơn hàng, tư vấn, quản lý sản phẩm |
| **Kỹ thuật viên (Technician)** | Xử lý yêu cầu bảo hành, sửa chữa |
| **Quản trị viên (Admin)** | Toàn quyền quản lý hệ thống |

---

## II. DANH MỤC CHỨC NĂNG CHÍNH

```
1.  Quản lý tài khoản người dùng
2.  Duyệt & tìm kiếm sản phẩm
3.  Xem chi tiết sản phẩm
4.  Build PC (Tự chọn cấu hình máy tính)
5.  Giỏ hàng
6.  Đặt hàng & Thanh toán
7.  Tra cứu & Quản lý đơn hàng
8.  Bảo hành & Dịch vụ sửa chữa
9.  Đánh giá sản phẩm
10. Khuyến mãi & Voucher
11. Danh sách yêu thích (Wishlist)
12. Sản phẩm đã xem
13. Tin tức / Blog công nghệ
14. Hỗ trợ khách hàng
15. Hệ thống showroom
16. Quản trị hệ thống (Admin)
```

---

## III. YÊU CẦU NGHIỆP VỤ CHI TIẾT & USE CASE

---

### MODULE 1: QUẢN LÝ TÀI KHOẢN NGƯỜI DÙNG

#### 1.1 Đăng ký tài khoản
**Mô tả:** Khách vãng lai tạo tài khoản mới để mua hàng và sử dụng các tính năng nâng cao.

**Yêu cầu nghiệp vụ:**
- Nhập họ tên, email, số điện thoại, mật khẩu
- Xác thực email hoặc OTP số điện thoại sau khi đăng ký
- Kiểm tra trùng email/SĐT đã tồn tại
- Mật khẩu tối thiểu 8 ký tự, có chữ hoa, số

**Use Case UC-01: Đăng ký tài khoản**
```
Actor:       Khách vãng lai
Tiền điều kiện: Chưa có tài khoản
Luồng chính:
  1. Khách click "Đăng ký"
  2. Điền form: họ tên, email, SĐT, mật khẩu, xác nhận mật khẩu
  3. Hệ thống validate dữ liệu
  4. Gửi email/OTP xác thực
  5. Khách xác nhận OTP
  6. Tạo tài khoản thành công, tự động đăng nhập
Luồng thay thế:
  3a. Email/SĐT đã tồn tại → thông báo lỗi
  3b. Mật khẩu không đủ mạnh → thông báo yêu cầu
  5a. OTP hết hạn → cho phép gửi lại
```

#### 1.2 Đăng nhập
**Yêu cầu nghiệp vụ:**
- Đăng nhập bằng email/SĐT + mật khẩu
- Đăng nhập bằng Google / Facebook (OAuth)
- Ghi nhớ đăng nhập (Remember me)
- Khóa tài khoản sau 5 lần nhập sai

**Use Case UC-02: Đăng nhập**
```
Actor:       Khách vãng lai
Tiền điều kiện: Đã có tài khoản
Luồng chính:
  1. Nhập email/SĐT và mật khẩu
  2. Hệ thống xác thực
  3. Đăng nhập thành công, chuyển về trang trước đó
  4. Merge giỏ hàng session vào tài khoản (nếu có)
Luồng thay thế:
  2a. Sai mật khẩu → thông báo lỗi, đếm số lần sai
  2b. Tài khoản bị khóa → thông báo liên hệ CSKH
  2c. Đăng nhập qua Google/Facebook → redirect OAuth
```

#### 1.3 Quản lý thông tin cá nhân
**Yêu cầu nghiệp vụ:**
- Cập nhật họ tên, số điện thoại, ngày sinh, giới tính, avatar
- Đổi mật khẩu (yêu cầu nhập mật khẩu cũ)
- Quên mật khẩu: gửi link reset qua email

**Use Case UC-03: Quản lý địa chỉ giao hàng**
```
Actor:       Khách hàng
Luồng chính:
  1. Vào "Địa chỉ của tôi"
  2. Thêm địa chỉ mới: họ tên, SĐT, tỉnh/thành, quận/huyện, phường/xã, địa chỉ chi tiết
  3. Đặt địa chỉ mặc định
  4. Chỉnh sửa / Xóa địa chỉ
Yêu cầu:
  - Tối đa 5 địa chỉ/tài khoản
  - Bắt buộc có 1 địa chỉ mặc định
```

---

### MODULE 2: DUYỆT & TÌM KIẾM SẢN PHẨM

#### 2.1 Danh mục sản phẩm (từ hacom.vn thực tế)
**Danh mục cấp 1 thực tế trên website:**
- Laptop, Tablet, Surface
- PC Gaming / Học tập / Văn phòng / Workstation
- Linh kiện máy tính (CPU, Mainboard, RAM, SSD, HDD, VGA, PSU, Case)
- Màn hình máy tính
- Phím chuột, Bàn ghế, Gaming Gear
- Tản nhiệt, Fan, Đèn LED
- Loa, Tai nghe, Mic, Webcam
- Camera, Thiết bị an ninh
- Thiết bị mạng, Lưu trữ
- Thiết bị văn phòng, Hội nghị
- Thiết bị siêu thị, POS
- Console & Game (PS5, Xbox, Nintendo)
- Hàng cũ / Thanh lý

**Yêu cầu nghiệp vụ:**
- Hiển thị menu danh mục đa cấp (tối thiểu 2 cấp)
- Lọc theo: thương hiệu, khoảng giá, thông số kỹ thuật, tình trạng hàng
- Sắp xếp: giá tăng/giảm, mới nhất, bán chạy nhất, đánh giá cao nhất
- Phân trang hoặc load-more
- Hiển thị số lượng sản phẩm trong danh mục

**Use Case UC-04: Lọc & Sắp xếp sản phẩm**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Vào trang danh mục (ví dụ: Laptop Gaming)
  2. Chọn bộ lọc: Brand (ASUS, MSI...), Giá (10-20tr), RAM (16GB)...
  3. Hệ thống cập nhật kết quả realtime (không reload trang)
  4. Sắp xếp theo tiêu chí mong muốn
  5. Xem danh sách sản phẩm đã lọc
```

#### 2.2 Tìm kiếm sản phẩm

**Yêu cầu nghiệp vụ:**
- Tìm kiếm full-text theo tên sản phẩm, SKU, thương hiệu
- Gợi ý tự động (autocomplete) khi gõ
- Tìm kiếm không dấu tiếng Việt
- Highlight từ khóa trong kết quả
- Lịch sử tìm kiếm gần đây

**Use Case UC-05: Tìm kiếm sản phẩm**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Nhập từ khóa vào ô tìm kiếm
  2. Hệ thống gợi ý sản phẩm liên quan (dropdown)
  3. Nhấn Enter → chuyển trang kết quả
  4. Hiển thị kết quả, cho phép lọc thêm
Luồng thay thế:
  4a. Không tìm thấy → gợi ý sản phẩm tương tự hoặc "Từ khóa phổ biến"
```

---

### MODULE 3: XEM CHI TIẾT SẢN PHẨM

**Yêu cầu nghiệp vụ:**
- Hiển thị gallery ảnh (zoom, slideshow)
- Giá bán, giá gốc, % giảm giá
- Thông số kỹ thuật đầy đủ (CPU, RAM, màn hình, pin, OS...)
- Tình trạng hàng (Còn hàng / Hết hàng / Pre-order)
- Chính sách bảo hành (12-36 tháng)
- Sản phẩm liên quan / Có thể bạn quan tâm
- Chia sẻ lên mạng xã hội

**Use Case UC-06: Xem chi tiết sản phẩm**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Click vào sản phẩm từ danh sách
  2. Xem ảnh sản phẩm (gallery), giá, mô tả ngắn
  3. Click "Thông số kỹ thuật" → xem bảng thông số chi tiết
  4. Kéo xuống xem đánh giá từ người mua
  5. Xem sản phẩm liên quan
  6. Chọn "Thêm vào giỏ hàng" hoặc "Mua ngay"
  7. Hệ thống ghi nhận lượt xem
```

---

### MODULE 4: BUILD PC — XÂY DỰNG CẤU HÌNH MÁY TÍNH

> Đây là tính năng đặc trưng và nổi bật nhất của hacom.vn

**Yêu cầu nghiệp vụ (từ scan thực tế):**
- Chọn từng linh kiện theo thứ tự: CPU → Mainboard → RAM → SSD → HDD → VGA → Nguồn PSU → Vỏ Case → Màn hình → Bàn phím → Chuột → Tai nghe → Loa → Ghế Gaming → Tản nhiệt → Windows bản quyền
- Hệ thống tự động tính tổng giá realtime
- Chọn showroom (để kiểm tra tồn kho tại cửa hàng)
- Áp dụng chính sách khuyến mãi Build PC (giảm đến 50% CPU khi lắp đủ bộ)
- Lưu cấu hình để dùng sau
- Xuất file Excel cấu hình
- Tải ảnh cấu hình (để chia sẻ)
- In cấu hình
- Thêm toàn bộ vào giỏ hàng 1 lần

**Chính sách Build PC (từ website thực tế):**
- Giảm đến 50% CPU khi mua đủ: Mainboard + SSD + RAM + Case + Nguồn + VGA từ RX6500XT/RTX3050 trở lên
- Giảm đến 30% CPU khi mua đủ: Mainboard + SSD + RAM + Case + Nguồn (không kèm VGA mạnh)
- Giảm tiền mặt thêm theo tổng giá trị bộ PC (tối đa 30 triệu)

**Use Case UC-07: Build PC**
```
Actor:       Khách vãng lai / Khách hàng
Tiền điều kiện: Vào trang /buildpc
Luồng chính:
  1. Chọn showroom hoặc "Kho Online"
  2. Chọn CPU: hiển thị danh sách + giá, lọc theo socket/hãng
  3. Chọn Mainboard: hệ thống gợi ý compatible với CPU đã chọn
  4. Chọn RAM: lọc theo DDR4/DDR5, dung lượng
  5. Chọn SSD/HDD, VGA, Nguồn, Case, Tản nhiệt...
  6. Tổng giá được tính realtime, hiển thị khuyến mãi áp dụng
  7. Xem tóm tắt đơn hàng Build PC
  8. Chọn: Lưu / Xuất Excel / Tải ảnh / Thêm vào giỏ hàng
Luồng thay thế:
  3a. Mainboard không tương thích CPU → cảnh báo
  8a. Chưa đăng nhập → yêu cầu đăng nhập để lưu cấu hình

Use Case UC-08: Quản lý cấu hình đã lưu
  1. Xem danh sách cấu hình đã lưu
  2. Đặt tên cấu hình
  3. Chỉnh sửa / Xóa / Nhân bản cấu hình
  4. Chia sẻ link cấu hình
```

---

### MODULE 5: GIỎ HÀNG

**Yêu cầu nghiệp vụ:**
- Thêm sản phẩm vào giỏ từ danh sách, trang chi tiết, hoặc Build PC
- Giỏ hàng hoạt động với cả khách vãng lai (lưu session) và đã đăng nhập (lưu DB)
- Khi đăng nhập: tự động merge giỏ hàng session + giỏ hàng tài khoản
- Cập nhật số lượng, xóa từng sản phẩm
- Tính tổng tiền realtime
- Hiển thị số lượng sản phẩm trên icon giỏ hàng header
- Lưu giỏ hàng tối đa 30 ngày

**Use Case UC-09: Quản lý giỏ hàng**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Thêm sản phẩm → icon giỏ hàng cập nhật số lượng
  2. Click icon giỏ hàng → xem danh sách sản phẩm
  3. Thay đổi số lượng (tăng/giảm/nhập tay)
  4. Xóa từng sản phẩm hoặc tất cả
  5. Xem tổng giá tạm tính
  6. Click "Tiến hành thanh toán"
Luồng thay thế:
  3a. Số lượng vượt tồn kho → báo giới hạn
  6a. Giỏ hàng trống → không cho tiếp tục
```

---

### MODULE 6: ĐẶT HÀNG & THANH TOÁN

**Yêu cầu nghiệp vụ:**

**Bước 1 - Thông tin giao hàng:**
- Chọn địa chỉ đã lưu hoặc nhập mới
- Chọn phương thức nhận hàng: Giao tận nơi / Nhận tại showroom
- Chọn showroom nhận hàng (nếu nhận tại cửa hàng)
- Ghi chú đơn hàng

**Bước 2 - Phương thức vận chuyển:**
- Giao hàng tiêu chuẩn (2-3 ngày)
- Giao hàng nhanh (1-2 ngày)
- Giao hỏa tốc (4 giờ - nội thành HN, HCM)
- Miễn phí giao hàng toàn quốc (theo chính sách HACOM)

**Bước 3 - Phương thức thanh toán (từ website thực tế):**
- Tiền mặt khi nhận hàng (COD)
- Chuyển khoản ngân hàng
- Ví điện tử: VNPay, Momo, ZaloPay
- Trả góp 0%: HomeCredit, FE Credit, HSBC, Shinhan, các ngân hàng

**Bước 4 - Áp dụng voucher/khuyến mãi:**
- Nhập mã voucher
- Hiển thị chương trình khuyến mãi đang áp dụng tự động

**Bước 5 - Xác nhận đơn hàng:**
- Hiển thị tóm tắt toàn bộ đơn hàng
- Xác nhận → Tạo đơn hàng → Gửi email xác nhận

**Use Case UC-10: Đặt hàng**
```
Actor:       Khách hàng (đã đăng nhập)
Tiền điều kiện: Giỏ hàng có ít nhất 1 sản phẩm
Luồng chính:
  1. Click "Tiến hành thanh toán" từ giỏ hàng
  2. Chọn/nhập địa chỉ giao hàng
  3. Chọn phương thức vận chuyển (hệ thống tính phí ship)
  4. Nhập mã voucher (tùy chọn)
  5. Chọn phương thức thanh toán
  6. Xem tóm tắt đơn hàng: sản phẩm, phí ship, giảm giá, tổng cộng
  7. Click "Đặt hàng"
  8. Hệ thống tạo mã đơn hàng (VD: HC-2024-000001)
  9. Gửi email xác nhận kèm chi tiết đơn hàng
  10. Chuyển đến trang "Đặt hàng thành công"
Luồng thay thế:
  3a. Địa chỉ ngoài vùng giao → thông báo chỉ nhận tại cửa hàng
  4a. Mã voucher không hợp lệ/hết hạn → thông báo lỗi
  5a. Thanh toán VNPay/Momo → redirect sang cổng TT, callback về hệ thống
  7a. Sản phẩm vừa hết hàng → thông báo, cho phép xóa hoặc chờ
```

**Use Case UC-11: Thanh toán trả góp**
```
Actor:       Khách hàng
Tiền điều kiện: Đơn hàng đủ điều kiện trả góp (thường >= 3 triệu)
Luồng chính:
  1. Chọn "Trả góp 0%" trong phương thức thanh toán
  2. Chọn đơn vị tài chính (HomeCredit, FE Credit...)
  3. Chọn kỳ hạn (6, 12, 24 tháng)
  4. Hệ thống hiển thị số tiền trả mỗi tháng
  5. Điền thông tin hồ sơ trả góp
  6. Đặt hàng → nhân viên liên hệ hỗ trợ hoàn tất thủ tục
```

---

### MODULE 7: TRA CỨU & QUẢN LÝ ĐƠN HÀNG

**Yêu cầu nghiệp vụ:**

**7.1 Tra cứu đơn hàng (không cần đăng nhập):**
- Nhập mã đơn hàng + SĐT/email đặt hàng
- Xem trạng thái, thông tin giao hàng, tracking

**7.2 Quản lý đơn hàng (đã đăng nhập):**
- Xem danh sách tất cả đơn hàng
- Lọc theo trạng thái: Chờ xác nhận / Đang xử lý / Đang giao / Đã giao / Đã hủy
- Xem chi tiết từng đơn hàng
- Hủy đơn (chỉ khi chưa xác nhận / chưa xuất kho)
- Yêu cầu đổi trả (trong 15 ngày)
- In hóa đơn điện tử
- Mua lại (thêm vào giỏ hàng nhanh)

**Vòng đời đơn hàng:**
```
Chờ xác nhận → Đã xác nhận → Đang xử lý → Đang giao → Đã giao → Hoàn thành
                                                                  ↕
                                                              Đổi/Trả
         ↓ (hủy tại bất kỳ bước nào trước khi xuất kho)
                     Đã hủy
```

**Use Case UC-12: Tra cứu đơn hàng**
```
Actor:       Khách vãng lai
Luồng chính:
  1. Vào /tra-don-hang
  2. Nhập mã đơn hàng + SĐT đặt hàng
  3. Hệ thống trả về thông tin đơn hàng
  4. Xem trạng thái, sản phẩm, địa chỉ giao hàng, timeline
Luồng thay thế:
  2a. Mã đơn hàng không tồn tại → thông báo lỗi
```

**Use Case UC-13: Hủy đơn hàng**
```
Actor:       Khách hàng
Tiền điều kiện: Đơn hàng đang ở trạng thái "Chờ xác nhận"
Luồng chính:
  1. Vào chi tiết đơn hàng
  2. Click "Hủy đơn"
  3. Chọn lý do hủy (từ danh sách + ghi chú thêm)
  4. Xác nhận hủy
  5. Hệ thống cập nhật trạng thái, hoàn lại tồn kho
  6. Gửi email thông báo hủy thành công
  7. Nếu đã thanh toán online → tạo yêu cầu hoàn tiền
```

**Use Case UC-14: Yêu cầu đổi/trả hàng**
```
Actor:       Khách hàng
Tiền điều kiện: Đơn hàng đã giao, trong vòng 15 ngày
Luồng chính:
  1. Vào chi tiết đơn hàng → "Yêu cầu đổi trả"
  2. Chọn sản phẩm cần đổi/trả
  3. Chọn lý do: lỗi sản phẩm / sai hàng / không ưng ý
  4. Tải ảnh/video mô tả vấn đề
  5. Gửi yêu cầu
  6. Nhân viên CSKH xem xét và liên hệ lại trong 24h
```

**Use Case UC-15: In hóa đơn điện tử**
```
Actor:       Khách hàng
Tiền điều kiện: Đơn hàng đã hoàn thành, đã thanh toán
Luồng chính:
  1. Vào chi tiết đơn hàng
  2. Click "In hóa đơn điện tử"
  3. Nhập thông tin công ty (nếu xuất hóa đơn doanh nghiệp)
  4. Hệ thống tạo PDF hóa đơn
  5. Tải về hoặc gửi qua email
```

---

### MODULE 8: BẢO HÀNH & DỊCH VỤ SỬA CHỮA

> Tính năng thực tế trên hacom.vn: Tra cứu bảo hành trước 2025 và từ 2025 (2 hệ thống khác nhau)

**Yêu cầu nghiệp vụ:**

**8.1 Tra cứu bảo hành:**
- Tra cứu theo số serial máy hoặc mã đơn hàng
- Hiển thị: ngày mua, thời hạn bảo hành, trạng thái (còn/hết)
- Không cần đăng nhập

**8.2 Yêu cầu bảo hành / Sửa chữa:**
- Mô tả lỗi, tải ảnh minh chứng
- Chọn hình thức: mang đến showroom / gửi bưu điện
- Theo dõi tiến độ sửa chữa online

**8.3 Dịch vụ bảo hành mở rộng:**
- Mua thêm gói bảo hành mở rộng (gia hạn thêm 1-2 năm)

**Vòng đời yêu cầu bảo hành:**
```
Tiếp nhận → Đang kiểm tra → Đang sửa chữa → Chờ linh kiện → Hoàn tất → Đã trả khách
```

**Use Case UC-16: Tra cứu bảo hành**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Vào /tra-bao-hanh-tu-2025
  2. Nhập số serial máy hoặc mã đơn hàng
  3. Hệ thống hiển thị: tên sản phẩm, ngày mua, hạn bảo hành, trạng thái
Luồng thay thế:
  2a. Serial không tìm thấy → hướng dẫn liên hệ hotline
```

**Use Case UC-17: Tạo yêu cầu sửa chữa**
```
Actor:       Khách hàng
Luồng chính:
  1. Đăng nhập → "Yêu cầu sửa chữa"
  2. Chọn sản phẩm (từ danh sách đã mua) hoặc nhập thủ công
  3. Mô tả triệu chứng lỗi
  4. Tải ảnh/video lỗi
  5. Chọn showroom tiếp nhận
  6. Chọn ngày hẹn mang máy đến
  7. Hệ thống tạo mã dịch vụ (ticket)
  8. Gửi SMS/email xác nhận hẹn
```

---

### MODULE 9: ĐÁNH GIÁ SẢN PHẨM

**Yêu cầu nghiệp vụ:**
- Chỉ khách hàng đã mua sản phẩm mới được đánh giá (verified purchase)
- Rating từ 1-5 sao
- Viết nhận xét + tải ảnh thực tế
- Đánh dấu review hữu ích
- Phân trang review theo rating
- Admin có thể ẩn review vi phạm

**Use Case UC-18: Đánh giá sản phẩm**
```
Actor:       Khách hàng (đã mua sản phẩm)
Tiền điều kiện: Đơn hàng chứa sản phẩm đó đã hoàn thành
Luồng chính:
  1. Hệ thống gửi email nhắc đánh giá sau khi nhận hàng 3 ngày
  2. Khách vào trang đánh giá / click từ email
  3. Chọn số sao (1-5)
  4. Viết tiêu đề + nội dung nhận xét
  5. Tải ảnh thực tế (tùy chọn)
  6. Submit → hiển thị ngay trên trang sản phẩm
  7. Cập nhật điểm rating trung bình sản phẩm (trigger tự động)
Luồng thay thế:
  1a. Khách chủ động vào trang sản phẩm để đánh giá
  6a. Nội dung vi phạm → giữ lại để admin duyệt
```

---

### MODULE 10: KHUYẾN MÃI & VOUCHER

**Yêu cầu nghiệp vụ:**

**10.1 Chương trình khuyến mãi:**
- Giảm giá theo danh mục / thương hiệu / sản phẩm cụ thể
- Hiển thị thẻ "SALE", "Giảm X%", "Giảm Xđ" trên sản phẩm
- Khuyến mãi có thời hạn (hiển thị đồng hồ đếm ngược)
- Tặng quà khi mua combo
- Ưu đãi học sinh sinh viên

**10.2 Mã voucher:**
- Nhập mã khi thanh toán
- Voucher giảm theo % hoặc số tiền cố định
- Voucher free ship
- Giới hạn số lần dùng / giới hạn per user
- Yêu cầu đơn tối thiểu

**Use Case UC-19: Sử dụng voucher**
```
Actor:       Khách hàng
Tiền điều kiện: Có mã voucher hợp lệ
Luồng chính:
  1. Ở trang thanh toán, nhập mã voucher
  2. Click "Áp dụng"
  3. Hệ thống kiểm tra: hiệu lực, điều kiện đơn tối thiểu, giới hạn dùng
  4. Hiển thị số tiền được giảm
  5. Tổng tiền được cập nhật
Luồng thay thế:
  3a. Voucher hết hạn → thông báo
  3b. Đơn chưa đủ điều kiện tối thiểu → thông báo còn thiếu bao nhiêu
  3c. Đã dùng hết lượt → thông báo
```

---

### MODULE 11: WISHLIST & SẢN PHẨM ĐÃ XEM

**Use Case UC-20: Quản lý danh sách yêu thích**
```
Actor:       Khách hàng
Luồng chính:
  1. Click icon tim trên sản phẩm → thêm vào wishlist
  2. Vào "Yêu thích" → xem danh sách
  3. Xóa khỏi wishlist
  4. Chuyển từ wishlist sang giỏ hàng
  5. Nhận thông báo khi sản phẩm yêu thích giảm giá
```

**Use Case UC-21: Sản phẩm đã xem**
```
Actor:       Khách vãng lai / Khách hàng
Luồng chính:
  1. Mỗi sản phẩm xem → ghi nhận vào lịch sử
  2. Vào /san-pham-da-xem → xem danh sách (tối đa 20 sản phẩm gần nhất)
  3. Xóa lịch sử xem
```

---

### MODULE 12: TIN TỨC / BLOG CÔNG NGHỆ

**Yêu cầu nghiệp vụ:**
- Đăng bài review sản phẩm, tin tức công nghệ, hướng dẫn
- Phân loại: Tin khuyến mãi / Review / Hướng dẫn / Sự kiện
- Tìm kiếm bài viết
- Đếm lượt xem
- Chia sẻ lên mạng xã hội
- Liên kết bài viết với sản phẩm đề cập

**Use Case UC-22: Đọc tin tức**
```
Actor:       Khách vãng lai
Luồng chính:
  1. Vào /tin-tuc → danh sách bài viết
  2. Lọc theo danh mục tin tức
  3. Click vào bài → đọc chi tiết
  4. Click vào sản phẩm được đề cập → chuyển sang trang sản phẩm
  5. Chia sẻ bài viết
```

---

### MODULE 13: HỖ TRỢ KHÁCH HÀNG

**Yêu cầu nghiệp vụ (từ hacom.vn thực tế):**

**13.1 Các kênh hỗ trợ:**
- Chat trực tuyến qua Facebook Messenger (8h-21h)
- Chat Zalo (8h-21h)
- Gọi hotline: 1900 1903 (8h-21h)
- Form góp ý / khiếu nại

**13.2 Đăng ký nhận email thông báo khuyến mãi**

**13.3 Hướng dẫn:**
- Hướng dẫn mua hàng trực tuyến
- Hướng dẫn thanh toán
- Hướng dẫn mua trả góp
- Bảng giá dịch vụ sửa chữa lắp đặt

**Use Case UC-23: Gửi góp ý / Khiếu nại**
```
Actor:       Khách hàng
Luồng chính:
  1. Vào /gop-y-khieu-nai
  2. Chọn loại: Góp ý / Khiếu nại / Yêu cầu hỗ trợ
  3. Nhập thông tin liên hệ, mã đơn hàng liên quan
  4. Mô tả vấn đề
  5. Gửi → Hệ thống tạo ticket hỗ trợ
  6. Gửi email xác nhận kèm mã ticket
  7. Nhân viên xử lý và phản hồi trong 24h
```

**Use Case UC-24: Đăng ký nhận thông báo khuyến mãi**
```
Actor:       Khách vãng lai
Luồng chính:
  1. Nhập email vào form cuối trang
  2. Click "Gửi"
  3. Hệ thống lưu email, gửi email xác nhận đăng ký
  4. Nhận thông báo khi có chương trình khuyến mãi mới
```

---

### MODULE 14: HỆ THỐNG SHOWROOM

**Yêu cầu nghiệp vụ (từ thực tế: 21 showroom):**
- Xem danh sách showroom theo tỉnh/thành: Hà Nội, Hải Phòng, TP.HCM, các tỉnh
- Xem địa chỉ, SĐT, giờ mở cửa, email từng showroom
- Xem ảnh thực tế showroom
- Xem bản đồ Google Maps
- Kiểm tra tồn kho theo showroom (tích hợp trong Build PC)

**Use Case UC-25: Tìm showroom gần nhất**
```
Actor:       Khách vãng lai
Luồng chính:
  1. Vào trang showroom / click "Tìm cửa hàng gần nhất"
  2. Cho phép truy cập vị trí (tùy chọn)
  3. Hiển thị showroom gần nhất hoặc theo tỉnh/thành
  4. Xem thông tin chi tiết showroom
  5. Click "Xem bản đồ" → mở Google Maps
  6. Click "Xem ảnh thực tế" → gallery ảnh showroom
```

---

### MODULE 15: QUẢN TRỊ HỆ THỐNG (ADMIN)

#### 15.1 Quản lý sản phẩm
**Use Case UC-26: CRUD Sản phẩm**
```
Actor:       Admin / Staff
Luồng chính:
  - Thêm sản phẩm mới: tên, danh mục, thương hiệu, giá, tồn kho, ảnh, thông số kỹ thuật
  - Chỉnh sửa thông tin sản phẩm
  - Ẩn/Hiện sản phẩm
  - Quản lý tồn kho (nhập kho, điều chuyển)
  - Import sản phẩm hàng loạt qua Excel
  - Quản lý giá theo showroom
```

#### 15.2 Quản lý đơn hàng
**Use Case UC-27: Xử lý đơn hàng**
```
Actor:       Staff / Admin
Luồng chính:
  1. Xem danh sách đơn hàng mới (pending)
  2. Xác nhận đơn → trừ tồn kho tự động
  3. Cập nhật trạng thái: Đang xử lý → Đang giao
  4. Nhập mã tracking vận chuyển
  5. Xác nhận giao thành công
  6. Ghi chú nội bộ cho đơn hàng
  7. Xử lý đổi/trả
```

#### 15.3 Quản lý khuyến mãi
**Use Case UC-28: Tạo chương trình khuyến mãi**
```
Actor:       Admin
Luồng chính:
  1. Tạo chương trình: tên, loại giảm giá, % hoặc số tiền, thời gian
  2. Chọn phạm vi: tất cả / danh mục / thương hiệu / sản phẩm cụ thể
  3. Kích hoạt / Dừng chương trình
  4. Xem báo cáo hiệu quả khuyến mãi

Use Case UC-29: Tạo voucher
  1. Nhập mã voucher hoặc tạo tự động
  2. Cấu hình: loại giảm, giá trị, đơn tối thiểu, số lần dùng, thời hạn
  3. Giới hạn đối tượng (tất cả / nhóm khách hàng cụ thể)
  4. Xuất danh sách voucher
```

#### 15.4 Quản lý bảo hành
**Use Case UC-30: Xử lý yêu cầu bảo hành**
```
Actor:       Kỹ thuật viên / Staff
Luồng chính:
  1. Tiếp nhận yêu cầu, tạo phiếu dịch vụ
  2. Kiểm tra máy, cập nhật chẩn đoán
  3. Cập nhật trạng thái xử lý
  4. Báo giá sửa chữa (nếu ngoài bảo hành)
  5. Khách duyệt / từ chối sửa
  6. Hoàn tất, thông báo khách đến lấy máy
```

#### 15.5 Báo cáo & Thống kê
**Use Case UC-31: Xem báo cáo kinh doanh**
```
Actor:       Admin
Chức năng:
  - Doanh thu theo ngày/tuần/tháng/năm
  - Top sản phẩm bán chạy
  - Đơn hàng theo trạng thái
  - Khách hàng mới / quay lại
  - Hiệu quả chương trình khuyến mãi
  - Tồn kho cảnh báo (sắp hết hàng)
  - Báo cáo theo showroom
```

#### 15.6 Quản lý nội dung
```
  - CRUD danh mục sản phẩm
  - CRUD thương hiệu
  - Quản lý banner/slider trang chủ
  - Quản lý bài viết blog
  - Quản lý showroom
```

---

## IV. YÊU CẦU PHI CHỨC NĂNG

### 4.1 Hiệu năng
- Trang chủ load trong < 3 giây
- Tìm kiếm trả kết quả trong < 1 giây
- Hỗ trợ tối thiểu 1,000 người dùng đồng thời
- Ảnh sản phẩm được nén và phục vụ qua CDN

### 4.2 Bảo mật
- HTTPS toàn bộ website
- Mật khẩu lưu trữ bằng bcrypt
- JWT/Session cho xác thực
- Chống SQL Injection, XSS
- Rate limiting API (chống brute force)
- Bảo mật thông tin khách hàng (theo chính sách hacom.vn)

### 4.3 Khả năng sử dụng
- Responsive: desktop, tablet, mobile
- Hỗ trợ tiếng Việt đầy đủ
- Tìm kiếm không dấu

### 4.4 Tích hợp bên thứ 3
- Cổng thanh toán: VNPay, Momo, ZaloPay
- Google Maps (showroom)
- Facebook / Google OAuth
- Đơn vị vận chuyển: GHN, GHTK, VNPost
- Email service (SMTP)
- SMS OTP

---

## V. TỔNG HỢP USE CASE DIAGRAM

### Nhóm theo Actor

**Khách vãng lai (Guest):**
- UC-01: Đăng ký tài khoản
- UC-02: Đăng nhập
- UC-04: Lọc & sắp xếp sản phẩm
- UC-05: Tìm kiếm sản phẩm
- UC-06: Xem chi tiết sản phẩm
- UC-07: Build PC
- UC-09: Quản lý giỏ hàng
- UC-12: Tra cứu đơn hàng
- UC-16: Tra cứu bảo hành
- UC-22: Đọc tin tức
- UC-24: Đăng ký nhận thông báo
- UC-25: Tìm showroom

**Khách hàng (Customer — đã đăng nhập):**
- Tất cả UC của Guest +
- UC-03: Quản lý địa chỉ giao hàng
- UC-08: Quản lý cấu hình Build PC đã lưu
- UC-10: Đặt hàng
- UC-11: Thanh toán trả góp
- UC-13: Hủy đơn hàng
- UC-14: Yêu cầu đổi/trả
- UC-15: In hóa đơn điện tử
- UC-17: Tạo yêu cầu sửa chữa
- UC-18: Đánh giá sản phẩm
- UC-19: Sử dụng voucher
- UC-20: Quản lý wishlist
- UC-21: Xem sản phẩm đã xem
- UC-23: Gửi góp ý / khiếu nại

**Nhân viên (Staff):**
- UC-26: Quản lý sản phẩm (hạn chế)
- UC-27: Xử lý đơn hàng
- UC-30: Xử lý bảo hành

**Quản trị viên (Admin):**
- Tất cả UC của Staff +
- UC-28: Tạo khuyến mãi
- UC-29: Tạo voucher
- UC-31: Xem báo cáo
- Quản lý danh mục, banner, blog, showroom, người dùng

---

## VI. BẢNG TÓM TẮT USE CASE

| Mã UC | Tên Use Case | Actor chính | Độ ưu tiên |
|-------|-------------|-------------|------------|
| UC-01 | Đăng ký tài khoản | Guest | Cao |
| UC-02 | Đăng nhập | Guest | Cao |
| UC-03 | Quản lý địa chỉ | Customer | Cao |
| UC-04 | Lọc sản phẩm | Guest | Cao |
| UC-05 | Tìm kiếm | Guest | Cao |
| UC-06 | Xem chi tiết SP | Guest | Cao |
| UC-07 | Build PC | Guest | Cao |
| UC-08 | Quản lý cấu hình PC | Customer | Trung bình |
| UC-09 | Giỏ hàng | Guest | Cao |
| UC-10 | Đặt hàng | Customer | Cao |
| UC-11 | Trả góp | Customer | Trung bình |
| UC-12 | Tra cứu đơn hàng | Guest | Cao |
| UC-13 | Hủy đơn hàng | Customer | Cao |
| UC-14 | Đổi/Trả hàng | Customer | Cao |
| UC-15 | In hóa đơn | Customer | Trung bình |
| UC-16 | Tra cứu bảo hành | Guest | Cao |
| UC-17 | Yêu cầu sửa chữa | Customer | Trung bình |
| UC-18 | Đánh giá SP | Customer | Trung bình |
| UC-19 | Sử dụng voucher | Customer | Cao |
| UC-20 | Wishlist | Customer | Thấp |
| UC-21 | SP đã xem | Guest | Thấp |
| UC-22 | Đọc tin tức | Guest | Thấp |
| UC-23 | Góp ý/Khiếu nại | Customer | Trung bình |
| UC-24 | Đăng ký email | Guest | Thấp |
| UC-25 | Tìm showroom | Guest | Trung bình |
| UC-26 | CRUD sản phẩm | Admin | Cao |
| UC-27 | Xử lý đơn hàng | Staff | Cao |
| UC-28 | Tạo khuyến mãi | Admin | Cao |
| UC-29 | Tạo voucher | Admin | Trung bình |
| UC-30 | Xử lý bảo hành | Technician | Trung bình |
| UC-31 | Báo cáo | Admin | Trung bình |

---

*Tài liệu được tổng hợp từ phân tích thực tế website https://hacom.vn — Tháng 06/2026*
