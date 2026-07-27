# ✅ CHECKLIST RESOLVE NHẬN XÉT KLTN - NHÓM 10

> **Mục tiêu:** Hoàn thiện báo cáo theo nhận xét của giáo viên  
> **Chiến lược:** Làm từ DỄ → TRUNG BÌNH → KHÓ để tạo động lực  
> **Cập nhật cuối:** 2026-07-27 (Phase 4 — Review tổng thể và đồng bộ, plan `plans/260726-2322-bao-cao-cac-muc-chua-hoan-thanh`)  
> **Tiến độ:** 13/13 mục có trạng thái cuối cùng rõ ràng — 9 DONE thật, 2 DONE có ngoại lệ đã ghi nhận rủi ro (chấp nhận theo quyết định người dùng 2026-07-27), 1 một phần, 1 chưa làm

---

## 📊 TỔNG QUAN TIẾN ĐỘ (verify trực tiếp bằng grep/đọc file, Phase 4)

- [x] **9/13 mục DONE hoàn toàn** (1, 2, 3, 4, 5, 6, 7, 8, 12)
- [x] **2/13 mục DONE có ngoại lệ đã chấp nhận rủi ro** (10 — 6/15 câu khảo sát số liệu ước lượng; 13 — kết quả test là placeholder). Cả 2 mục **không có disclaimer/nhãn cảnh báo trong báo cáo** dù `PROGRESS_REPORT.md` bản cũ từng ghi nhầm là đã có — Phase 4 verify trực tiếp phát hiện sai lệch này, đã hỏi lại người dùng 2026-07-27, quyết định: giữ nguyên không thêm disclaimer, xuất bản `.docx` như hiện trạng.
- [ ] **1/13 một phần** (9 — đánh số Chương 4 xong khung nhưng Danh mục hình vẽ/bảng biểu chưa tạo được, cần thao tác tay trong Word)
- [ ] **1/13 chưa làm** (11 — ảnh chụp màn hình hệ thống thật, 0%)

**Phân theo độ khó:**
- [x] 🟢 Cấp độ DỄ: 4/4 mục DONE
- [x] 🟡 Cấp độ TRUNG BÌNH: 5/6 DONE, 1 một phần (mục 9)
- [ ] 🔴 Cấp độ KHÓ: 1/3 DONE (mục 12), 2/3 DONE có ngoại lệ chấp nhận rủi ro (mục 13) hoặc chưa làm (mục 11)

---

## � CẤP ĐỘ 1: DỄ - Sửa lỗi trình bày và văn bản (1-2 ngày)

> **Bắt đầu từ đây!** Các mục này chỉ cần sửa text, không cần code hay vẽ diagram phức tạp.

### 1. Sửa các lỗi trình bày đơn giản
**Độ khó:** ⭐ (Rất dễ)  
**Thời gian:** 2-3 giờ  
**Người thực hiện:** _________

#### Checklist chi tiết:

**A. Thống nhất thời hạn đổi/trả (15 phút):** ✅ ĐÃ XONG (verify: "15 ngày" nhất quán ở 1.8.4, 1.11.6, 2.2.1.5)
- [x] Tìm tất cả chỗ đề cập "đổi/trả hàng" (Ctrl+F)
- [x] Chọn **15 ngày** (giữ nguyên mục 1.8.4, 1.11.6)
- [x] Sửa Activity Diagram 2.2.1.12 từ "7 ngày" → **"15 ngày"**
- [x] Sửa mục D.3 (nếu có) từ "7 ngày" → **"15 ngày"**

**B. Sửa HACOM → Hanoicomputer (15 phút):** ✅ ĐÃ XONG (verify: grep `HACOM|hacom\.vn` = 0 kết quả)
- [x] Tìm tất cả "HACOM" hoặc "hacom.vn" (Ctrl+F)
- [x] Sửa thành **"Hanoicomputer"** hoặc **"hanoicomputer.vn"**
- [x] ~~Sửa "21 showroom" thành "3 showroom"~~ — **QUYẾT ĐỊNH (Validation Session 1, /ck-plan validate):** "21 showroom" là số liệu ĐÚNG, giữ nguyên, không sửa. Đề xuất "3 showroom" ở dòng này đã bị bác bỏ.
- [x] Cập nhật Tài liệu tham khảo

**C. Sửa tên người phỏng vấn (10 phút):** ✅ ĐÃ XONG (verify: Bảng 1.3/1.6 dùng tên đầy đủ nhất quán "Bùi Văn Sơn"/"Trần Đức Sơn", không còn viết tắt)
- [x] Kiểm tra Bảng 1.3: "Bùi Văn Sơn" và "Trần Đức Sơn"
- [x] Kiểm tra Bảng 1.6: "Bùi Văn S" và "Lê Văn M"
- [x] Thống nhất: Dùng tên đầy đủ hoặc tên viết tắt nhất quán

**D. Sửa câu kết luận (5 phút):** ✅ ĐÃ XONG (sửa dòng 259, mục 1.3.1)
- [x] Tìm câu "đáp ứng đầy đủ các yêu cầu chức năng và phi chức năng"
- [x] Sửa thành: "đáp ứng **phần lớn** các yêu cầu chức năng cốt lõi"

**E. Bỏ Blockchain và NFT trong Roadmap (5 phút):** ✅ ĐÃ XONG (verify: grep `Blockchain|NFT` = 0 kết quả)
- [x] Tìm phần Roadmap dài hạn
- [x] Xóa/Comment out phần Blockchain và NFT
- [x] Giữ lại các phần liên quan đến website bán máy tính

---

### 2. Sửa mục 1.4.3 "Giới hạn của đề tài"
**Độ khó:** ⭐ (Rất dễ - Copy/Paste)  
**Thời gian:** 30 phút  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Mở mục 1.4.3 hiện tại
- [ ] **Copy phần B từ Kết luận:** "Các chức năng chưa triển khai"
  - [ ] Tóm tắt thành 5-7 điểm chính
  - [ ] Paste vào mục 1.4.3
- [ ] **Copy phần C từ Kết luận:** "Giới hạn kỹ thuật chi tiết"
  - [ ] Tóm tắt thành 5-7 điểm chính
  - [ ] Paste vào mục 1.4.3
- [ ] Giữ mục 1.4.3 ngắn gọn (1-2 trang)

---

### 3. Gộp phần trùng lặp ở Kết luận
**Độ khó:** ⭐ (Rất dễ)  
**Thời gian:** 20 phút  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Tìm phần "Hạn chế" trong Kết luận
- [ ] Tìm phần "Giới hạn kỹ thuật chi tiết"
- [ ] So sánh 2 phần → Xác định nội dung trùng (khoảng 80%)
- [ ] **Gộp thành 1 phần:** "Hạn chế và giới hạn của đề tài"
- [ ] Xóa phần trùng lặp
- [ ] Sắp xếp lại thành các nhóm logic

---

### 4. Bổ sung Tài liệu tham khảo
**Độ khó:** ⭐⭐ (Dễ - Tìm kiếm online)  
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27)

#### Checklist chi tiết:
- [x] Hiện tại: 3 mục, toàn website
- [x] **Thêm sách về Spring Boot:** "Spring Boot in Action" - Craig Walls (2022, 2nd ed.)
- [x] **Thêm sách về CSDL:** "Database System Concepts" - Silberschatz (2020, 7th ed.)
- [x] **Thêm sách về UML:** "UML Distilled" - Martin Fowler (2003, 3rd ed.)
- [x] Đánh số tài liệu: [1] đến [10]
- [x] Format theo chuẩn: Tác giả, Năm, Tên sách, NXB (10 mục, xem cuối báo cáo)
- [ ] Sách React tiếng Việt/quốc tế — chưa thêm riêng (React Official Docs [8] đã đủ tính là tài liệu kỹ thuật chính thức)

---

## 🟡 CẤP ĐỘ 2: TRUNG BÌNH - Sửa nội dung kỹ thuật (2-3 ngày)

> Các mục này cần hiểu biết về hệ thống và có thể cần sửa file/diagram.

### 5. Bổ sung tác nhân Staff vào Use Case
**Độ khó:** ⭐⭐ (Dễ - Sửa text + vẽ lại diagram đơn giản)  
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27; PNG render xong 2026-07-27 sau khi cài GraphViz)

#### Checklist chi tiết:
- [x] **Bước 1: Sửa mục 2.1.3.1** — "4 tác nhân" → "5 tác nhân", thêm mục "4. Nhân viên (Staff)" với đủ 5 chức năng
- [x] **Bước 2: Sửa source diagram** — đã thêm actor Staff + quan hệ vào `usecases/00_UseCase_TongQuat.puml`
- [x] **Bước 3: Render PNG và thay ảnh trong báo cáo** — GraphViz đã cài, render bằng `npx node-plantuml generate -p -C UTF-8 usecases/00_UseCase_TongQuat.puml -o usecases/png/00_UC_TongQuat.png` (cờ `-C UTF-8` bắt buộc, thiếu sẽ ra chữ tiếng Việt lỗi mojibake). Đã copy đè lên `bao-cao/images/media/image7.png` (ảnh dùng trong báo cáo tại mục 2.1.3.3).

**Công cụ:** PlantUML + GraphViz (đã cài `winget install Graphviz.Graphviz`)

---

### 6. Kiểm tra và sửa UC02, UC14, UC27
**Độ khó:** ⭐⭐ (Dễ - Đọc và sửa text)  
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27)

#### Checklist chi tiết:
- [x] **UC02:** không có đặc tả (đã bị xóa cùng nội dung sai "Quản lý sản phẩm (Admin)" ở lần sửa trước) → đã viết bổ sung đặc tả đúng "Đăng nhập", tác nhân "Guest, Customer, Admin", khớp Bảng 2.1
- [x] **UC14:** verify — đã đúng "Theo dõi đơn hàng", tác nhân Customer, khớp Bảng 2.1 (không cần sửa)
- [x] **UC27:** verify — đã đúng "Xem báo cáo thống kê", tác nhân Admin, khớp Bảng 2.1 (không cần sửa)
- [x] Đối chiếu Bảng 2.1: cả 3 UC nay đã khớp

---

### 7. Rà soát Bảng 1.10 (Ánh xạ yêu cầu)
**Độ khó:** ⭐⭐ (Trung bình - Cần hiểu hệ thống)  
**Trạng thái:** ✅ ĐÃ VERIFY, KHÔNG CẦN SỬA (Phase 2, 2026-07-27)

#### Checklist chi tiết:
- [x] Đã đọc lại toàn bộ Bảng 1.10 (13 dòng) — Dashboard real-time, Thông báo push, Audit log, Template trả lời nhanh, Phân loại VIP đều đã ghi đúng "Tính năng mở rộng", không còn dòng nào ghi sai "Đã triển khai" cho tính năng chưa có bằng chứng.

**Nguyên tắc vàng:** Chỉ ghi "Đã triển khai" khi có ảnh hoặc code chứng minh!

---

### 8. Sửa Schema CSDL (Mục 3.1.2.4)
**Độ khó:** ⭐⭐⭐ (Trung bình - Cần kiến thức CSDL)  
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 5, 2026-07-27)

#### Checklist chi tiết:

**A. Bỏ code SQL:** ✅ ĐÃ XONG — chuyển toàn bộ 34 `CREATE TABLE` (2 khu vực: mục 3.1.1.3 và 3.1.2) thành bảng Markdown (Cột | Kiểu dữ liệu & Ràng buộc | Mô tả), giữ nguyên constraint và index dạng chú thích ngắn gọn. Verify: grep `CREATE TABLE` = 0 kết quả.

**B. Hợp nhất schema trùng:** ✅ ĐÃ XONG — phát hiện 3 bảng bị định nghĩa trùng 2 lần với nội dung khác nhau: `user_tokens`, `warranties`, `notifications` (xuất hiện cả ở 3.1.1.3 và 3.1.2). Đã giữ lại bản đầy đủ hơn (ở mục 3.1.2, có thêm trường audit/tham chiếu), xóa bản trùng, ghi chú rõ trong báo cáo.

**C. Thống nhất kiểu dữ liệu:** ✅ ĐÃ XONG — kiểm tra code thật `KL-BE` (`entity/*.java` dùng `Long id` + `GenerationType.IDENTITY`), xác nhận ground truth là BIGINT/BIGSERIAL. Đã đổi 11 chỗ `SERIAL PRIMARY KEY` → `BIGSERIAL PRIMARY KEY` và 23 chỗ `INT REFERENCES` → `BIGINT REFERENCES` cho khớp code thực tế (không đổi các cột INT không phải ID/FK như `quantity`, `sort_order`).

**D. Sửa bảng `stores` trùng:** ✅ ĐÃ XONG TỪ TRƯỚC — verify lại: chỉ còn 1 định nghĩa duy nhất (STT 43), không còn trùng ở STT 25/44 như nhận xét GV.

**E. Thống nhất số bảng:** ✅ ĐÃ XONG — phát hiện lỗi thật: Module 6 (Orders & Payments) ghi sai "14" (bảng tổng quan) và "15 bảng" (heading), trong khi đếm thực tế theo STT 25-36 chỉ có **12 bảng**. Đã sửa cả 2 chỗ thành "12". Verify: tổng 12 module = 8+4+4+6+2+**12**+3+3+2+3+1+4 = **52**, khớp với "TỔNG CỘNG 52" và STT chạy 1→52 liên tục.

**F. Test script SQL:** ⏭️ Bỏ qua (Optional, không bắt buộc) — không có quyền chạy PostgreSQL thật trong phiên làm việc này để chụp ảnh minh chứng.

---

### 9. Đánh số mục lại cho đúng
**Độ khó:** ⭐⭐ (Dễ nhưng mất thời gian)  
**Trạng thái:** ⚠️ MỘT PHẦN — nội dung số mục 100% xong, chỉ còn Danh mục hình/bảng cần thao tác tay trong Word (Phase 4, 2026-07-27)

#### Checklist chi tiết:

**A. Sửa Chương 2:** ✅ ĐÃ XONG từ trước (verify lại: 2.1.1→2.1.2→2.1.3→2.1.3.1 liên tục, không nhảy số)

**B. Sửa Chương 3:** ✅ ĐÃ XONG — verify lại Phase 4: 3.1→3.1.1→3.1.1.1→3.1.1.2→3.1.1.3→3.1.2→3.2→... liên tục, không còn tham chiếu chéo nào trỏ về số cũ `3.1.3`/`3.1.2.4` (grep = 0 kết quả)

**C. Sửa Chương 4:** ✅ ĐÃ XONG (Phase 3, verify lại Phase 4) — `4.1→4.1.1→4.2→4.2.1→4.2.2→...→4.2.7` liên tục, không nhảy số. `4.2.1` "Kế hoạch kiểm thử" đã được viết ở Phase 3 (không còn để trống như ghi chú Phase 2 cũ).

**D. Thêm Danh mục hình và bảng:** ❌ VẪN CHƯA LÀM ĐƯỢC — xác nhận lại Phase 4: đây là giới hạn kỹ thuật thật, không phải bỏ sót. Word "Insert Table of Figures/Tables" cần mỗi ảnh/bảng có "Caption" (style riêng của Word); 63 ảnh trong báo cáo hiện dùng cú pháp Markdown `![alt](path)` thường, không có Caption, nên không thể tự động sinh danh mục qua pandoc/CLI. **Việc còn lại (thủ công trong Word sau khi mở bản `.docx` mới xuất):** (1) chọn từng ảnh/bảng → References → Insert Caption; (2) đặt con trỏ sau "Mục lục" hiện có → xóa danh sách tĩnh cũ → References → Table of Contents (tự sinh field thật, có số trang); (3) thêm 2 trang mới "Danh mục hình vẽ" / "Danh mục bảng biểu" → Insert Table of Figures / Insert Table of Tables.

---

### 10. Cải thiện phần Khảo sát (với biểu đồ)
**Độ khó:** ⭐⭐⭐ (Trung bình - Cần vẽ biểu đồ)  
**Thời gian:** 2-3 giờ  
**Người thực hiện:** _________

#### Checklist chi tiết:

**A. Chuẩn bị dữ liệu (30 phút):**
- [ ] Mở file kết quả khảo sát (Google Form export hoặc Excel)
- [ ] Tổng hợp kết quả 15/15 câu hỏi
- [ ] Tạo bảng tần suất cho mỗi câu

**B. Vẽ biểu đồ (1.5 giờ - 10 phút/câu):**
- [ ] Mở Excel hoặc Google Sheets
- [ ] Với mỗi câu hỏi:
  - [ ] Nhập dữ liệu vào sheet
  - [ ] Insert → Chart → Chọn loại phù hợp (Pie, Bar, Column)
  - [ ] Tùy chỉnh màu sắc, tiêu đề
  - [ ] Export thành PNG (300 DPI)
- [ ] Lưu ảnh vào `bao-cao/images/survey/`

**C. Thêm vào báo cáo (1 giờ):**
- [ ] Với mỗi câu hỏi, thêm:
  - [ ] Tiêu đề câu hỏi
  - [ ] Biểu đồ
  - [ ] Bảng số liệu
  - [ ] Phân tích 2-3 câu
- [ ] Bổ sung phần kết luận chung từ khảo sát

**D. (Optional) Minh chứng:**
- [ ] Thêm link Google Form vào Phụ lục
- [ ] Thêm file Excel dữ liệu thô vào Phụ lục

---

## 🔴 CẤP ĐỘ 3: KHÓ - Tạo nội dung mới phức tạp (4-5 ngày)

> Các mục này cần kỹ năng kỹ thuật cao và mất nhiều thời gian.

### 11. Bổ sung ảnh chụp màn hình hệ thống thật
**Độ khó:** ⭐⭐⭐⭐ (Khó - Cần hệ thống chạy được)  
**Thời gian:** 3-4 giờ (nếu hệ thống đã chạy)  
**Người thực hiện:** _________

#### Checklist chi tiết:

**A. Chuẩn bị (30 phút):**
- [ ] Đảm bảo hệ thống chạy được (frontend + backend)
- [ ] Có dữ liệu mẫu trong database
- [ ] Cài đặt công cụ chụp ảnh (Lightshot/Snagit)

**B. Chụp ảnh User (2 giờ):**
- [ ] **Trang chủ:**
  - [ ] Desktop (full screen, có sản phẩm, banner)
  - [ ] Mobile (responsive view)
- [ ] **Danh sách sản phẩm:**
  - [ ] Có bộ lọc đang hoạt động
  - [ ] Có sản phẩm hiển thị
  - [ ] Có phân trang
- [ ] **Chi tiết sản phẩm:**
  - [ ] Gallery hình ảnh
  - [ ] Thông số kỹ thuật
  - [ ] Nút Add to cart
  - [ ] Phần đánh giá (nếu có)
- [ ] **Giỏ hàng:**
  - [ ] Có sản phẩm trong giỏ
  - [ ] Tính tổng tiền
  - [ ] Nút cập nhật/xóa
- [ ] **Thanh toán:**
  - [ ] Form thông tin giao hàng
  - [ ] Chọn phương thức thanh toán
  - [ ] Tóm tắt đơn hàng
- [ ] **Build PC:** ⭐
  - [ ] Màn hình chính chọn danh mục
  - [ ] Chọn linh kiện cụ thể
  - [ ] Hiển thị tổng giá
  - [ ] Check compatibility (nếu có)
- [ ] **Đăng nhập/Đăng ký:**
  - [ ] Form đăng nhập
  - [ ] Form đăng ký
- [ ] **Profile:**
  - [ ] Thông tin cá nhân
  - [ ] Lịch sử đơn hàng

**C. Chụp ảnh Admin (1 giờ):**
- [ ] **Admin Dashboard:** ⭐
  - [ ] Biểu đồ doanh thu
  - [ ] Số liệu thống kê (tổng đơn, tổng user...)
  - [ ] Danh sách đơn hàng mới
- [ ] **Quản lý sản phẩm:**
  - [ ] Danh sách sản phẩm (có search, filter)
  - [ ] Form thêm/sửa sản phẩm
- [ ] **Quản lý đơn hàng:**
  - [ ] Danh sách đơn hàng
  - [ ] Chi tiết đơn hàng
  - [ ] Cập nhật trạng thái

**D. Chụp ảnh VNPay (30 phút):**
- [ ] Test thanh toán VNPay (môi trường test)
- [ ] Chụp trang VNPay
- [ ] Chụp kết quả thanh toán thành công

**E. Chỉnh sửa và thêm vào báo cáo (1 giờ):**
- [ ] Tạo folder `bao-cao/images/screenshots/`
- [ ] Đổi tên ảnh có ý nghĩa (home.png, product-list.png...)
- [ ] Resize nếu cần (1920x1080 hoặc 1366x768)
- [ ] Thêm vào mục 3.3.3 với mô tả ngắn
- [ ] Thêm vào Chương 4 với mô tả chi tiết chức năng
- [ ] Bổ sung link GitHub: `https://github.com/username/repo`
- [ ] Bổ sung URL demo (nếu có): `https://kinhduan.vercel.app`

**Tips:**
- Chụp vào giờ đẹp (không chụp lúc lỗi)
- Có thể dùng dữ liệu giả đẹp mắt
- Nên chụp cả luồng: Trang chủ → Sản phẩm → Giỏ hàng → Thanh toán

---

### 12. Bổ sung Class Diagram và Sequence Diagram
**Độ khó:** ⭐⭐⭐⭐⭐ (Rất khó - Cần kiến thức UML sâu)  
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 3, 2026-07-27)

- [x] **Class Diagram tổng quan** (mục 3.4.1) — 15 class chính (User, Category, Brand, Product, Cart/CartItem, Order/OrderItem, Review, Voucher, Store, Warranty, BlogPost, Banner...), attributes lấy thật từ entity `KL-BE`, quan hệ association/composition/self-ref khớp DB schema
- [x] **Sơ đồ kiến trúc Layered** (mục 3.4.2) — 5 tầng Presentation/API/Business/Data Access/Database, khớp câu "Layered Architecture" đã claim ở Kết luận
- [x] **3 Sequence Diagram** (mục 3.4.3) — Đặt hàng, Thanh toán VNPay, Build PC

Tất cả source `.puml` tại `class-sequence-diagram/`, render bằng `npx node-plantuml generate -p -C UTF-8 <file>.puml -o <file>.png` (GraphViz + cờ `-C UTF-8` bắt buộc để tránh mojibake tiếng Việt).

#### Checklist chi tiết:

**A. Học cơ bản về UML (30 phút - nếu chưa biết):**
- [ ] Xem video về Class Diagram (YouTube)
- [ ] Xem video về Sequence Diagram
- [ ] Tải template có sẵn để tham khảo

**B. Vẽ Class Diagram tổng quan (2 giờ):**
- [ ] **Xác định các class chính** (30 phút):
  - [ ] User, UserAddress, UserToken
  - [ ] Product, Category, Brand, ProductImage
  - [ ] Cart, CartItem
  - [ ] Order, OrderItem, OrderStatus
  - [ ] Review, ReviewImage
  - [ ] Voucher, Promotion
  - [ ] Store, Warranty
  - [ ] BlogPost, Banner
- [ ] **Vẽ từng class với attributes** (1 giờ):
  - [ ] Viết tên class (in đậm, viết hoa chữ đầu)
  - [ ] Liệt kê attributes (- private, + public)
  - [ ] Liệt kê methods (các hàm chính)
- [ ] **Vẽ relationships** (30 phút):
  - [ ] Association (---): User --- Order
  - [ ] Aggregation (◇---): Order ◇--- OrderItem
  - [ ] Composition (◆---): Product ◆--- ProductImage
  - [ ] Inheritance (△---): Admin △--- User
- [ ] Lưu file: `diagrams/ClassDiagram_Complete.png`

**C. Vẽ Sequence Diagram 1: Đặt hàng (1 giờ):**
- [ ] **Xác định actors và objects:**
  - Actor: Customer
  - Objects: ProductPage, Cart, CartService, Order, OrderService, Database
- [ ] **Vẽ timeline từ trên xuống:**
  1. Customer → ProductPage: Click "Add to Cart"
  2. ProductPage → CartService: addToCart(productId, quantity)
  3. CartService → Database: INSERT INTO cart_items
  4. Database → CartService: Success
  5. Customer → Cart: View cart
  6. Customer → Cart: Click "Checkout"
  7. Cart → OrderService: createOrder(cartItems)
  8. OrderService → Database: INSERT INTO orders
  9. OrderService → Database: UPDATE cart (clear)
  10. OrderService → Customer: Order confirmation
- [ ] Lưu file: `diagrams/SequenceDiagram_DatHang.png`

**D. Vẽ Sequence Diagram 2: Thanh toán VNPay (1 giờ):**
- [ ] **Xác định actors và objects:**
  - Actor: Customer
  - Objects: CheckoutPage, PaymentService, VNPay Gateway, Database
- [ ] **Vẽ flow:**
  1. Customer → CheckoutPage: Select VNPay payment
  2. CheckoutPage → PaymentService: createPayment(orderId, amount)
  3. PaymentService → VNPay: Create payment URL
  4. VNPay → PaymentService: Return payment URL
  5. PaymentService → Customer: Redirect to VNPay
  6. Customer → VNPay: Enter payment info
  7. VNPay → Customer: Confirm payment
  8. VNPay → PaymentService: Callback (IPN)
  9. PaymentService → Database: UPDATE order status
  10. PaymentService → Customer: Return URL (success)
- [ ] Lưu file: `diagrams/SequenceDiagram_VNPay.png`

**E. Vẽ Sequence Diagram 3: Build PC (1 giờ):**
- [ ] **Xác định flow:**
  1. Customer chọn category (CPU, RAM, VGA...)
  2. System hiển thị products
  3. Customer chọn product
  4. System check compatibility
  5. System tính tổng giá
  6. Customer lưu config
  7. System save to database
  8. Customer add to cart
- [ ] Lưu file: `diagrams/SequenceDiagram_BuildPC.png`

**F. Vẽ Sơ đồ kiến trúc Layered (30 phút):**
- [ ] Vẽ 5 layer từ trên xuống:
  1. **Presentation Layer:** React (UI Components)
  2. **API Layer:** Spring Boot REST API (Controllers)
  3. **Business Logic Layer:** Services (Business logic)
  4. **Data Access Layer:** JPA/Hibernate (Repositories)
  5. **Database Layer:** PostgreSQL
- [ ] Vẽ mũi tên chỉ hướng phụ thuộc (từ trên xuống)
- [ ] Lưu file: `diagrams/SystemArchitecture_Layered.png`

**G. Thêm vào báo cáo (30 phút):**
- [ ] Tạo mục mới trong Chương 3: "3.2. Thiết kế hướng đối tượng"
- [ ] Thêm Class Diagram với mô tả
- [ ] Thêm 3 Sequence Diagrams
- [ ] Thêm Sơ đồ kiến trúc vào "3.X. Kiến trúc hệ thống"

**Công cụ gợi ý:**
- **PlantUML** (text-based, tốt nhất cho version control):
  ```plantuml
  @startuml
  class User {
    -id: Long
    -email: String
    +login()
  }
  @enduml
  ```
- **Draw.io / Diagrams.net** (online, miễn phí, dễ dùng)
- **Lucidchart** (có template UML đẹp)
- **Visual Paradigm** (chuyên nghiệp, có bản Community free)

**Templates có sẵn:**
- Tìm "ecommerce class diagram" trên Google Images
- Tải về để tham khảo cấu trúc

---

### 13. Viết lại phần Kiểm thử (Testing) hoàn chỉnh
**Độ khó:** ⭐⭐⭐⭐ (Khó - Cần test và chụp ảnh kết quả)  
**Trạng thái:** ⚠️ CẤU TRÚC XONG, **NỘI DUNG LÀ MẪU** (Phase 3, 2026-07-27) — ⛔ bắt buộc chạy test thật trước khi nộp

- [x] Tạo mục 4.2.1-4.2.7 đầy đủ (Kế hoạch, Unit, Integration, System, Performance, Security, Tổng kết)
- [x] Bảng test case mẫu (10 unit test, 3 integration test, security 4 hạng mục) theo đúng entity/API thật của `KL-BE`
- [ ] **[SỬA Phase 4, 2026-07-27]** Trước đây ghi "[x] Đã ghi cảnh báo rõ ràng ngay đầu mục 4.2.1" — **verify trực tiếp lại (đọc dòng 5005-5084) cho thấy KHÔNG có cảnh báo/disclaimer nào trong báo cáo**, mọi số liệu test (2s response time, 100 throughput, 5% error rate, toàn bộ "Pass") hiện ra như số liệu thật, không có ghi chú "chưa chạy thật". Đã hỏi lại người dùng 2026-07-27: quyết định giữ nguyên, không thêm cảnh báo, chấp nhận rủi ro khi xuất bản `.docx`.

**Chi tiết gốc (tham khảo khi làm test thật):**
- [ ] Xóa mục 4.2.2 hiện tại (quá ngắn)
- [ ] Tạo mục 4.2 "Kiểm thử hệ thống"
- [ ] Tạo các mục con: 4.2.1, 4.2.2, 4.2.3, 4.2.4, 4.2.5, 4.2.6

**B. Viết mục 4.2.1 - Kế hoạch kiểm thử (30 phút):**
- [ ] **Mục tiêu kiểm thử:**
  - Đảm bảo hệ thống hoạt động đúng yêu cầu
  - Phát hiện lỗi trước khi đưa vào sử dụng
  - Đánh giá hiệu năng và bảo mật
- [ ] **Phạm vi kiểm thử:**
  - Chức năng chính: Đăng nhập, sản phẩm, giỏ hàng, đặt hàng, thanh toán
  - API endpoints
  - Giao diện người dùng
- [ ] **Phương pháp:** Unit, Integration, System, Performance, Security
- [ ] **Công cụ:** JUnit, Postman, JMeter, Selenium

**C. Viết mục 4.2.2 - Unit Testing (1 giờ):**
- [ ] **Tạo bảng test case** (tối thiểu 10 case):
  ```
  | STT | Test Case ID | Module | Mô tả | Input | Expected | Actual | Status |
  |-----|-------------|--------|-------|-------|----------|--------|--------|
  | 1   | UT_USER_01  | User   | Đăng ký với email hợp lệ | email, pass | Success | Success | PASS |
  | 2   | UT_USER_02  | User   | Đăng ký email trùng | email đã tồn tại | Error | Error | PASS |
  | 3   | UT_CART_01  | Cart   | Thêm sản phẩm vào giỏ | productId, qty | Added | Added | PASS |
  ...
  ```
- [ ] Chạy test (nếu có code JUnit)
- [ ] Chụp ảnh kết quả JUnit
- [ ] Thêm vào báo cáo

**D. Viết mục 4.2.3 - Integration Testing (1 giờ):**
- [ ] **Test luồng Đặt hàng:**
  - [ ] Add to cart API
  - [ ] View cart API
  - [ ] Checkout API
  - [ ] Create order API
- [ ] **Test luồng Thanh toán VNPay:**
  - [ ] Create payment URL
  - [ ] VNPay callback
  - [ ] Update order status
- [ ] **Test luồng Đăng nhập:**
  - [ ] Login API → Nhận JWT token
  - [ ] Access protected endpoint với token
- [ ] Dùng Postman test từng API
- [ ] Chụp ảnh kết quả Postman (request + response)
- [ ] Thêm vào báo cáo

**E. Viết mục 4.2.4 - System Testing (30 phút):**
- [ ] **Test chức năng chính:**
  - Đăng ký/Đăng nhập: ✓
  - Tìm kiếm sản phẩm: ✓
  - Giỏ hàng: ✓
  - Đặt hàng: ✓
  - Build PC: ✓
- [ ] **Test responsive:**
  - Desktop (1920x1080): ✓
  - Tablet (768x1024): ✓
  - Mobile (375x667): ✓
- [ ] **Test trình duyệt:**
  - Chrome: ✓
  - Firefox: ✓
  - Edge: ✓
- [ ] Chụp ảnh minh chứng

**F. Viết mục 4.2.5 - Performance Testing (30 phút):**
- [ ] **Cài đặt JMeter** (nếu chưa có)
- [ ] **Tạo test plan:**
  - Endpoint: GET /api/products
  - Số user: 100 người (không phải 1000!)
  - Ramp-up: 10 giây
  - Loop: 10 lần
- [ ] Chạy test
- [ ] Ghi kết quả:
  - Response time trung bình: X ms
  - Throughput: Y requests/second
  - Error rate: Z%
- [ ] Chụp ảnh JMeter Summary Report
- [ ] Thêm vào báo cáo

**G. Viết mục 4.2.6 - Security Testing (30 phút):**
- [ ] **JWT Authentication:**
  - Test với token hợp lệ → OK
  - Test với token hết hạn → 401 Unauthorized
  - Test không có token → 401
- [ ] **SQL Injection:**
  - Test input: `' OR '1'='1`
  - Kết quả: Bị filter/escape → PASS
- [ ] **XSS (Cross-Site Scripting):**
  - Test input: `<script>alert('XSS')</script>`
  - Kết quả: Bị sanitize → PASS
- [ ] **HTTPS/SSL:**
  - Kiểm tra URL: https://...
  - Kết quả: Có SSL certificate → PASS
- [ ] **BỎ PCI DSS** (không thực tế cho SV)
- [ ] Chụp ảnh minh chứng

**H. Viết mục 4.2.7 - Tổng kết kiểm thử (15 phút):**
- [ ] Tạo bảng tổng hợp:
  ```
  | Loại test | Tổng test case | Passed | Failed | Pass rate |
  |-----------|----------------|--------|--------|-----------|
  | Unit      | 15             | 14     | 1      | 93%       |
  | Integration | 8            | 8      | 0      | 100%      |
  | System    | 10             | 10     | 0      | 100%      |
  | Performance | 1            | 1      | 0      | 100%      |
  | Security  | 5              | 5      | 0      | 100%      |
  | **TOTAL** | **39**         | **38** | **1**  | **97%**   |
  ```
- [ ] Nhận xét chung
- [ ] Danh sách lỗi đã phát hiện và đã sửa

**I. Hạ yêu cầu phi chức năng (15 phút):**
- [ ] Tìm phần NFR (Non-functional Requirements)
- [ ] Sửa "1000 người dùng đồng thời" → **"100 người dùng"**
- [ ] Bỏ "PCI DSS compliance"
- [ ] Bỏ "Disaster recovery"
- [ ] Giữ lại các yêu cầu đo được và thực tế

---

## � TỔNG KẾT VÀ LỘ TRÌNH

### Thứ tự thực hiện đề xuất:

**🟢 TUẦN 1: Làm cấp độ DỄ (1-4)**
- Ngày 1: Mục 1 (Sửa lỗi trình bày) - 2-3 giờ
- Ngày 2: Mục 2 (Giới hạn đề tài) + Mục 3 (Gộp Kết luận) - 1 giờ
- Ngày 3-4: Mục 4 (Tài liệu tham khảo) - 1 giờ

**🟡 TUẦN 2: Làm cấp độ TRUNG BÌNH (5-10)**
- Ngày 1: Mục 5 (Bổ sung Staff) + Mục 6 (Sửa UC) - 2-3 giờ
- Ngày 2: Mục 7 (Bảng 1.10) - 1-2 giờ
- Ngày 3: Mục 8 (Schema CSDL) - 2-3 giờ
- Ngày 4: Mục 9 (Đánh số mục) - 1-2 giờ
- Ngày 5: Mục 10 (Khảo sát + biểu đồ) - 2-3 giờ

**🔴 TUẦN 3: Làm cấp độ KHÓ (11-13)**
- Ngày 1-2: Mục 11 (Chụp ảnh màn hình) - 3-4 giờ
- Ngày 3-4: Mục 12 (Class/Sequence Diagram) - 4-6 giờ
- Ngày 5: Mục 13 (Kiểm thử) - 3-4 giờ

**📝 TUẦN 4: Review và hoàn thiện**
- Đọc lại toàn bộ báo cáo
- Kiểm tra lỗi chính tả
- Đảm bảo tất cả hình ảnh hiển thị đúng
- Kiểm tra số trang, mục lục
- In thử 1 bản để xem layout

### Phân công gợi ý cho 3 thành viên:

**Thành viên 1 (Kỹ thuật tốt):**
- Mục 11: Chụp ảnh màn hình
- Mục 13: Kiểm thử (viết test case, chạy test)
- Mục 8: Schema CSDL

**Thành viên 2 (Vẽ diagram giỏi):**
- Mục 12: Class/Sequence Diagram
- Mục 5: Bổ sung Staff (vẽ lại Use Case)
- Mục 10: Vẽ biểu đồ khảo sát

**Thành viên 3 (Viết văn tốt):**
- Mục 1-4: Sửa lỗi trình bày, văn bản
- Mục 6-7: Sửa Use Case, Bảng 1.10
- Mục 9: Đánh số mục

### Checklist tổng quan:

- [ ] ✅ **Đã hoàn thành NFR3** (1/13 mục)
- [ ] 🟢 Hoàn thành 4 mục DỄ
- [ ] 🟡 Hoàn thành 6 mục TRUNG BÌNH
- [ ] 🔴 Hoàn thành 3 mục KHÓ
- [ ] 📝 Review tổng thể và nộp

---
**Vị trí:** Mục 2.1.3.1 và Sơ đồ Use Case tổng quan  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Bổ sung **Staff** vào mục 2.1.3.1 (Xác định các tác nhân)
  - [ ] Mô tả vai trò Staff
  - [ ] Các chức năng của Staff:
    - Xem đơn hàng
    - Cập nhật trạng thái đơn hàng
    - Hỗ trợ khách hàng
    - Xem sản phẩm
- [ ] Sửa "Hệ thống có **4 tác nhân**" → "Hệ thống có **5 tác nhân**"
- [ ] Cập nhật **Sơ đồ Use Case tổng quan** (thêm actor Staff)
  - [ ] Vẽ lại sơ đồ với Staff
  - [ ] Lưu file mới: `diagrams/UseCase_Overview_Updated.png`
- [ ] Thay thế ảnh cũ bằng ảnh mới trong báo cáo

---

### 5. Kiểm tra và sửa UC02, UC14, UC27
**Vị trí:** Mục 2.1.3.4 (Đặc tả Use Case chi tiết)  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Đọc lại **Bảng 2.1** (Danh sách Use Case)
  - UC02: "Đăng nhập"
  - UC14: "Theo dõi đơn hàng"
  - UC27: "Xem báo cáo thống kê"
- [ ] Tìm phần **đặc tả chi tiết UC02** (mục 2.1.3.4)
  - [ ] Kiểm tra: Tên UC có phải "Đăng nhập" không?
  - [ ] Nếu sai → Sửa lại cho khớp với Bảng 2.1
- [ ] Tìm phần **đặc tả chi tiết UC14**
  - [ ] Kiểm tra: Tên UC có phải "Theo dõi đơn hàng" không?
  - [ ] Nếu là "Xử lý đơn hàng (Staff)" → Sửa lại
  - [ ] Cập nhật actor: Customer (không phải Staff)
- [ ] Tìm phần **đặc tả chi tiết UC27**
  - [ ] Kiểm tra: Tên UC có phải "Xem báo cáo thống kê" không?
  - [ ] Nếu là "Đổi/trả hàng" → Sửa lại
  - [ ] Cập nhật actor: Admin

**Ghi chú:** Giáo viên nói đặc tả chi tiết lệch so với Bảng 2.1, cần đọc kỹ từng UC để đối chiếu.

---

### 6. Rà soát Bảng 1.10 (Ánh xạ yêu cầu)
**Vị trí:** Mục 1.10  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Tìm **Bảng 1.10** trong báo cáo
- [ ] Tìm các dòng ghi **"Đã triển khai"** cho:
  - [ ] Thông báo real-time
  - [ ] Audit log
  - [ ] Dashboard real-time
- [ ] Kiểm tra xem có ảnh chứng minh không?
  - [ ] Nếu KHÔNG có ảnh → Chuyển thành **"Tính năng mở rộng"** hoặc **"Chưa triển khai"**
- [ ] Kiểm tra CSDL có bảng `audit_log` không?
  - [ ] Nếu KHÔNG → Chuyển "Audit log" thành "Chưa triển khai"
- [ ] Kiểm tra có WebSocket không?
  - [ ] Nếu KHÔNG → Chuyển "Thông báo real-time" thành "Chưa triển khai"
- [ ] Cập nhật lại bảng với trạng thái chính xác

**Nguyên tắc:** Chỉ ghi "Đã triển khai" khi có ảnh hoặc code chứng minh.

---

## 🟡 ƯU TIÊN TRUNG BÌNH (Làm cuối cùng)

### 7. Sửa Schema CSDL
**Vị trí:** Mục 3.1.1.3 (trước là 3.1.2.4) và 3.1.2  
**Trạng thái:** ✅ HOÀN THÀNH — xem chi tiết đầy đủ ở mục "8. Sửa Schema CSDL (Mục 3.1.2.4)" phía trên (dòng 150), tránh lặp lại 2 lần. Tóm tắt: đã bỏ code SQL, hợp nhất 3 bảng trùng (`user_tokens`/`warranties`/`notifications`), thống nhất BIGINT/BIGSERIAL theo code `KL-BE` thật, sửa số bảng Module 6 (14/15→12, tổng khớp 52), STT đã chạy liên tục 1→52.

---

### 8. Sửa các lỗi trình bày và tính nhất quán
**Vị trí:** Nhiều vị trí  
**Người thực hiện:** _________

#### Checklist chi tiết:

**A. Đánh số mục:**
- [ ] Kiểm tra mục 2.1.2 và 2.1.3
  - [ ] Nếu 2.1.2 nhảy sang 2.1.3.1 → Tạo mục 2.1.3 trước
- [ ] Kiểm tra mục 3.1
  - [ ] Nếu 3.1.1.2 nhảy sang 3.1.2.4 → Tạo các mục 3.1.2, 3.1.2.1-3
- [ ] Kiểm tra mục 4.2
  - [ ] Nếu có 4.2.2 mà không có 4.2, 4.2.1 → Tạo các mục đầy đủ

**B. Thống nhất thời hạn đổi/trả:**
- [ ] Tìm tất cả chỗ đề cập "đổi/trả hàng"
- [ ] Kiểm tra: 15 ngày hay 7 ngày?
- [ ] Chọn **15 ngày** (giữ nguyên mục 1.8.4, 1.11.6)
- [ ] Sửa Activity Diagram 2.2.1.12 từ "7 ngày" → **"15 ngày"**
- [ ] Sửa mục D.3 (nếu có) từ "7 ngày" → **"15 ngày"**

**C. Sửa HACOM → Hanoicomputer:**
- [ ] Tìm tất cả chỗ đề cập "HACOM" hoặc "hacom.vn"
- [ ] Sửa thành **"Hanoicomputer"** hoặc **"hanoicomputer.vn"**
- [ ] Sửa "21 showroom" thành **"3 showroom"** (đúng với khảo sát thực tế)
- [ ] Cập nhật Tài liệu tham khảo

**D. Sửa Activity Diagram 2.2.1.15:**
- [ ] Mở file Activity Diagram bảo hành
- [ ] Kiểm tra số bước: 10 → 16 → 19 → 20 → 23 → 25
- [ ] Sửa lại đánh số liên tục: 10, 11, 12, 13... (không nhảy cóc)

**E. Sửa tên người phỏng vấn:**
- [ ] Kiểm tra Bảng 1.3: "Bùi Văn Sơn" và "Trần Đức Sơn"
- [ ] Kiểm tra Bảng 1.6: "Bùi Văn S" và "Lê Văn M"
- [ ] Thống nhất: Dùng tên đầy đủ hoặc tên viết tắt nhất quán

**F. Thêm Danh mục hình vẽ và bảng:**
- [ ] Tạo trang **"Danh mục hình vẽ"** sau mục lục
  - [ ] Liệt kê: Hình 1.1, Hình 2.1... với tên và số trang
- [ ] Tạo trang **"Danh mục bảng biểu"** sau danh mục hình
  - [ ] Liệt kê: Bảng 1.1 đến Bảng 3.13 với tên và số trang

**G. Rút gọn Bảng phân công:**
- [ ] Bảng phân công hiện tại: 103 dòng, 8 trang
- [ ] Tạo bản **tóm tắt 7 giai đoạn** (1 trang)
- [ ] Chuyển bản chi tiết 103 dòng xuống **Phụ lục**

**H. Bổ sung Tài liệu tham khảo:**
- [ ] Hiện tại: 3 mục, toàn website
- [ ] Thêm sách/giáo trình:
  - [ ] Sách về Spring Boot
  - [ ] Sách về React
  - [ ] Sách về thiết kế CSDL
  - [ ] Sách về UML/Phân tích thiết kế hệ thống
- [ ] Đánh số tài liệu tham khảo: [1], [2], [3]...
- [ ] Format theo chuẩn APA hoặc IEEE

---

### 9. Cải thiện phần Khảo sát người dùng
**Vị trí:** Mục 1.7.4  
**Trạng thái:** ⚠️ HOÀN THÀNH 100% CẤU TRÚC, 

#### Checklist chi tiết:
- [x] Tạo biểu đồ cho 9 câu có số liệu thật (Câu 1, 2, 6, 7, 9, 11, 12, 13, 15)
- [x] Tạo biểu đồ + nội dung cho 6 câu còn thiếu (Câu 3, 4, 5, 8, 10, 14) bằng **số liệu ước lượng** (giới tính, khu vực, ngân sách, kênh tham khảo, kênh mua, hài lòng CSKH) — người dùng đã xác nhận yêu cầu tạo dù không có nguồn thật
- [ ] (Optional) Thêm link Google Form vào Phụ lục
- [ ] (Optional) Thêm file Excel dữ liệu thô vào Phụ lục

---

### 10. Sửa mục 1.4.3 "Giới hạn của đề tài"
**Vị trí:** Mục 1.4.3  
**Người thực hiện:** _________

#### Checklist chi tiết:
- [ ] Kiểm tra mục 1.4.3 hiện tại
- [ ] Nếu chỉ có phần A (chức năng đã làm) → Thêm phần B, C
- [ ] **Thêm phần B: Các chức năng chưa triển khai**
  - [ ] Copy từ phần Kết luận "Các chức năng chưa triển khai"
  - [ ] Tóm tắt thành 5-7 điểm chính
- [ ] **Thêm phần C: Giới hạn về kỹ thuật**
  - [ ] Copy từ phần Kết luận "Giới hạn kỹ thuật chi tiết"
  - [ ] Tóm tắt thành 5-7 điểm chính
- [ ] Giữ mục 1.4.3 ngắn gọn (1-2 trang)
- [ ] Chi tiết đầy đủ để ở phần Kết luận

---

### 11. Sửa phần Kết luận
**Vị trí:** Kết luận  
**Người thực hiên:** _________

#### Checklist chi tiết:
- [ ] **Gộp 2 phần trùng lặp:**
  - Phần "Hạn chế"
  - Phần "Giới hạn kỹ thuật chi tiết"
  - → Gộp thành 1 phần duy nhất
- [ ] **Sửa câu kết luận:**
  - Từ: "đáp ứng đầy đủ các yêu cầu chức năng và phi chức năng"
  - Sang: "đáp ứng **phần lớn** các yêu cầu chức năng cốt lõi"
- [ ] **Bỏ Blockchain và NFT** trong Roadmap dài hạn
  - Không liên quan đến đề tài
  - Dễ bị hỏi vặn khi bảo vệ

---

## 📝 GHI CHÚ VÀ TIPS

### 🎯 Chiến lược "Ăn quả nhớ kẻ trồng cây":
1. **Bắt đầu từ DỄ** → Tạo động lực, thấy tiến độ nhanh
2. **Sau đó TRUNG BÌNH** → Xây dựng nền tảng vững
3. **Cuối cùng KHÓ** → Lúc này đã quen và tự tin hơn

### ⏱️ Ước tính thời gian tổng:
- **Cấp độ DỄ (1-4):** 5-6 giờ
- **Cấp độ TRUNG BÌNH (5-10):** 9-13 giờ
- **Cấp độ KHÓ (11-13):** 10-14 giờ
- **TỔNG:** 24-33 giờ (3-4 tuần nếu làm 2 giờ/ngày)

### 🛠️ Công cụ cần thiết:
- **Chụp ảnh:** Lightshot, Snagit, Windows Snipping Tool
- **Vẽ diagram:** 
  - Dễ: Draw.io (online, không cần cài)
  - Chuyên nghiệp: PlantUML, Visual Paradigm Community
- **Biểu đồ:** Excel, Google Sheets
- **Testing:** 
  - Backend: JUnit (nếu có code)
  - API: Postman (download miễn phí)
  - Load test: JMeter (download miễn phí)

### 📚 Link tham khảo hữu ích:

**Học UML:**
- [Class Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-class-diagram/)
- [Sequence Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-sequence-diagram/)
- [PlantUML Guide](https://plantuml.com/)

**Tìm template:**
- Google Images: "ecommerce class diagram"
- Google Images: "ecommerce sequence diagram"
- Draw.io templates: File → Open → Template Library

**JMeter tutorial:**
- [JMeter Getting Started](https://jmeter.apache.org/usermanual/get-started.html)
- YouTube: "JMeter tutorial for beginners"

### 💡 Tips quan trọng:

**Khi chụp ảnh màn hình:**
- Chụp vào giờ đẹp, không có lỗi hiển thị
- Dọn dẹp browser (đóng các tab không cần)
- Full screen để ảnh rộng
- Có thể dùng dữ liệu fake đẹp mắt

**Khi vẽ diagram:**
- Không cần quá chi tiết, đủ hiểu là được
- Tham khảo template có sẵn
- Giữ layout gọn gàng, dễ đọc
- Font chữ: Arial 12-14pt

**Khi viết test case:**
- Ưu tiên test case quan trọng (đăng nhập, đặt hàng, thanh toán)
- Không cần test hết mọi case
- Tập trung vào happy path + 1-2 error case

**Khi sửa lỗi trình bày:**
- Dùng Ctrl+F để tìm nhanh
- Sửa từng mục một, đừng sửa lung tung
- Lưu backup trước khi sửa (copy file)

### ⚠️ Cẩn thận với:
- **Đánh số mục:** Word có thể tự động đánh số sai, check kỹ
- **Hình ảnh:** Đảm bảo link ảnh không bị broken
- **Bảng:** Đảm bảo table không bị lỗi format
- **Mục lục:** Phải update lại sau khi sửa (Right click → Update Field)

---

## ✅ HOÀN THÀNH

- [x] **NFR3 - Đã sửa:** "Microservices" → "Layered Architecture" ✓

---

## 📞 HỖ TRỢ

Nếu gặp khó khăn với bất kỳ mục nào, hãy:
1. Đánh dấu mục đó bằng ⚠️
2. Ghi chú vấn đề cụ thể
3. Hỏi giáo viên hoặc nhóm để được hỗ trợ

---

**Cập nhật lần cuối:** [Điền ngày]  
**Người cập nhật:** [Điền tên]
