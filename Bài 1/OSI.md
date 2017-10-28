# MÔ HÌNH OSI #

## Hoàn cảnh ra đời ##

Trước khi mô hình OSI ra đời, việc thiết kế các mạng lưới truyền thông hoàn toàn do những công ty kinh doanh phát triển độc lập. Dưới sự khống chế của luật bản quyền về kỹ thuật, những công ty lớn như IBM, Apple, Novell Inc… đều có những tiêu chuẩn về giao thức truyền thông của riêng mình. Tại thời điểm đó, các mạng truyền thông lớn hỗ trợ nhiều bộ giao thức khác nhau, dẫn đến hệ quả là các thiết bị mạng gặp khó khăn hoặc thậm chí không thể giao tiếp được với nhau.

Mô hình OSI là sự cố gắng của các tổ chức nhằm giải quyết mâu thuẫn của các công ty kinh doanh với mục đích đưa ra được một tiêu chuẩn chung về kĩ thuật mạng truyền thông để các sản phẩm của các công ty kinh doanh có khả năng phối hợp và làm việc được với nhau.

Mô hình OSI (Open Systems Interconnection Reference Model) được thiết kế dựa trên nguyên lý phân tầng, trừu tượng hóa kỹ thuật kết nối và truyền thông giữa các máy tính. Mô hình này được phát triển thành một phần trong kế hoạch kết nối các hệ thống mở (Open Systems Interconnection) do ISO và IUT-T khởi xướng. Một tên gọi khác của nó là mô hình bảy tầng OSI.

**Mô hình OSI**

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/476px-OSI_Model_v1.svg.png)

**Các tầng trong mô hình OSI**

*Application Layer (Tầng ứng dụng)*

Tầng ứng dụng là tầng trên cùng của mô hình OSI gần gũi nhất với người sử dụng, nó cung cấp các dịch vụ cao cấp và các chương trình ứng dụng để người dùng truy xuất đến các dịch vụ mạng như web browser, mail user agent, ftp client…

*Presentation Layer*

Như các bạn đã biết, việc lưu trữ và truyền tải thông tin của một máy tính phụ thuộc vào cấu trúc của CPU và hệ điều hành. Để tránh việc không đồng bộ giữa các kiến trúc, dữ liệu đi xuống từ tầng application khi tới tầng presentation được chuyển về một format chuẩn.

Một số công việc của tầng presentation như:

- Dịch các mã kí tự từ ASCII sang EBCDIC.
- Chuyển đổi kiểu dữ liệu, ví dụ 1 số kiểu integer sẽ được chuyển sang dấu chấm động (floating pont).
- Mã hóa và giải mã dữ liệu để đảm bảo tính bảo mật.

*Session Layer*

Tầng này chịu trách nhiệm thiết lập, quản lý, duy trì và kết thúc các phiên làm việc. Nhiệm vụ cụ thể của tầng session: khi người dùng muốn sử dụng một dịch vụ mạng, trước hết tầng session phải tìm cách thiết lập được một phiên làm việc với nhà cung cấp dịch vụ, trong quá trình sử dụng dịch vụ, nếu vì một lý do nào đó gây mất kếu nối, tầng session phải tìm cách kết nối lại.

*Transport Layer*

Tầng transport đảm bảo truyền thông tin chính xác giữa các thiết bị. Tầng transport sẽ quy định máy tính sẽ sử dụng giao thức nào cho phù hợp với môi trường truyền, ưu tiên tốc độ hay cần đảm bảo tính chính xác… Dữ liệu từ Tầng session đưa xuống sẽ bị phân nhỏ thành các segment, các segment được đánh số thứ tự để bên nhận có thể ghép lại thành dữ liệu chính xác.

*Network Layer*

Tầng network cung cấp các dịch vụ về chọn đường đi, kết nối giữa 2 hệ thống, điều khiển và phân phối luồng dữ liệu truyền tải trên mạng để tránh tắc nghẽn. Tầng network có nhiệm vụ định tuyến dữ liệu từ nơi gửi đến nơi nhận, nó sẽ xác định đường truyền nào là tốt nhất dựa trên cơ sở các điều kiện của mạng, độ ưu tiên dịch vụ. Các segment được đẩy xuống từ tầng transport sẽ được đóng gói thành các packet.

*Data Link Layer*

Tầng data link cung cấp các phương tiện có tính năng và quy trình để truyền dữ liệu giữa các thực thể và phát hiện các lỗi trong quá trình truyền. Cụ thể tầng data link có các nhiệm vụ: thành lập và kết thúc các liên kết logic giữa 2 máy, đóng gói dữ liệu thô từ tầng physical thành các frame và quan trọng nhất là điều khiển và phân tích thông số của các frame, phát hiện lỗi và đưa ra cơ chế sửa lỗi.

*Physical Layer*

Tầng vật lý định nghĩa tất cả các đặc tả về cấu trúc mạng (bus, ring, start…), chuẩn truyền dẫn (RS-485, IEC 1158-2, cáp quang…) phương pháp mã hóa bit (NRZ, Manchester, FSK…), chế độ truyền tải, tốc độ truyền tải, giao diện cơ học (phích cắm, chân cắm…)







