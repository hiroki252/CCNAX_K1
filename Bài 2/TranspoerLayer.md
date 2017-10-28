# TRANSPORT LAYER #

Lớp Transport đảm nhận các nhiệm vụ :

- Truyền tải các session trao đổi dữ liệu của lớp Application qua một kết nối end-to-end
- Thực hiện phân mảnh dữ liệu, đóng gói các PDU của lớp Application ở trên vào các đơn vị dữ liệu lớp 4
- Việc truyền tải của các giao thức lớp Transport có thể theo phương thức connection-oriented hoặc connectionless

Có ai giao thức nổi bật của chồng giao thức TCP/IP hoạt động ở lớp thứ 4 của mô hình OSI là UDP và TCP. Các phần tiếp theo sẽ đi vào đặc điểm của 2 giao thức quan trong này


**UDP**

UDP (User Datagram Protocol) là một giao thức truyền tải connectionless điển hình. Một giao thức connectionless sẽ không thực hiện thao tác xây dựng kết nối trước khi truyền dữ liệu mà thực hiện truyền ngay lập tức khi có dữ liệu cần truyền (gọi là kiểu truyền best effort – truyền tổng lực). Ngoài ra phương thức truyền connectionless cũng không sử dụng các phương pháp đảm bảo độ tin cậy như báo cáo nhận hay điều khiển luồng (flow control). Connectionless không thực hiện các biện pháp đánh số thứ tự cho các đơn vị dữ liệu được truyền…

Với đặc điểm này , UDP sẽ truyền tải rất nhanh cho dữ liệu của lớp ứng dụng, tuy nhiên, hoạt động truyền tải này không có độ tin cậy cao và dễ bị lỗi. Hình 1.7 trình bày cấu trúc của một gói tin UDP ( thường được gọi là UDP Datagram)

![](https://i0.wp.com/tuhocmang.com/wp-content/uploads/2014/07/udp.png)

- Các trường source port và destination port: cho phép định danh một session của một ứng dụng nào đó chạy trên UDP. Có thể coi port chính là địa chỉ của lớp thứ 4
- UDP length: cho biết chiều dài của toàn bộ UDP datagram
- UDP checksum: thực hiện kiểm tra lỗi cho toàn bộ UDP datagram
- Data: dữ liệu lớp trện được đóng gói vào UDP datagram đang xét.


**TCP**

Ngược lại với UDP, TCP (Tranmission Control Protocol) là giao thức truyền tải connection-oriented điển hình .Một giao thức connection-oriented (hướng kết nối) mang các đặc điểm như sau:

- Phải thực hiện thiết lập kết nối với đầu xa trước khi thực hiện truyền dữ liệu. Tiến trình thiết lập kết nối ở TCP được gọi là tiến trình bắt tay 3 bước (threeway handshake)
- Phải thực hiện cơ chế báo nhận khi truyền dữ liệu. Mọi segment được gửi đi đều phải được báo nhận (acknowledge, hay viết gọn là ack). Các segment gửi đi mà không được báo nhận xem như bị lỗi khi truyền và sẽ được thực hiện truyền lại
- Phải thực hiện cơ chế đánh số thứ tự (sequencing) cho các đơn vị dữ liệu được truyền
- Phải thực hiện các cơ chế điều khiển luồng thích hợp (flow control) để tránh nghẽn xảy ra

Ngoài ra , một kết nối TCP có thể được xem như một cặp đường kết nối luận lý kết nối giữa 2 host đầu cuối, mỗi đường phục vụ cho một hướng truyền dữ liệu. Ta nói TCP hỗ trợ truyền tải full duplex.

TCP cũng cung cấp các dịch vụ sửa lỗi , trong đó phía nhận có thể yêu cầu phía gửi truyền lại một segment nào đó

![](https://i1.wp.com/tuhocmang.com/wp-content/uploads/2014/07/h1.png)

- **Source port và destination port (đều dài 16 bit):** được sử dụng để định danh cho session của giao thức nào đó trên lớp ứng dụng đang được truyền tải trong TCP segment đang xét
- **Sequence number (32 bit):** là số thứ tự của byte đầu tiên trong phần data của segment đang xét. Được sử dụng để đãm bảo sắp xếp đúng thứ tự của dữ liệu nhận được tại phía nhận
- **Acknowledge number (32 bit):** số thự tự của byte kế tiếp mà phía nhận mong muốn phía gửi gửi cho mình
- **Header length (4 bit) :**  cho biết chiều dài của TCP header tính theo đơn vị word (32bit)
- **Các bit reserverd (4 bit):** đều được thiết lập bằng 0
- **Các bit control (9 bit):** thực hiện các chức năng điều khiển như thiết lập, kết thúc một session, kiểm soát nghẽn,… Mỗi bit này còn được gọi là một cờ (flag).
- **Window size (16 bit):** số lượng byte mà thiết bị sẵn sàng tiếp nhận
- **Checksum (16 bit):** kiểm tra lỗi cho toàn bộ TCP segment
- **Urgent pointer (16 bit) **: chỉ báo điểm kết thúc của dữ liệu khẩn cấp có tính ưu tiên cao (cần xử lý trước)
- **Options (tối đa 32 bit):** cho phép thêm vào TCP các tính năng khác
- **Data:** dữ liệu lớp trên

**Bắt tay 3 bước**

![](https://i0.wp.com/tuhocmang.com/wp-content/uploads/2014/07/3-buoc.png)

Giả sử host A muốn truyền dữ liệu cho host B thông qua một kết nối TCP. Trước khi thực hiện truyền , host A cần phải thiết lập kết nối TCP với host B việc này được tiến hành thông qua quá trình bắt tay 3 bước:

- Host A gửi cho host B segment đầu tiên , segment này có cờ SYN được bật lên . Giả sử rằng host A thiết lập cho segment này số thứ tự (sequence) là 100. Segment đầu tiên này không chứa phần dữ liệu nên không có phần data, tuy nhiên số lượng byte dữ liệu vẫn được tính là một byte cho hoạt động gửi cờ SYN.
- Host B khi nhận được cờ SYN từ đầu bên kia, thực hiện hồi đáp lại một TCP segment . Segment này có cờ SYN và cờ ACK được bật lên . Giả sử rằng Host B thiết lập cho segment này có số thứ tự là 300.Segment trả lời từ Host B này cũng không có dữ liệu nhưng vẫn được tính là 1 byte cho phần data. Khi hồi đáp host , host B cũng cần phải chỉ rõ trong trường ACK sequence số thứ tự của byte kế tiếp mà nó muốn nhận từ host A. Như đã nói segment SYN do A gửi qua được tính là 1 byte bên B sẽ mong muốn nhận byte tiếp theo là byte thứ 101 từ A , do đó ACK sequence được đánh số là 101.
- Khi host A nhận được segement hồi đáp từ host B , nó gửi segment có bật cờ ACK về lại cho host B. Trường ACK sequence trong segment A gửi B sẽ chỉ rõ số thứ tự của byte tiếp theo mà nó muốn nhận từ B , đó là byte 301.
- Sau khi 3 bước này được hoàn tất , kết nối TCP đã được thiết lập giữa host A và host B, lúc này 2 host đã có thể truyền dữ liệu được với nhau


**ACK báo nhận (Acknowledgement)**

![](https://cdn.itforvn.com/wp-content/uploads/2017/08/image5-1.png)

Để tăng hiệu xuất , việc báo nhận có thể được thực hiện cho nhiều byte một lúc thông qua hiệu chỉnh window size . Ở ví dụ trong hình 1.22, host nhận thưc hiện báo nhận cho từng đợt 3 byte gửi đến từ host gửi bằng cách thiết lập window size = 3

![](https://1.bp.blogspot.com/-jAARhqiwrx0/V_3syo0m3fI/AAAAAAAARt4/ZQFglFUfVU0l7BSAeZF2abWtRVStDUZdgCLcB/s1600/fixed.png)









