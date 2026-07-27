# Quy Trình Cập Nhật Báo Cáo Khi Có Yêu Cầu Thay Đổi

## Tổng quan

Tài liệu này mô tả các bước chuẩn để xử lý một yêu cầu thay đổi (từ GV, thành viên nhóm, hoặc tự rà soát) đối với báo cáo KLTN, từ lúc tiếp nhận đến lúc đánh dấu hoàn thành. Áp dụng cho `KLTN_BaoCao_WebsiteBanMayTinh_KinhDuan_Ver2.md` và bản `.docx` tương ứng.

**Vì sao cần quy trình:** báo cáo dài 5000+ dòng, nhiều phần tham chiếu chéo nhau (mục lục, đánh số chương, bảng số liệu, diagram) — sửa 1 chỗ dễ làm lệch chỗ khác nếu không kiểm tra hệ thống. Kinh nghiệm thực tế: `PROGRESS_REPORT.md` từng ghi nhận sai một số mục đã xong (numbering chương 2, tên người phỏng vấn) vì không re-verify sau khi sửa.

## Các file liên quan và vai trò

| File | Vai trò |
|---|---|
| `NhanXet_KLTN_Nhom10_KinhDuan_Ver2.md` | Nguồn yêu cầu thay đổi gốc (nhận xét GV) — **không sửa file này** |
| `Ke_Hoach_Chinh_Sua_Bao_Cao.md` | Kế hoạch tổng thể, nhóm các nhận xét thành hạng mục |
| `CHECKLIST_RESOLVE.md` | Checklist chi tiết từng việc cần làm, phân độ khó Dễ/Trung bình/Khó |
| `PROGRESS_REPORT.md` | Trạng thái đã làm/chưa làm — **cập nhật sau mỗi lần sửa**, không suy đoán |
| `KLTN_BaoCao_WebsiteBanMayTinh_KinhDuan_Ver2.md` | Bản nội dung báo cáo (Markdown) — file sửa chính |
| `.docx` tương ứng | Bản nộp cuối cùng — export lại từ Markdown khi hoàn tất một đợt sửa |

## Quy trình từng bước

### Bước 1 — Tiếp nhận yêu cầu thay đổi
- Ghi yêu cầu vào `Ke_Hoach_Chinh_Sua_Bao_Cao.md` nếu là hạng mục mới (chưa có trong checklist hiện tại).
- Nếu yêu cầu khớp mục đã có trong `CHECKLIST_RESOLVE.md`, dùng lại mục đó, không tạo trùng.

### Bước 2 — Phân loại mức độ
Theo khung có sẵn trong `CHECKLIST_RESOLVE.md`:
- 🟢 **Dễ**: sửa text/số liệu đơn lẻ, không ảnh hưởng cấu trúc.
- 🟡 **Trung bình**: sửa nội dung kỹ thuật, có thể cần sửa bảng/diagram liên quan.
- 🔴 **Khó**: cần tạo nội dung mới (ảnh chụp màn hình, diagram UML, bảng test case).

Phân loại sai sẽ ước lượng sai thời gian — ưu tiên xử lý Dễ trước để tạo tiến độ nhìn thấy được.

### Bước 3 — Xác định phạm vi ảnh hưởng
Trước khi sửa, tìm **tất cả** vị trí liên quan bằng full-text search (Ctrl+F trong Word, hoặc `grep` trên bản Markdown), không chỉ sửa chỗ đầu tiên tìm thấy. Với mỗi thay đổi, kiểm tra các nhóm sau có bị ảnh hưởng không:
1. Nội dung chính (thân bài).
2. Mục lục / Danh mục hình vẽ / Danh mục bảng biểu (thường lệch số trang sau khi sửa — cần Update Field trong Word).
3. Bảng số liệu liên quan (vd: sửa số showroom phải sửa cả bảng CSDL, cả Activity Diagram nếu có nhắc).
4. Diagram/hình ảnh minh họa (activity diagram, use case diagram, ERD) — nếu số liệu/tên trong hình không khớp text mới, phải vẽ lại và export ảnh mới.
5. Đánh số mục (heading numbering) — sửa/thêm 1 mục có thể làm lệch số các mục sau.

### Bước 4 — Verify tình trạng hiện tại (bắt buộc, trước khi sửa)
Không tin tưởng 100% vào ghi chú cũ trong `PROGRESS_REPORT.md` — luôn kiểm tra lại bằng cách đọc/grep trực tiếp nội dung hiện tại của file báo cáo trước khi kết luận "đã xong" hay "chưa làm". Đây là bước từng bị bỏ qua và gây sai lệch báo cáo tiến độ.

### Bước 5 — Thực hiện chỉnh sửa
- Sửa trực tiếp trên bản nội dung chính thức (Word nếu là bản nộp, hoặc Markdown nếu nhóm đang thao tác trên bản `.md`).
- Với thay đổi ảnh hưởng nhiều vị trí: sửa hết toàn bộ vị trí đã liệt kê ở Bước 3 trong cùng một lần, tránh sửa rải rác gây bỏ sót.
- Với diagram cần vẽ lại: lưu file nguồn (PlantUML/Draw.io) và ảnh export vào đúng thư mục con hiện có (`activity-diagram/`, `usecases/`, `ERD_Modules/`), đặt tên nhất quán với ảnh cũ đang thay thế.

### Bước 6 — Kiểm tra tính nhất quán sau khi sửa
- Đọc lại đoạn vừa sửa và các vị trí liên quan đã liệt kê ở Bước 3.
- Với thay đổi số liệu/đánh số: đếm lại tổng số liên quan (vd: tổng số bảng CSDL, tổng số tác nhân Use Case) để câu tổng kết khớp con số thực tế.
- Với thay đổi cấu trúc mục: kiểm tra mục trước và mục sau không bị nhảy số.

### Bước 7 — Cập nhật file theo dõi tiến độ
- Cập nhật `CHECKLIST_RESOLVE.md`: tick các checkbox đã hoàn thành.
- Cập nhật `PROGRESS_REPORT.md`: đổi trạng thái mục tương ứng (❌ → ⚠️ → ✅), ghi rõ bằng chứng (số dòng/mục đã sửa) thay vì ghi chung chung.
- Không đánh dấu "hoàn thành" nếu chỉ sửa được một phần vị trí liên quan.

### Bước 8 — Review toàn bộ đoạn đã sửa
Đọc lại nguyên đoạn (không chỉ dòng vừa sửa) để phát hiện lỗi ngữ cảnh, câu cụt, hoặc nội dung copy-paste còn sót từ bản cũ.

### Bước 9 — Đồng bộ Markdown ↔ Word
Nếu nhóm dùng bản `.md` làm bản nháp thao tác nhanh: sau khi hoàn tất một đợt sửa, export/copy nội dung sang bản `.docx` chính thức để nộp, kiểm tra lại định dạng (bảng, hình, số trang) không bị vỡ khi chuyển đổi.

### Bước 10 — Commit
Commit trong git repo `DATN-BaoCao` với message mô tả rõ hạng mục đã sửa (vd: "Sửa 21 showroom → 3 showroom, bổ sung Staff vào 2.1.3.1"), không gộp nhiều hạng mục không liên quan vào 1 commit để dễ truy vết khi cần rollback.

## Checklist nhanh trước khi coi 1 mục là "hoàn thành"

- [ ] Đã sửa hết mọi vị trí xuất hiện (không chỉ vị trí đầu tiên tìm thấy)
- [ ] Số liệu tổng (đếm bảng, đếm tác nhân, đếm mục...) đã khớp với thay đổi
- [ ] Mục lục / danh mục hình / danh mục bảng đã cập nhật nếu cấu trúc thay đổi
- [ ] Diagram/hình ảnh liên quan đã khớp nội dung text mới
- [ ] `CHECKLIST_RESOLVE.md` và `PROGRESS_REPORT.md` đã cập nhật đúng trạng thái thực tế
- [ ] Đã đọc lại toàn đoạn, không chỉ dòng vừa sửa

## Tham chiếu
- [Ke_Hoach_Chinh_Sua_Bao_Cao.md](./Ke_Hoach_Chinh_Sua_Bao_Cao.md)
- [CHECKLIST_RESOLVE.md](./CHECKLIST_RESOLVE.md)
- [PROGRESS_REPORT.md](./PROGRESS_REPORT.md)
- [NhanXet_KLTN_Nhom10_KinhDuan_Ver2.md](./NhanXet_KLTN_Nhom10_KinhDuan_Ver2.md)
