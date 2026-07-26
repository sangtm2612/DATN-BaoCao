## \* Chương 4 không có ảnh chụp màn hình nào

Chưa có kết quả demo hệ thống

## \* Mã Use Case gán sai - 3/7 bản đặc tả lệch so với Bảng 2.1

- **UC02** - Bảng 2.1 ghi "Đăng nhập", nhưng phần đặc tả lại là "Quản lý sản phẩm (Admin)".
- **UC14** - Bảng 2.1 ghi "Theo dõi đơn hàng", nhưng phần đặc tả lại là "Xử lý đơn hàng (Staff)".
- **UC27** - Bảng 2.1 ghi "Xem báo cáo thống kê", nhưng phần đặc tả lại là "Đổi/trả hàng".

## \* Schema định nghĩa trùng nhưng nội dung khác nhau

Không cần đưa code tạo các bảng của CSDL

#### Mục 3.1.2.4. Chi tiết schema các bảng 

## \* Số bảng cơ sở dữ liệu không khớp

Báo cáo ghi "50 bảng",

cộng số bảng của 12 module thì được 55, còn số thứ tự lại chạy đến 53. Riêng bảng `stores` bị đếm hai lần (STT 25 ở Module 6 và STT 44 ở Module 9).

## \* Thiếu tác nhân Staff

Mục 2.1.3.1 chỉ liệt kê 4 tác nhân (Guest, Customer, Admin, Payment Gateway); sơ đồ use case tổng quan cũng chỉ vẽ 3 tác nhân. Trong khi đó mục 1.10, ma trận phân quyền 3.2.2 và bản đặc tả UC14 đều sử dụng vai trò Staff.

## \* Mâu thuẫn giữa "đã triển khai" và "chưa có"

Bảng 1.10 (Ánh xạ yêu cầu) ghi *Đã triển khai* cho: thông báo real-time, audit log, dashboard real-time. Nhưng phần Kết luận lại ghi "Chưa có hệ thống notification real-time", "No WebSocket"; và trong hơn 50 bảng cơ sở dữ liệu **không tồn tại bảng audit_log nào**.

Tương tự, mục 2.2.1.13 mô tả cả Facebook OAuth trong khi Kết luận ghi "chỉ hỗ trợ Google OAuth".

# \* TỒN TẠI TỪ LẦN GÓP Ý TRƯỚC CHƯA ĐƯỢC SỬA

- **NFR3 vẫn ghi "kiến trúc microservices"** trong khi Kết luận ghi "Monolithic Architecture, chưa áp dụng microservices". Lỗi này đã được nêu ở nhận xét
- **Các yêu cầu phi chức năng vẫn quá tham vọng và chưa kiểm chứng:** 1000 người dùng đồng thời, chuẩn PCI DSS, uptime 99%, disaster recovery. Trong khi mục kiểm thử (4.2.2) chỉ vỏn vẹn vài dòng và kết thúc cụt ở "Security Testing: Authentication: JWT with expiration".
- **Khảo sát 156 phiếu** vẫn chỉ trình bày kết quả 8/15 câu hỏi, không có biểu đồ, không có minh chứng dữ liệu thô, số liệu vẫn tròn bất thường.
- **"21 showroom toàn quốc"** (số liệu thực của HACOM) vẫn được giữ nguyên, trong khi khảo sát thực tế lại tiến hành tại Hanoicomputer với 3 chi nhánh.
- **Mục 1.4.3 "Giới hạn của đề tài"** hiện chỉ còn phần A liệt kê chức năng đã làm, không còn nội dung nói về giới hạn. Cần đưa lại bản tóm tắt giới hạn tại mục này.

# \* THIẾU SO VỚI ĐỀ CƯƠNG ĐÃ DUYỆT

chưa có: **Class Diagram, Sequence Diagram, Sitemap, User Flow, Wireframe, Mockup, tài liệu SRS, API documentation (Swagger)**.

Class Diagram và Sequence Diagram là bắt buộc khi đã chọn hướng phân tích đối tượng.

Chương 3 đã **bỏ hẳn mục "Thiết kế kiến trúc hệ thống"**, trong khi phần Kết luận khẳng định "áp dụng thành công kiến trúc Layered Architecture" mà không có sơ đồ nào chứng minh, và bảng phân công lại ghi rõ đầu việc "Sơ đồ kiến trúc hệ thống - Trang - Tuần 4".

# \* LỖI TRÌNH BÀY VÀ TÍNH NHẤT QUÁN

- **Đánh số mục sai:** mục 2.1.2 rồi nhảy sang 2.1.3.1-2.1.3.4 (không tồn tại mục 2.1.3); mục 3.1.1.2 nhảy sang 3.1.2.4 (thiếu 3.1.2 và 3.1.2.1-3); phần kiểm thử đánh số 4.2.2 nhưng không có mục 4.2 và 4.2.1.
- **Mâu thuẫn thời hạn đổi/trả hàng:** 15 ngày (mục 1.8.4, 1.11.6, UC27) so với **7 ngày** (Activity Diagram 2.2.1.12, mục D.3).
- **Nhầm lẫn doanh nghiệp:** Tài liệu tham khảo ghi *"Website bán máy tính trực tuyến Hà Nội Computer - https://hacom.vn/"*. HACOM (hacom.vn) và Hà Nội Computer (hanoicomputer.vn) là hai doanh nghiệp khác nhau. Nhóm khảo sát thực tế tại Hanoicomputer thì phải trích dẫn đúng hanoicomputer.vn.
- **Tài liệu tham khảo chỉ có 3 mục, toàn bộ là website**, không đánh số, không có giáo trình hay sách nào về Spring Boot, React, thiết kế cơ sở dữ liệu hay UML. Chưa đạt chuẩn khóa luận tốt nghiệp.
- **Tên người phỏng vấn không nhất quán:** Bảng 1.3 ghi "Bùi Văn Sơn" và "Trần Đức Sơn"; Bảng 1.6 lại ghi "Bùi Văn S" và "Lê Văn M".
- **Activity Diagram 2.2.1.15 (bảo hành) đánh số bước nhảy cóc:** từ 10 sang 16, từ 19 sang 20, từ 23 sang 25.
- **Thiếu Danh mục hình vẽ và Danh mục bảng biểu** (các bảng đã được đánh số từ Bảng 1.1 đến Bảng 3.13 nhưng không có mục lục tương ứng).
- **Phần "Hạn chế" và "Giới hạn kỹ thuật chi tiết" ở Kết luận trùng nội dung khoảng 80%** - nên gộp làm một. Roadmap dài hạn có cả Blockchain và NFT, không liên quan đến đề tài, nên bỏ để tránh bị hỏi vặn khi bảo vệ.
- **Bảng phân công 103 dòng chiếm khoảng 8 trang** trong mục 1.5 - nên rút gọn theo 7 giai đoạn và đưa bản chi tiết xuống Phụ lục.
- **Câu kết luận "đáp ứng đầy đủ các yêu cầu chức năng và phi chức năng"** không đúng với chính phần Hạn chế được liệt kê ngay bên dưới.

# \* YÊU CẦU THỰC HIỆN TIẾP, THEO THỨ TỰ ƯU TIÊN

- **Bổ sung ảnh chụp màn hình hệ thống thật** vào mục 3.3.3 và Chương 4 (tối thiểu 10-12 màn hình, bắt buộc có Build PC và Admin Dashboard), kèm link repository GitHub và/hoặc URL đã deploy.
- **Sửa mã UC02, UC14, UC27**; bổ sung tác nhân Staff vào mục 2.1.3.1 và sơ đồ use case tổng quan.
- **Hợp nhất các schema trùng lặp**, thống nhất kiểu khóa chính/khóa ngoại (nên chọn BIGINT cho toàn bộ), chạy thử script SQL và chụp kết quả làm minh chứng.
- **Rà soát chéo Bảng 1.10 với phần Kết luận:** mọi dòng ghi "Đã triển khai" phải có ảnh chứng minh; nếu không thì chuyển thành "Tính năng mở rộng".
- **Bổ sung Class Diagram và Sequence Diagram** (tối thiểu 3 sequence: Đặt hàng, Thanh toán VNPay, Build PC) cùng sơ đồ kiến trúc hệ thống.
- **Viết lại phần kiểm thử** thành mục 4.2 hoàn chỉnh: bảng test case, kết quả pass/fail, ảnh chụp JUnit/Postman. Đồng thời hạ các yêu cầu phi chức năng xuống mức đo được (ví dụ: 100 người dùng đồng thời đo bằng JMeter) và bỏ PCI DSS, disaster recovery.
- **Sửa các lỗi nhất quán còn lại:** NFR3 (bỏ microservices), thống nhất thời hạn đổi/trả 15 ngày, sửa nhầm lẫn HACOM-Hanoicomputer, bổ sung tài liệu tham khảo học thuật, sửa đánh số mục, thêm danh mục hình và bảng.
