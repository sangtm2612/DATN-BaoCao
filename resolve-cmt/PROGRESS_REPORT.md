# 📊 BÁO CÁO TIẾN ĐỘ RESOLVE - KLTN NHÓM 10

**Ngày cập nhật:** 2026-07-27 (qua `/ck:cook` plan `260726-2322-bao-cao-cac-muc-chua-hoan-thanh`, Phase 1+2+5 + Class/Sequence Diagram của Phase 3; GraphViz cài xong nên Mục 5 Staff + Mục 12 Diagram nay 100%)
**File được scan:** `KLTN_BaoCao_WebsiteBanMayTinh_KinhDuan_Ver2.md`

---

## ✅ TỔNG QUAN

**Tiến độ tổng thể:** 9/13 mục hoàn thành 100%, 2/13 một phần, 2/13 chưa làm

### Phân theo độ khó:
- 🟢 **DỄ (4 mục):** 4/4 hoàn thành ✓ (100%)
- 🟡 **TRUNG BÌNH (6 mục):** 5/6 hoàn thành, 1 mục còn dở (Đánh số mục — Chương 4 thiếu 4.2.1, thiếu Danh mục hình/bảng)
- 🔴 **KHÓ (3 mục):** 1/3 hoàn thành 100% (Mục 12), 1/3 cấu trúc xong nhưng nội dung mẫu (Mục 13 — cần chạy test thật), 1/3 chưa làm (Mục 11 — cần hệ thống chạy để chụp ảnh)

---

## 🟢 CẤP ĐỘ DỄ - Tiến độ: 4/4 (100%)

### ✅ MỤC 1: Sửa lỗi trình bày đơn giản
**Trạng thái:** ✅ HOÀN THÀNH 100%

- Thời hạn đổi/trả "15 ngày" nhất quán (1.8.4, 1.11.6, 2.2.1.5)
- Blockchain/NFT: không còn trong Roadmap
- HACOM → Hanoicomputer: grep = 0 kết quả
- Tên người phỏng vấn: đã nhất quán ("Bùi Văn Sơn", "Trần Đức Sơn")
- Câu kết luận mục tiêu (dòng 259): đã sửa "đáp ứng đầy đủ" → "đáp ứng phần lớn các yêu cầu chức năng cốt lõi"
- ⚠️ **"21 showroom" giữ nguyên — QUYẾT ĐỊNH (Validation Session 1):** xác nhận đây là số liệu đúng, đề xuất đổi "3 showroom" trước đó đã bị bác bỏ, không sửa.

---

### ✅ MỤC 2: Sửa mục 1.4.3 "Giới hạn của đề tài"
**Trạng thái:** ✅ HOÀN THÀNH 100%

Đủ 3 phần: A (chức năng đã triển khai), B (chưa triển khai — 4 nhóm), C (giới hạn kỹ thuật — 8 nhóm).

---

### ✅ MỤC 3: Gộp phần trùng lặp ở Kết luận
**Trạng thái:** ✅ HOÀN THÀNH 100%

Đã gộp thành 1 mục "Hạn chế của đề tài", không còn 2 heading riêng ("Hạn chế" + "Giới hạn kỹ thuật chi tiết") trong nội dung.

---

### ✅ MỤC 4: Bổ sung Tài liệu tham khảo
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27)

- Đã thêm 3 sách/giáo trình học thuật: Database System Concepts (Silberschatz, 2020), UML Distilled (Fowler, 2003), Spring Boot in Action (Walls, 2022)
- Đánh số [1] đến [10], format Tác giả/Năm/Tên/NXB
- Giữ nguyên các tài liệu kỹ thuật cũ (Spring Docs, React Docs, PostgreSQL Docs, JWT Docs, VNPay, 2 website khảo sát)

---

## 🟡 CẤP ĐỘ TRUNG BÌNH - Tiến độ: 5/6 hoàn thành

### ✅ MỤC 5: Bổ sung tác nhân Staff
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27; PNG render xong sau khi cài GraphViz)

- ✅ Mục 2.1.3.1: "4 tác nhân" → "5 tác nhân", đã thêm mục "4. Nhân viên (Staff)" với đủ 5 chức năng
- ✅ Đã thêm actor Staff + quan hệ vào source `usecases/00_UseCase_TongQuat.puml`
- ✅ Đã render PNG (GraphViz cài qua winget) và thay ảnh trong báo cáo (`bao-cao/images/media/image7.png`, dùng ở mục 2.1.3.3). Lưu ý kỹ thuật: bắt buộc dùng cờ `-C UTF-8` khi render, thiếu cờ này chữ tiếng Việt bị lỗi mojibake.

---

### ✅ MỤC 6: Kiểm tra và sửa UC02, UC14, UC27
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 2, 2026-07-27)

- UC02: không có đặc tả chi tiết (đã mất cùng nội dung sai "Quản lý sản phẩm (Admin)" từ lần sửa trước) → đã viết bổ sung đặc tả đúng "Đăng nhập", khớp Bảng 2.1
- UC14, UC27: verify — đã đúng từ trước, không cần sửa

---

### ✅ MỤC 7: Rà soát Bảng 1.10
**Trạng thái:** ✅ ĐÃ VERIFY, KHÔNG CẦN SỬA (Phase 2, 2026-07-27)

Đọc lại toàn bộ 13 dòng — Dashboard real-time, Thông báo push, Audit log, Template trả lời nhanh, Phân loại VIP đều đã ghi đúng "Tính năng mở rộng", không còn dòng nào ghi sai "Đã triển khai".

---

### ✅ MỤC 8: Sửa Schema CSDL
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 5, 2026-07-27 — mục này bị bỏ sót hoàn toàn khỏi plan ban đầu, đã phát hiện và bổ sung xử lý)

- Bỏ code SQL: chuyển 34 `CREATE TABLE` (mục 3.1.1.3 + 3.1.2) thành bảng Markdown, verify grep `CREATE TABLE` = 0
- Hợp nhất schema trùng: phát hiện 3 bảng trùng thật (`user_tokens`, `warranties`, `notifications`), giữ bản đầy đủ hơn, xóa bản trùng
- Thống nhất kiểu dữ liệu: verify code thật `KL-BE` (`Long id` + `GenerationType.IDENTITY`) → đổi 11 chỗ SERIAL→BIGSERIAL, 23 chỗ INT REFERENCES→BIGINT REFERENCES
- Bảng `stores`: verify lại, chỉ còn 1 định nghĩa (STT 43), không trùng
- Thống nhất số bảng: phát hiện lỗi thật Module 6 ghi "14"/"15 bảng" nhưng đếm thực tế 12 → đã sửa, tổng 12 module nay khớp 52 (khớp TỔNG CỘNG và STT 1→52)

---

### ⚠️ MỤC 9: Đánh số mục lại cho đúng
**Trạng thái:** ⚠️ HOÀN THÀNH 60% (Phase 2, 2026-07-27)

- ✅ Chương 2: đã đúng từ trước (2.1.1→2.1.2→2.1.3→2.1.3.1 liên tục)
- ✅ Chương 3: đã sửa — đổi `3.1.3`→`3.1.2` (Các bảng bổ sung), và phát hiện thêm lỗ hổng thật `3.1.1.2`→`3.1.2.4` (đúng như nhận xét GV) → đã đổi `3.1.2.4`→`3.1.1.3`, Chương 3 nay đánh số liên tục 3.1.1→3.1.1.1→3.1.1.2→3.1.1.3→3.1.2
- ⚠️ Chương 4: đã tạo heading `4.2. Kiểm thử hệ thống` làm mục cha trước `4.2.2`. **`4.2.1` "Kế hoạch kiểm thử" chưa tạo** — để dành cho Phase 3 khi viết nội dung kiểm thử thật
- ❌ Danh mục hình vẽ + Danh mục bảng biểu: chưa có — **chuyển sang Phase 4**, nên tạo bằng tính năng "Insert Table of Figures/Tables" của Word khi đồng bộ `.docx` (Markdown không có số trang nên không thể liệt kê chính xác)

---

### ⚠️ MỤC 10: Cải thiện phần Khảo sát
**Trạng thái:** ⚠️ ĐỦ 15/15 CÂU VỀ CẤU TRÚC, nhưng **6 câu là số liệu ƯỚC LƯỢNG** — ⛔ BẮT BUỘC thay bằng số liệu thật trước khi nộp

- ✅ Câu 1, 2, 6, 7, 9, 11, 12, 13, 15 (9/15): số liệu thật, đã có biểu đồ
- ⚠️ Câu 3, 4, 5, 8, 10, 14 (6/15): **không có số liệu nguồn trong repo** (đã kiểm tra `bien-bao-khao-sat/` — 2 file đó là phỏng vấn nhân viên FPT Shop/Hanoicomputer, khác khảo sát 156 khách hàng này). Theo yêu cầu người dùng (2026-07-27), đã tạo số liệu **ƯỚC LƯỢNG** + biểu đồ để đủ cấu trúc 15/15 câu, đánh dấu rõ `[⚠️ SỐ LIỆU ƯỚC LƯỢNG]` ở từng câu và ghi chú cảnh báo liêm chính học thuật ở cuối mục 1.7.4
- ⛔ **RỦI RO:** nếu nộp nguyên trạng, đây là số liệu bịa — phải thay bằng dữ liệu khảo sát thật (Google Form/Excel) trước khi bảo vệ

---

## 🔴 CẤP ĐỘ KHÓ - Tiến độ: 0/3 (0%)

### ❌ MỤC 11: Bổ sung ảnh chụp màn hình
**Trạng thái:** ❌ CHƯA LÀM 0% — xem Phase 3 của plan `260726-2322-bao-cao-cac-muc-chua-hoan-thanh`

Chương 4 vẫn chỉ có mô tả text cho 8 màn hình, mục 3.3.3 "Design" cũng chỉ text, chưa có ảnh, link GitHub, hay URL demo.

---

### ✅ MỤC 12: Class Diagram và Sequence Diagram
**Trạng thái:** ✅ HOÀN THÀNH 100% (Phase 3, 2026-07-27)

- ✅ Class Diagram tổng quan (mục 3.4.1): 15 class chính, attributes lấy thật từ entity `KL-BE`
- ✅ Sơ đồ kiến trúc Layered (mục 3.4.2): khớp câu "Layered Architecture" đã claim ở Kết luận — hết mâu thuẫn lời văn/hình ảnh
- ✅ 3 Sequence Diagram (mục 3.4.3): Đặt hàng, Thanh toán VNPay, Build PC

---

### ⚠️ MỤC 13: Viết kiểm thử
**Trạng thái:** ⚠️ CẤU TRÚC XONG, NỘI DUNG LÀ MẪU (Phase 3, 2026-07-27) — ⛔ bắt buộc chạy test thật trước khi nộp

- ✅ Đã tạo đủ 4.2.1-4.2.7 (Kế hoạch, Unit, Integration, System, Performance, Security, Tổng kết) với bảng test case theo đúng entity/API thật của `KL-BE`
- ⛔ **`KL-BE`/`KL-FE` không có file test nào** (0 file `*Test.java`) — mọi kết quả Pass/Fail, response time đang là placeholder `⚠️ Cần chạy`, KHÔNG PHẢI số liệu thật
- **RỦI RO tương tự Mục 10:** nếu nộp nguyên trạng, đây là bịa kết quả kiểm thử. Đã ghi cảnh báo rõ trong báo cáo (đầu mục 4.2.1).

---

## 🎯 KẾT LUẬN VÀ KHUYẾN NGHỊ

### 📊 Tổng kết:
- **✅ Hoàn thành 100%:** 9/13 mục (Mục 1, 2, 3, 4, 5, 6, 7, 8, 12)
- **⚠️ Hoàn thành một phần:** 2/13 mục (Mục 9 đánh số — 60%; Mục 10 khảo sát — đủ cấu trúc 15/15 câu nhưng 6 câu là số liệu ƯỚC LƯỢNG, ⛔ bắt buộc thay số liệu thật trước khi nộp)
- **❌ Chưa làm:** 1/13 mục (Mục 11 ảnh chụp màn hình — cần hệ thống chạy thật để chụp)
- **⚠️ Cấu trúc xong, nội dung mẫu cần thay thật:** Mục 13 kiểm thử (giống Mục 10, ⛔ bắt buộc chạy test thật trước khi nộp)

### 🔥 Việc còn lại (theo plan `plans/260726-2322-bao-cao-cac-muc-chua-hoan-thanh/`):

**Phase 3 (ưu tiên cao nhất, chưa làm):**
1. Chụp 10-12 ảnh màn hình hệ thống thật, chèn vào mục 3.3.3 + Chương 4.1.1, thêm link GitHub/demo (Mục 11) — cần `KL-FE`/`KL-BE` chạy
2. ⛔ Chạy test thật cho Mục 13: viết JUnit trong `KL-BE`, test Postman, chạy JMeter — thay hết các ô `⚠️ Cần chạy` trong mục 4.2.2-4.2.7 bằng kết quả thật + ảnh chụp minh chứng

**Việc lặt vặt còn sót:**
3. Tạo Danh mục hình vẽ + Danh mục bảng biểu trong Word (không phải Markdown) — Mục 9


**Phase 4 (làm sau cùng):** Review tổng thể, kiểm tra tham chiếu chéo, đồng bộ Markdown → Word, update Mục lục/Danh mục hình-bảng.

### ✅ Điểm mạnh:
- Cấp độ Dễ đã 100% hoàn thành
- Schema CSDL đã sửa triệt để, có đối chiếu với code thật (`KL-BE`) chứ không đoán
- Mọi thay đổi đều verify lại bằng grep, không chỉ tin theo báo cáo tiến độ cũ (bài học từ lần review trước: từng ghi sai trạng thái một số mục)

---

**Lưu ý:** File này phản ánh trạng thái đã verify trực tiếp trên nội dung báo cáo (grep/đọc file), không suy đoán. Chi tiết từng bước xem `CHECKLIST_RESOLVE.md` và plan `plans/260726-2322-bao-cao-cac-muc-chua-hoan-thanh/`.
