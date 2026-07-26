# SOFTWARE REQUIREMENTS SPECIFICATION (SRS)
## Hệ thống Website Bán Máy Tính Trực Tuyến
### (Clone & Phát triển dựa trên hacom.vn)

---

| Thông tin | Nội dung |
|-----------|---------|
| **Tên dự án** | Website Bán Máy Tính Trực Tuyến — HACOM Clone |
| **Phiên bản** | 1.0 |
| **Ngày tạo** | 02/06/2026 |
| **Nguồn phân tích** | https://hacom.vn |
| **Mục đích** | Luận án tốt nghiệp |
| **Tiêu chuẩn** | IEEE Std 830-1998 (SRS Standard) |

---

## MỤC LỤC

1. [Giới thiệu](#1-giới-thiệu)
2. [Mô tả tổng quan](#2-mô-tả-tổng-quan)
3. [Yêu cầu chức năng](#3-yêu-cầu-chức-năng)
4. [Yêu cầu phi chức năng](#4-yêu-cầu-phi-chức-năng)
5. [Ràng buộc thiết kế](#5-ràng-buộc-thiết-kế)
6. [Giao diện hệ thống](#6-giao-diện-hệ-thống)

---

## 1. GIỚI THIỆU

### 1.1 Mục đích tài liệu
Tài liệu này mô tả đầy đủ các yêu cầu phần mềm cho hệ thống website thương mại điện tử bán máy tính trực tuyến, được phát triển dựa trên phân tích thực tế từ hacom.vn. Tài liệu phục vụ làm cơ sở thiết kế, phát triển và kiểm thử hệ thống trong khuôn khổ luận án tốt nghiệp.

### 1.2 Phạm vi hệ thống
Hệ thống bao gồm:
- **Website Frontend**: Giao diện người dùng (khách hàng)
- **Admin Panel**: Giao diện quản trị (nhân viên, admin)
- **Backend API**: RESTful API xử lý nghiệp vụ
- **Database**: PostgreSQL lưu trữ dữ liệu
- **Tích hợp**: Cổng thanh toán, Email/SMS, Google Maps

### 1.3 Định nghĩa & Thuật ngữ

| Thuật ngữ | Định nghĩa |
|-----------|-----------|
| SKU | Stock Keeping Unit — Mã định danh sản phẩm |
| Build PC | Tính năng tự chọn linh kiện lắp ráp máy tính |
| COD | Cash On Delivery — Thanh toán khi nhận hàng |
| OTP | One-Time Password — Mật khẩu dùng một lần |
| CDN | Content Delivery Network — Mạng phân phối nội dung |
| JWT | JSON Web Token — Token xác thực |
| Voucher | Mã giảm giá nhập tay khi thanh toán |
| Promotion | Chương trình khuyến mãi tự động |
| Warranty | Chính sách bảo hành sản phẩm |

### 1.4 Tài liệu tham khảo
- IEEE Std 830-1998: Recommended Practice for SRS
- Phân tích thực tế website: https://hacom.vn (scan ngày 02/06/2026)
- Tài liệu Use Case: `YeuCauNghiepVu_HACOM.md`
- Database Schema: `database/schema.sql`

---

## 2. MÔ TẢ TỔNG QUAN

### 2.1 Bối cảnh sản phẩm

```
┌─────────────────────────────────────────────────────────┐
│                   HACOM SYSTEM                          │
│                                                         │
│  ┌──────────┐    ┌──────────────┐    ┌───────────────┐  │
│  │ Frontend │◄──►│  Backend API │◄──►│  PostgreSQL   │  │
│  │ (Web App)│    │  (REST API)  │    │   Database    │  │
│  └──────────┘    └──────┬───────┘    └───────────────┘  │
│                         │                               │
│              ┌──────────┼──────────┐                    │
│              ▼          ▼          ▼                    │
│         ┌─────────┐ ┌───────┐ ┌──────────┐             │
│         │ VNPay   │ │ Email │ │ G.Maps   │             │
│         │ Momo    │ │  SMS  │ │   API    │             │
│         │ ZaloPay │ │       │ │          │             │
│         └─────────┘ └───────┘ └──────────┘             │
└─────────────────────────────────────────────────────────┘
```

### 2.2 Chức năng tổng quan sản phẩm

Hệ thống cung cấp nền tảng thương mại điện tử chuyên ngành công nghệ với các chức năng cốt lõi:

1. Bán hàng trực tuyến đa danh mục (laptop, PC, linh kiện, phụ kiện)
2. Tính năng Build PC — tự chọn và lắp ráp máy tính
3. Quản lý vòng đời đơn hàng end-to-end
4. Hệ thống bảo hành điện tử
5. Quản trị nội dung và báo cáo kinh doanh

### 2.3 Đặc điểm người dùng

| Nhóm người dùng | Tần suất sử dụng | Kỹ năng kỹ thuật | Đặc điểm |
|-----------------|-----------------|------------------|----------|
| Khách vãng lai | Thấp | Cơ bản | Tìm kiếm, xem giá |
| Khách hàng cá nhân | Trung bình | Cơ bản–Trung bình | Mua hàng, theo dõi đơn |
| Khách hàng doanh nghiệp | Cao | Trung bình | Mua số lượng lớn |
| Nhân viên kinh doanh | Rất cao | Trung bình–Cao | Xử lý đơn, CSKH |
| Kỹ thuật viên | Cao | Cao | Bảo hành, sửa chữa |
| Quản trị viên | Cao | Cao | Toàn quyền hệ thống |

### 2.4 Giả định và phụ thuộc
- Hệ thống yêu cầu kết nối internet ổn định
- Cổng thanh toán bên thứ 3 hoạt động bình thường
- Dịch vụ gửi Email/SMS khả dụng 24/7
- Dữ liệu tỉnh/huyện/xã Việt Nam được cập nhật đầy đủ

---

## 3. YÊU CẦU CHỨC NĂNG

### 3.1 MODULE QUẢN LÝ TÀI KHOẢN

#### FR-01: Đăng ký tài khoản
| Thuộc tính | Mô tả |
|-----------|-------|
| **Mã** | FR-01 |
| **Tên** | Đăng ký tài khoản khách hàng |
| **Mức ưu tiên** | Cao |
| **Mô tả** | Hệ thống cho phép khách vãng lai tạo tài khoản mới |
| **Input** | Họ tên, email, số điện thoại, mật khẩu, xác nhận mật khẩu |
| **Output** | Tài khoản được tạo, OTP gửi qua SĐT/email |
| **Xử lý** | Validate → Kiểm tra trùng → Hash mật khẩu → Gửi OTP → Kích hoạt |

**Ràng buộc dữ liệu:**
- Email: đúng định dạng RFC 5322, độc nhất trong hệ thống
- Số điện thoại: 10 số, bắt đầu bằng 0, độc nhất
- Mật khẩu: tối thiểu 8 ký tự, có ít nhất 1 chữ hoa và 1 số
- OTP: 6 chữ số, hết hạn sau 5 phút, tối đa gửi lại 3 lần/giờ

#### FR-02: Đăng nhập
| Thuộc tính | Mô tả |
|-----------|-------|
| **Mã** | FR-02 |
| **Tên** | Đăng nhập tài khoản |
| **Mức ưu tiên** | Cao |
| **Input** | Email/SĐT + Mật khẩu, hoặc OAuth token |
| **Output** | JWT access token + refresh token, thông tin user |
| **Xử lý** | Tìm user → Verify password (bcrypt) → Tạo JWT → Merge giỏ hàng |

**Ràng buộc bảo mật:**
- Khóa tài khoản sau 5 lần sai liên tiếp (mở lại sau 30 phút)
- JWT access token hết hạn sau 1 giờ
- Refresh token hết hạn sau 30 ngày
- Hỗ trợ đăng nhập Google OAuth 2.0 và Facebook Login

#### FR-03: Quản lý thông tin cá nhân
- **FR-03a**: Xem và cập nhật profile (họ tên, ngày sinh, giới tính, avatar)
- **FR-03b**: Quản lý địa chỉ giao hàng (CRUD, tối đa 5 địa chỉ, 1 mặc định)
- **FR-03c**: Đổi mật khẩu (yêu cầu nhập mật khẩu cũ)
- **FR-03d**: Quên mật khẩu (gửi link reset qua email, hết hạn sau 15 phút)

---

### 3.2 MODULE SẢN PHẨM & TÌM KIẾM

#### FR-04: Quản lý danh mục sản phẩm
| Thuộc tính | Mô tả |
|-----------|-------|
| **Mã** | FR-04 |
| **Mức ưu tiên** | Cao |
| **Mô tả** | Hệ thống tổ chức sản phẩm theo cây danh mục đa cấp |

**Yêu cầu:**
- Danh mục tối thiểu 2 cấp (cấp cha → cấp con)
- Mỗi danh mục có: tên, slug URL, icon, ảnh, mô tả, thứ tự hiển thị
- Hỗ trợ ẩn/hiện danh mục không ảnh hưởng sản phẩm
- Breadcrumb tự động theo cây danh mục

**Danh mục cấp 1 tối thiểu:**
Laptop | PC Gaming | PC Văn phòng | Linh kiện | Màn hình | Phím chuột | Tản nhiệt | Loa tai nghe | Camera an ninh | TB Văn phòng | TB Siêu thị | Mạng & Lưu trữ | Console & Game | Hàng cũ

#### FR-05: Tìm kiếm sản phẩm
| Thuộc tính | Mô tả |
|-----------|-------|
| **Mã** | FR-05 |
| **Mức ưu tiên** | Cao |
| **Input** | Từ khóa tìm kiếm |
| **Output** | Danh sách sản phẩm phù hợp |

**Yêu cầu:**
- Full-text search theo: tên sản phẩm, SKU, tên thương hiệu, thông số kỹ thuật
- Tìm kiếm không phân biệt dấu tiếng Việt (unaccent)
- Autocomplete: gợi ý tối đa 10 sản phẩm khi gõ từ 2 ký tự trở lên
- Phản hồi autocomplete trong < 300ms
- Lưu lịch sử tìm kiếm (tối đa 10 từ khóa gần nhất)
- Gợi ý "Có thể bạn muốn tìm" khi không có kết quả

#### FR-06: Hiển thị danh sách sản phẩm
**Yêu cầu lọc (Filter):**
- Thương hiệu (multi-select)
- Khoảng giá (range slider: min–max)
- Thông số kỹ thuật (CPU, RAM, màn hình, pin... theo danh mục)
- Tình trạng: Còn hàng / Hàng mới / Đang giảm giá
- Lọc kết hợp nhiều tiêu chí cùng lúc

**Yêu cầu sắp xếp (Sort):**
- Mặc định (nổi bật)
- Giá tăng dần / Giảm dần
- Mới nhất
- Bán chạy nhất
- Đánh giá cao nhất

**Yêu cầu phân trang:**
- Tối đa 24 sản phẩm/trang
- Hỗ trợ URL parameter: `?page=2&sort=price-asc&brand=asus`

#### FR-07: Xem chi tiết sản phẩm
**Yêu cầu:**
- Gallery ảnh: tối thiểu 5 ảnh, hỗ trợ zoom
- Hiển thị: tên, giá bán, giá gốc, % giảm, tình trạng kho
- Bảng thông số kỹ thuật đầy đủ (key-value)
- Chính sách bảo hành (X tháng)
- Tab: Mô tả | Thông số | Đánh giá
- Sản phẩm liên quan (tối đa 8 sản phẩm cùng danh mục)
- Ghi nhận lượt xem (+1 mỗi lần user truy cập)
- Nút "Thêm vào giỏ" và "Mua ngay" (disabled khi hết hàng)

---

### 3.3 MODULE BUILD PC

#### FR-08: Xây dựng cấu hình PC
| Thuộc tính | Mô tả |
|-----------|-------|
| **Mã** | FR-08 |
| **Mức ưu tiên** | Cao (tính năng đặc trưng) |
| **Mô tả** | Cho phép người dùng tự chọn linh kiện lắp ráp máy tính |

**Danh sách 23 loại linh kiện có thể chọn (từ hacom.vn thực tế):**

| STT | Loại linh kiện | Bắt buộc |
|-----|---------------|---------|
| 1 | CPU — Bộ vi xử lý | ✅ |
| 2 | Mainboard — Bo mạch chủ | ✅ |
| 3 | RAM | ✅ |
| 4 | HDD | ❌ |
| 5 | SSD | ✅ |
| 6 | VGA — Card màn hình | ❌ |
| 7 | VGA Like New | ❌ |
| 8 | Nguồn PSU | ✅ |
| 9 | Vỏ Case | ✅ |
| 10 | Màn hình | ❌ |
| 11 | Bộ bàn phím + chuột | ❌ |
| 12 | Bàn phím | ❌ |
| 13 | Chuột | ❌ |
| 14 | Tai nghe | ❌ |
| 15 | Loa | ❌ |
| 16 | Ghế Gaming | ❌ |
| 17 | Quạt làm mát | ❌ |
| 18 | Tản nhiệt khí | ❌ |
| 19 | Tản nhiệt nước AIO | ❌ |
| 20 | Tản nhiệt nước Custom | ❌ |
| 21 | Thiết bị mạng | ❌ |
| 22 | Windows bản quyền | ❌ |
| 23 | Phần mềm Antivirus | ❌ |

**Yêu cầu nghiệp vụ:**
- Lọc sản phẩm theo showroom đã chọn (kiểm tra tồn kho)
- Cảnh báo khi CPU và Mainboard không tương thích socket
- Cảnh báo khi PSU không đủ công suất cho cấu hình
- Tính tổng giá realtime khi thay đổi linh kiện
- Áp dụng tự động chính sách khuyến mãi Build PC:
  - Giảm ≤ 50% CPU khi có đủ: Main + SSD + RAM + Case + Nguồn + VGA ≥ RX6500XT
  - Giảm ≤ 30% CPU khi có đủ: Main + SSD + RAM + Case + Nguồn (không cần VGA mạnh)
  - Tặng tiền mặt thêm theo tổng giá trị bộ (tối đa 30 triệu)
- Cho phép: Lưu cấu hình | Xuất Excel | Tải ảnh PNG | In | Thêm vào giỏ
- Mẫu cấu hình có sẵn: CẤU HÌNH 1 đến CẤU HÌNH 5

---

### 3.4 MODULE GIỎ HÀNG

#### FR-09: Quản lý giỏ hàng
| Mã | FR-09 | Mức ưu tiên | Cao |
|----|-------|-------------|-----|

**Yêu cầu:**

| STT | Yêu cầu | Điều kiện |
|-----|---------|-----------|
| 1 | Thêm sản phẩm vào giỏ | Sản phẩm còn hàng |
| 2 | Thay đổi số lượng | 1 ≤ qty ≤ tồn kho |
| 3 | Xóa từng sản phẩm | — |
| 4 | Xóa toàn bộ giỏ hàng | Xác nhận trước khi xóa |
| 5 | Tính tổng tiền realtime | — |
| 6 | Hiển thị số lượng SP trên icon | Cập nhật realtime |
| 7 | Giỏ hàng không cần đăng nhập | Lưu vào session/localStorage |
| 8 | Merge giỏ hàng khi đăng nhập | Ưu tiên giữ sản phẩm từ cả hai |
| 9 | Lưu giỏ hàng 30 ngày | Session hoặc DB |
| 10 | Hiển thị giá + ảnh + tên SP | Snapshot tại thời điểm thêm |

---

### 3.5 MODULE ĐẶT HÀNG & THANH TOÁN

#### FR-10: Quy trình đặt hàng
| Mã | FR-10 | Mức ưu tiên | Cao |
|----|-------|-------------|-----|

**Bước 1 — Địa chỉ giao hàng:**
- Chọn từ danh sách địa chỉ đã lưu hoặc nhập mới
- Chọn phương thức: Giao tận nơi (toàn quốc) / Nhận tại showroom

**Bước 2 — Vận chuyển:**

| Phương thức | Thời gian | Phí | Điều kiện miễn phí |
|-------------|-----------|-----|-------------------|
| Tiêu chuẩn | 2–3 ngày | 30,000đ | Đơn ≥ 5,000,000đ |
| Nhanh | 1–2 ngày | 50,000đ | Đơn ≥ 10,000,000đ |
| Hỏa tốc | 4 giờ (nội thành) | 80,000đ | — |
| Nhận tại showroom | — | Miễn phí | — |

**Bước 3 — Thanh toán:**

| Phương thức | Xử lý | Thời gian |
|-------------|-------|-----------|
| COD | Đồng bộ | Khi giao hàng |
| Chuyển khoản ngân hàng | Thủ công | 1–24 giờ |
| VNPay | Redirect | Tức thì |
| Momo | Redirect | Tức thì |
| ZaloPay | Redirect | Tức thì |
| Trả góp 0% | Manual | 1–3 ngày |

**Bước 4 — Voucher:** Nhập mã tùy chọn, kiểm tra trực tiếp

**Bước 5 — Xác nhận:**
- Tóm tắt: sản phẩm, địa chỉ, phí ship, giảm giá, **tổng cộng**
- Tạo mã đơn hàng: `HC-YYYY-NNNNNN`
- Gửi email xác nhận ngay sau khi đặt

**Ràng buộc:**
- Số lượng mua ≤ tồn kho hiện tại
- Đơn hàng tối thiểu: không giới hạn (cho cá nhân)
- Tự động hủy đơn COD chưa xác nhận sau 48 giờ

#### FR-11: Thanh toán trả góp
- Điều kiện: giá trị đơn ≥ 3,000,000đ
- Đối tác: HomeCredit, FE Credit, HSBC, Shinhan, Techcombank
- Kỳ hạn: 6, 12, 18, 24 tháng
- Lãi suất: 0% (theo chương trình khuyến mãi)
- Quy trình: Chọn gói → Điền thông tin → Nhân viên liên hệ trong 24h

---

### 3.6 MODULE QUẢN LÝ ĐƠN HÀNG

#### FR-12: Tra cứu đơn hàng (không cần đăng nhập)
- Input: Mã đơn hàng + SĐT đặt hàng
- Output: Trạng thái đơn, sản phẩm, địa chỉ, timeline, tracking

#### FR-13: Lịch sử đơn hàng (cần đăng nhập)
- Danh sách tất cả đơn, lọc theo trạng thái
- Xem chi tiết từng đơn

#### FR-14: Trạng thái đơn hàng

```
pending → confirmed → processing → shipping → delivered → completed
   ↑_________________↓ (cancelled)
```

| Trạng thái | Mô tả | Ai thay đổi |
|-----------|-------|-------------|
| pending | Chờ xác nhận | Hệ thống tự tạo |
| confirmed | Đã xác nhận | Staff |
| processing | Đang đóng gói | Staff |
| shipping | Đang giao hàng | Staff / Đơn vị VC |
| delivered | Đã giao | Đơn vị VC / Staff |
| completed | Hoàn thành | Khách xác nhận / Tự động sau 7 ngày |
| cancelled | Đã hủy | Khách (trước confirmed) / Staff |
| refunded | Đã hoàn tiền | Admin |

#### FR-15: Hủy đơn hàng
- Chỉ cho phép hủy khi status = `pending`
- Yêu cầu chọn lý do hủy
- Hoàn lại tồn kho tự động
- Hoàn tiền nếu đã thanh toán online (3–7 ngày làm việc)

#### FR-16: Yêu cầu đổi/trả hàng
- Thời hạn: trong 15 ngày kể từ ngày giao thành công
- Lý do hợp lệ: Lỗi sản phẩm / Sai hàng / Hàng bị hư hỏng khi giao
- Yêu cầu upload ảnh/video minh chứng
- Staff xem xét trong 24 giờ

#### FR-17: In hóa đơn điện tử
- Xuất PDF hóa đơn điện tử
- Hỗ trợ hóa đơn cá nhân và doanh nghiệp (nhập MST)
- Gửi hóa đơn qua email

---

### 3.7 MODULE BẢO HÀNH & DỊCH VỤ

#### FR-18: Tra cứu bảo hành
- Không yêu cầu đăng nhập
- Tìm theo: số serial máy, mã đơn hàng
- Hiển thị: tên SP, ngày mua, hạn bảo hành, trạng thái
- Hệ thống có 2 API riêng: trước 2025 và từ 2025 (theo thực tế hacom.vn)

#### FR-19: Trạng thái bảo hành

| Trạng thái | Mô tả |
|-----------|-------|
| active | Còn trong hạn bảo hành |
| expired | Hết hạn bảo hành |
| voided | Mất bảo hành (tự ý sửa, bị va đập...) |
| in_service | Đang trong quá trình sửa chữa |

#### FR-20: Yêu cầu sửa chữa

**Vòng đời phiếu dịch vụ:**
```
received → diagnosing → repairing → (waiting_part →) done → returned
```

**Yêu cầu:**
- Tạo phiếu online hoặc trực tiếp tại showroom
- Chọn showroom tiếp nhận và đặt lịch hẹn
- Upload ảnh/video mô tả lỗi (tối đa 5 file, mỗi file ≤ 10MB)
- Kỹ thuật viên cập nhật trạng thái và ghi chú
- Thông báo tự động qua SMS/Email khi đổi trạng thái
- Báo giá trước khi sửa (nếu ngoài bảo hành, chờ khách duyệt)

---

### 3.8 MODULE ĐÁNH GIÁ SẢN PHẨM

#### FR-21: Review sản phẩm

**Yêu cầu:**
- Chỉ người đã mua sản phẩm (order_item liên kết) mới được đánh giá
- Rating: 1–5 sao (bắt buộc)
- Tiêu đề + nội dung (tùy chọn, tối đa 1000 ký tự)
- Upload ảnh thực tế (tùy chọn, tối đa 5 ảnh)
- 1 user chỉ đánh giá 1 lần/sản phẩm đã mua
- Đánh dấu "Hữu ích" trên review của người khác
- Hiển thị "Đã mua hàng" (verified badge)
- Tự động cập nhật điểm rating trung bình sản phẩm

**Moderation:**
- Review hiển thị ngay (auto-approve)
- Admin có thể ẩn review vi phạm chính sách

---

### 3.9 MODULE KHUYẾN MÃI & VOUCHER

#### FR-22: Chương trình khuyến mãi (Promotion)
- Loại giảm giá: theo % hoặc số tiền cố định
- Phạm vi: toàn bộ / danh mục / thương hiệu / sản phẩm cụ thể
- Có thời gian bắt đầu và kết thúc
- Tự động áp dụng khi sản phẩm thuộc chương trình KM
- Hiển thị nhãn "SALE", đồng hồ đếm ngược

**Các loại khuyến mãi thực tế trên hacom.vn:**
- Khuyến mãi laptop / PC / linh kiện / phụ kiện
- Ưu đãi học sinh sinh viên
- Khuyến mãi theo thương hiệu (ASUS, MSI, Gigabyte...)
- Chương trình Build PC (giảm CPU theo bộ)
- Give Away (quay số trúng thưởng)

#### FR-23: Voucher / Coupon
- Tạo mã thủ công hoặc tự động (random)
- Loại: % giảm | Giảm tiền cố định | Free ship
- Ràng buộc: đơn tối thiểu, giảm tối đa, số lần dùng, per-user limit
- Thời hạn hiệu lực
- Kiểm tra realtime khi nhập mã
- Ghi nhận lịch sử sử dụng

---

### 3.10 MODULE TƯƠNG TÁC

#### FR-24: Wishlist (Danh sách yêu thích)
- Thêm/xóa sản phẩm yêu thích (icon tim)
- Xem danh sách wishlist
- Chuyển từ wishlist sang giỏ hàng
- Nhận thông báo khi sản phẩm yêu thích giảm giá

#### FR-25: Sản phẩm đã xem
- Ghi nhận tự động khi user vào trang chi tiết
- Hiển thị tối đa 20 sản phẩm gần nhất
- Khả dụng cả khi không đăng nhập (localStorage)

#### FR-26: Thông báo (Notifications)
- Thông báo trong app: đơn hàng, bảo hành, khuyến mãi
- Email: xác nhận đơn, trạng thái đơn, nhắc đánh giá
- SMS: xác nhận đặt hàng, giao hàng

---

### 3.11 MODULE NỘI DUNG

#### FR-27: Tin tức / Blog
- Danh mục: Tin khuyến mãi | Review SP | Hướng dẫn | Công nghệ | Sự kiện
- CRUD bài viết (Admin)
- Liên kết bài viết với sản phẩm đề cập
- Tìm kiếm bài viết
- Đếm lượt xem

#### FR-28: Banner & Slider
- Quản lý banner trang chủ (CRUD)
- Cấu hình vị trí: home_slider, sidebar, popup
- Thời gian hiển thị (start_date, end_date)
- Link đến trang đích

#### FR-29: Hệ thống Showroom
- Danh sách 21 showroom thực tế (từ hacom.vn)
- Thông tin: địa chỉ, SĐT, email, giờ mở cửa
- Gallery ảnh thực tế showroom
- Tích hợp Google Maps
- Tìm showroom theo tỉnh/thành

---

### 3.12 MODULE QUẢN TRỊ (ADMIN)

#### FR-30: Quản lý sản phẩm
- CRUD đầy đủ: tên, danh mục, thương hiệu, giá, tồn kho, ảnh, thông số
- Ẩn/hiện sản phẩm
- Import hàng loạt qua file Excel
- Quản lý tồn kho theo showroom
- Lịch sử thay đổi giá

#### FR-31: Quản lý đơn hàng
- Xem toàn bộ đơn hàng, lọc theo trạng thái/ngày/showroom
- Xác nhận / Từ chối đơn hàng
- Cập nhật trạng thái và thêm mã tracking
- Ghi chú nội bộ (staff note)
- Xử lý hoàn tiền

#### FR-32: Báo cáo & Thống kê

| Báo cáo | Mô tả |
|---------|-------|
| Doanh thu | Theo ngày/tuần/tháng/năm, so sánh kỳ trước |
| Đơn hàng | Số lượng theo trạng thái, tỷ lệ hủy |
| Sản phẩm | Top bán chạy, tồn kho sắp hết |
| Khách hàng | Mới/quay lại, LTV, phân khúc |
| Khuyến mãi | Doanh thu theo chiến dịch |
| Showroom | So sánh hiệu quả theo chi nhánh |

---

## 4. YÊU CẦU PHI CHỨC NĂNG

### 4.1 Hiệu năng (Performance)

| Chỉ số | Yêu cầu |
|--------|---------|
| Thời gian tải trang chủ | < 3 giây (3G) |
| Thời gian tải trang SP | < 2 giây |
| Thời gian autocomplete | < 300ms |
| Thời gian xử lý đặt hàng | < 5 giây |
| Concurrent users | ≥ 1,000 người đồng thời |
| Uptime | ≥ 99.5% / tháng |
| Throughput API | ≥ 500 requests/giây |

### 4.2 Bảo mật (Security)

| Yêu cầu | Mô tả |
|---------|-------|
| HTTPS | Toàn bộ website, TLS 1.2+ |
| Password hashing | bcrypt, cost factor ≥ 12 |
| JWT | Access token 1h, Refresh 30 ngày |
| SQL Injection | Sử dụng parameterized queries |
| XSS | Sanitize input, Content Security Policy |
| CSRF | CSRF token cho mọi form POST |
| Rate limiting | API: 100 req/min/IP; Login: 5 lần sai → khóa |
| PCI DSS | Không lưu thông tin thẻ ngân hàng |
| GDPR/Luật BVNTD | Bảo mật thông tin khách hàng |

### 4.3 Khả năng sử dụng (Usability)

- Responsive design: hỗ trợ desktop (≥1200px), tablet (768–1199px), mobile (< 768px)
- Hỗ trợ trình duyệt: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Tiếng Việt đầy đủ (UI, thông báo lỗi, email)
- Tìm kiếm không phân biệt dấu (unaccent)
- Loading skeleton khi tải dữ liệu
- Thông báo lỗi rõ ràng, thân thiện người dùng

### 4.4 Khả năng mở rộng (Scalability)

- Kiến trúc hỗ trợ horizontal scaling
- Database connection pooling
- Cache layer (Redis) cho sản phẩm phổ biến, session
- CDN cho ảnh sản phẩm và static assets
- API phân trang cho mọi endpoint danh sách

### 4.5 Khả năng bảo trì (Maintainability)

- Code tuân theo chuẩn (ESLint/PSR/PEP8...)
- Unit test coverage ≥ 70%
- API documentation (Swagger/OpenAPI)
- Logging đầy đủ (request, error, business events)
- Database migration có version control

### 4.6 Tích hợp bên thứ 3

| Dịch vụ | Mục đích | Fallback |
|---------|---------|---------|
| VNPay | Thanh toán online | — |
| Momo | Thanh toán ví | — |
| ZaloPay | Thanh toán ví | — |
| SMTP (SendGrid/SES) | Gửi email | Queue retry 3 lần |
| SMS (VIETTEL/VNPT) | Gửi OTP, thông báo | Fallback qua email |
| Google Maps JavaScript API | Hiển thị showroom | Địa chỉ text |
| Google OAuth 2.0 | Đăng nhập | — |
| Facebook Login | Đăng nhập | — |
| GHN / GHTK | Vận chuyển, tracking | — |

---

## 5. RÀNG BUỘC THIẾT KẾ

### 5.1 Công nghệ đề xuất

| Tầng | Công nghệ |
|------|-----------|
| Frontend | React.js / Next.js |
| Backend | Node.js (Express) hoặc Laravel (PHP) |
| Database | PostgreSQL 15+ |
| Cache | Redis |
| Storage | AWS S3 hoặc MinIO (ảnh sản phẩm) |
| CDN | Cloudflare |
| Container | Docker + Docker Compose |

### 5.2 Ràng buộc nghiệp vụ

- Giá sản phẩm hiển thị đã bao gồm VAT 10%
- Đơn vị tiền tệ: VNĐ (Vietnam Dong)
- Múi giờ hệ thống: UTC+7 (Asia/Ho_Chi_Minh)
- Số lượng tối thiểu mua: 1
- Hủy đơn chỉ khi chưa xác nhận (status = pending)
- Đổi/trả trong 15 ngày theo chính sách hacom.vn

---

## 6. GIAO DIỆN HỆ THỐNG

### 6.1 Giao diện người dùng (UI)

**Trang chủ:**
- Hero banner slider (khuyến mãi nổi bật)
- Danh mục sản phẩm nhanh (grid icon)
- Sản phẩm nổi bật / Bán chạy / Hàng mới
- Banner khuyến mãi theo thương hiệu
- Hệ thống showroom

**Header:**
- Logo | Tìm kiếm (nổi bật) | Tài khoản | Yêu thích | Giỏ hàng
- Menu danh mục mega menu đa cấp
- Thanh top: hotline | Build PC | Tra cứu đơn | Tra cứu bảo hành

**Footer:**
- Thông tin công ty | Hỗ trợ | Chính sách | Mạng xã hội
- Phương thức thanh toán (logo VNPay, Momo...)
- Form đăng ký nhận email khuyến mãi

### 6.2 Giao diện Admin Panel

- Dashboard: doanh thu, đơn hàng, khách hàng (biểu đồ)
- Sidebar menu: Sản phẩm | Đơn hàng | Khuyến mãi | Bảo hành | Nội dung | Báo cáo | Cài đặt
- Bảng dữ liệu có phân trang, sắp xếp, lọc, tìm kiếm
- Form CRUD responsive

### 6.3 Giao diện API (REST)

- Base URL: `https://api.hacom-clone.vn/v1`
- Authentication: Bearer JWT token
- Content-Type: `application/json`
- Response format:
```json
{
  "success": true,
  "data": { ... },
  "message": "...",
  "pagination": { "page": 1, "limit": 24, "total": 120 }
}
```
- Error format:
```json
{
  "success": false,
  "error": {
    "code": "PRODUCT_NOT_FOUND",
    "message": "Sản phẩm không tồn tại"
  }
}
```

---

## PHỤ LỤC: MA TRẬN TRUY XUẤT YÊU CẦU

| Mã FR | Tên yêu cầu | Module | Use Case | Bảng DB | Mức ưu tiên |
|-------|------------|--------|---------|---------|-------------|
| FR-01 | Đăng ký | Tài khoản | UC-01 | users, user_tokens | Cao |
| FR-02 | Đăng nhập | Tài khoản | UC-02 | users, user_tokens | Cao |
| FR-03 | Quản lý profile | Tài khoản | UC-03 | users, user_addresses | Cao |
| FR-04 | Danh mục SP | Sản phẩm | UC-04 | categories | Cao |
| FR-05 | Tìm kiếm | Sản phẩm | UC-05 | products | Cao |
| FR-06 | Danh sách SP | Sản phẩm | UC-04 | products, brands | Cao |
| FR-07 | Chi tiết SP | Sản phẩm | UC-06 | products, product_images, product_attributes | Cao |
| FR-08 | Build PC | Build PC | UC-07, UC-08 | pc_builds, pc_build_items, pc_components | Cao |
| FR-09 | Giỏ hàng | Giỏ hàng | UC-09 | carts, cart_items | Cao |
| FR-10 | Đặt hàng | Đơn hàng | UC-10 | orders, order_items | Cao |
| FR-11 | Trả góp | Thanh toán | UC-11 | installment_plans, order_installments | TB |
| FR-12 | Tra cứu ĐH | Đơn hàng | UC-12 | orders | Cao |
| FR-13 | Lịch sử ĐH | Đơn hàng | UC-12a | orders, order_items | Cao |
| FR-14 | Trạng thái ĐH | Đơn hàng | UC-27 | orders | Cao |
| FR-15 | Hủy đơn | Đơn hàng | UC-13 | orders | Cao |
| FR-16 | Đổi/trả | Đơn hàng | UC-14 | orders | Cao |
| FR-17 | Hóa đơn điện tử | Đơn hàng | UC-15 | orders, order_items | TB |
| FR-18 | Tra cứu BH | Bảo hành | UC-16 | warranties | Cao |
| FR-19 | Trạng thái BH | Bảo hành | — | warranties | TB |
| FR-20 | Yêu cầu SC | Bảo hành | UC-17, UC-30 | service_requests | TB |
| FR-21 | Đánh giá SP | Review | UC-18 | reviews, review_images | TB |
| FR-22 | Khuyến mãi | KM | UC-28 | promotions | Cao |
| FR-23 | Voucher | KM | UC-19, UC-29 | vouchers, voucher_usage | Cao |
| FR-24 | Wishlist | Tương tác | UC-20 | wishlists | Thấp |
| FR-25 | SP đã xem | Tương tác | UC-21 | product_views | Thấp |
| FR-26 | Thông báo | Tương tác | — | notifications | TB |
| FR-27 | Tin tức/Blog | Nội dung | UC-22 | blog_posts, blog_categories | Thấp |
| FR-28 | Banner | Nội dung | — | banners | TB |
| FR-29 | Showroom | Nội dung | UC-25 | stores | TB |
| FR-30 | Quản lý SP | Admin | UC-26 | products | Cao |
| FR-31 | Quản lý ĐH | Admin | UC-27 | orders | Cao |
| FR-32 | Báo cáo | Admin | UC-31 | (views/queries) | TB |

---

*Tài liệu SRS — Phiên bản 1.0 — Luận án tốt nghiệp — 02/06/2026*
*Phân tích từ thực tế: https://hacom.vn*
