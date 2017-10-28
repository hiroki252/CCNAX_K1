# TÌM HIỂU VỀ MẠNG CĂN BẢNG #
## Network là gì ##
- Mạng máy tính là một hệ thống tập hợp bởi nhiều máy tính, laptop và các thiết bị được kết nối/liên kết với nhau bởi đường truyền vật lý theo một kiến trúc nào đó nhằm trao đổi dữ liệu và chia sẽ tài nguyên cho nhau

## Lợi ích ##
- Sử dụng chung tài nguyên: những tài nguyên của mạng như thiết bị, chương trình và dữ liệu 
- Tăng độ tin cậy vủa hệ thống
- Nâng cao chất lượng và hiệu quả thông tin
- cung cấp sự thống nhất giữ các giữ liệu


## Các loại TOPOLOGY ##

**Star topology**

![](http://www.omnisecu.com/images/basic-networking/star-topology.jpg)

- Mạng dạng hình sao bao gồm một trung tâm và các nút thông tin. Các nút thông tin là các trạm đầu cuối, các máy tính và các thiết bị khác của mạng. Trung tâm của mạng điều phối mọi hoạt động trong mạng với các chức nǎng cơ bản là
- Xác định cặp địa chỉ gửi và nhận được phép chiếm tuyến thông tin và liên lạc với nhau.
- Cho phép theo dõi và sử lý sai trong quá trình trao đổi thông tin.
- Thông báo các trạng thái của mạng…

*Các ưu điểm của mạng hình sao:*

- Hoạt động theo nguyên lý nối song song nên nếu có một thiết bị nào đó ở một nút thông tin bị hỏng thì mạng vẫn hoạt động bình thường.
- Cấu trúc mạng đơn giản và các thuật toán điều khiển ổn định.
- Mạng có thể mở rộng hoặc thu hẹp tuỳ theo yêu cầu của người sử dụng.

*Nhược điểm của mạng hình sao:*

- Khả nǎng mở rộng mạng hoàn toàn phụ thuộc vào khả nǎng của trung tâm . Khi trung tâm có sự cố thì toàn mạng ngừng hoạt động.
- Mạng yêu cầu nối độc lập riêng rẽ từng thiết bị ở các nút thông tin đến trung tâm. Khoảng cách từ máy đến trung tâm rất hạn chế (100 m).

**Mạng hình tuyến (Bus Topology)**

![](https://voer.edu.vn/file/16020)

- Theo cách bố trí hành lang các đường như hình vẽ thì máy chủ (host) cũng như tất cả các máy tính khác (workstation) hoặc các nút (node) đều được nối về với nhau trên một trục đường dây cáp chính để chuyển tải tín hiệu
- Tất cả các nút đều sử dụng chung đường dây cáp chính này. Phía hai đầu dây cáp được bịt bởi một thiết bị gọi là terminator. Các tín hiệu và gói dữ liệu (packet) khi di chuyển lên hoặc xuống trong dây cáp đều mang theo điạ chỉ của nơi đến.
- Loại hình mạng này dùng dây cáp ít nhất, dễ lắp đặt. Tuy vậy cũng có những bất lợi đó là sẽ có sự ùn tắc giao thông khi di chuyển dữ liệu với lưu lượng lớn và khi có sự hỏng hóc ở đoạn nào đó thì rất khó phát hiện, một sự ngừng trên đường dây để sửa chữa sẽ ngừng toàn bộ hệ thống.

**Mạng dạng vòng (Ring Topology)**

![](https://capmanglan.files.wordpress.com/2014/04/download-2.jpg)

- Mạng dạng này, bố trí theo dạng xoay vòng, đường dây cáp được thiết kế làm thành một vòng khép kín, tín hiệu chạy quanh theo một chiều nào đó. Các nút truyền tín hiệu cho nhau mỗi thời điểm chỉ được một nút mà thôi. Dữ liệu truyền đi phải có kèm theo địa chỉ cụ thể của mỗi trạm tiếp nhận.
- Mạng dạng vòng có thuận lợi là có thể nới rộng ra xa, tổng đường dây cần thiết ít hơn so với hai kiểu trên. Nhược điểm là đường dây phải khép kín, nếu bị ngắt ở một nơi nào đó thì toàn bộ hệ thống cũng bị ngừng.


