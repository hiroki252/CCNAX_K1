# NETWORK LAYER #

Tầng mạng đánh địa chỉ cho các thông điệp và dịch các địa chỉ lôgic và tên sang địa chỉ vật lý. Tầng này còn quyết định tuyến truyền thông từ nguồn đến đích, đồng thời quản lý những vấn đề về giao thông, chẳng hạn như chuyển mạch, định tuyến (routing), và khống chế sự tắc nghẽn của các gói dữ liệu.

## Các đặc tính của Internet Protocol ##

Chức năng lớp internet của mô hình tcp/ip hoàn toàn tương tự như lớp Network  của mô hình OSI. Các thực thể của lớp này thực hiện các nhiệm vụ chính là định tuyến (Routing), tìm đường đi tối ưu từ điểm này đến điểm kia của mạng cho việc di chuyển một loại lưu lượng nào đó . Ngoài ra lớp internet còn cung cấp cách thức truyền tải dữ liệu trên một sơ đồ đã được định tuyến và cung cấp cách thức đánh địa chỉ logic để phục vụ cho tác vụ định tuyến

##  IP header ##

![](http://media.techtarget.com/digitalguide/images/Misc/100504_cisco_figure_3_12b.gif)

- **Version (4 bit ) :** trường này cho biết version của giao thức IP đang sử dụng. Hiện nay chỉ có hai version của giao thức IP là 4 và 6. Header hình trên là giao giao thức IPv4 nên giá trị của trường này luôn dược thiết lập là 4.
- **IP Header Length (4 bit) **: trường này cho biết kích thước tính theo đơn vị word – 32 bit của IP Header.
- **Service Type (8 bit) :** trường này được sử dụng cho mục đích đánh dấu dữ liệu (marking) phục vụ cho tác vụ QoS với các gói tin IP . QoS (Quality of Service) là tập hợp các kĩ thuật cho phép cấp phát các tài nguyên một cách thích hợp cho các loại dữ liệu khác nhau, từ đó có thể đảm bảo chất lượng dịch vụ mạng cho các loại dữ liệu này .
-** Packet Length (16 bit) **: cho biết chiều dài tính theo byte của toàn bộ gói tin IP.
- **Các trường Identification, Flag và Fragment Offset:** được sử dụng cho mục đích phân mảnh gói tin IP
- **Time to Live (TTL) (8 bit) :** được sử dụng để chống loop gói tin IP khi xảy ra lỗi định tuyến trên sơ đồ mạng, Cứ mỗi khi gói tin IP đi qua một node lớp 3 (ví dụ: Router), giá trị TTL này lại được giảm đi 1 đơn vị . Khi TTL = 0, gói tin sẽ bị loại bỏ.
- **Protocol (8 bit) :** trường này được sử dụng để nhận dạng giao thức nào đang được truyền tải trong phần data của gói tin IP . Các giao thức truyền tải bởi giao thức IP đều được gán cho một giá trị Protocol-ID được quy định bởi IANA (Internet Assigned Number Authority), là tổ chức quốc tế quản lý địa chỉ IP và số hiệu mạng.

**Ví dụ :** nếu Protocol-id = 6 , phần data của gói tin IP đang đóng gói một TCP segment; nếu protocol-id = 17 , phần data của gói tin IP đang đóng gói một UDP datagram; nếu protocol-id = 89 , phần data của một gói tin IP đang đóng gói một gói tin của giao thức định tuyến OSPF,v.v..

Tương tự như trường port của giao thức TCP và UDP, trường protocol cho phép một thiết bị lớp 3 nhận dạng được giao thức được truyền tải bởi giao thức IP mà không cần phải mở gói IP ra để kiểm tra

- **Header checksum (8 bit) :** trường này được sử dụng cho việc kiểm tra lỗi của IP Header
- **Các trường Source Address (32 bit) và Destination Address (32 bit) :** cho biết địa chỉ của thiết bị gửi đi gói IP và thiết bị đích đến của gói IP đang xét .
- **Options và Padding :** trường option cho phép thêm vào tính năng mới cho giao thức IP. Cấu trúc của gói IP quy định option phải là bội số của 32 bit nên nếu option không đủ số bit , các bit padding sẽ được thêm vào để đạt được yêu cầu này .

## Định dạng Địa chỉ IP ##

- Địa chỉ IP gồm 32 bit nhị phân , chia thành 4 cụm 8 bit (gọi là các octet). Các octet được biểu diễn dưới dạng thập phân và được ngăn cách bằng các dấu chấm
- Địa chỉ IP được chia thành 2 phần : phần mạng (network) và phần host.

![](https://1.bp.blogspot.com/-ZpLb8_NTw8c/VsfhfALNkUI/AAAAAAAAAX8/q88QC-LXAkM/s1600/cautrucIP.png)
 
- **Subnet mask**: Subnet mask là một dãy nhị phân dài 32 bit đi kèm với một địa chỉ IP để cho phép xác định được network mà IP này thuộc về. Điều này được thực hiện bằng AND địa chỉ IP với subnet-mask theo từng bit mộtVí dụ : Xét địa chỉ IP 192.168.1.1 với subnet-mask là 255.255.255.0. Để xác định địa chỉ mạng của đia chỉ này , thực hiện AND 192.168.1.1 với 255.255.255.0.

![](https://engisv.com/wp-content/uploads/2017/02/subnet-1.png)

Để đơn giản, chỉ cần nhớ rằng : phần network của địa chỉ mạng chạy đến, các bit 1 của subnet-mask chạy đến đó; ứng với các bit phần host của địa chỉ , các bit của subnet mask nhận giá trị bằng 0


- **Prefix – length**: Một cách khác để hiển thị địa chỉ IP là sử dụng số prefix-length. Số prefix-length là số bit mạng trong một địa chỉ IP . Giá trị này được viết ngay sau địa chỉ IP và ngăn cách bởi dấu “/”

## Địa chỉ Private và Public ##

- **Private:** Chỉ được sử dụng trong mạng nội bộ (mạng LAN), không được định tuyến trên môi trường Internet. Có thể được sử dụng lặp lại trong các mạng LAN khác nhau .
- **Public:** là địa chỉ IP sử dụng cho các gói tin đi trên môi trường Internet, được định tuyến trên môi trường Internet. Địa chỉ public phải là duy nhất cho mỗi host tham gia vào Internet.

- Dải địa chỉ private (được quy định trong RFC 1918):

Lớp A:         10.x.x.x

Lớp B:          172.16.x.x -> 
172.31.x.x

Lớp C:          192.168.x.x

- Kỹ thuật NAT (Network Address Translation) được sử dụng để chuyển đổi giữa IP private và IP public
- Ý nghĩa của địa chỉ private: được sử dụng để bảo tồn địa chỉ IP public

## Các lớp địa chỉ IP ##

![](https://image.slidesharecdn.com/network-1206754309287969-2-130903092039-/95/network-12067543092879692-37-638.jpg?cb=1378200219)

**Lớp A:**

- Địa chỉ lớp A sử dụng một otet đầu làm phần mạng, ba octet sau làm phần host
- Bit đầu của một địa chỉ lớp A luôn được giữ là 0.
- Các địa chỉ lớp mạng lớp A gồm : 1.0.0.0 -> 126.0.0.0.
- Mạng 127.0.0.0 được sử dụng làm loopback
- Phần host có 24 bit => mỗi mạng lớp A có (224 – 2) host.

**Lớp B**

- Địa chỉ lớp B sử dụng hai octet đầu làm phần mạng , hai octet sau làm phần host.
- Hai bit đầu của một địa chỉ lớp B luôn được giữ là 1 0
- Các địa chỉ mạng lớp B gồm : 128.0.0.0 -> 191.255.0.0 . Có tất cả 214 mạng trong lớp B.
- Phần host dài 16 bit do đó một mạng lớp B có (216 – 2) host.

**Lớp C**

- Địa chỉ lớp C sử dụng 3 octet đầu làm phần mạng , một octet sau làm phần host.
- Ba bit đầu của một địa chỉ lớp C luôn được giữ là 1 1 0.
- Các địa chỉ mạng lớp C gồm : 192.0.0.0 -> 223.255.255.0 . Có tất cả 221 mạng trong lớp C.
- Phần host dài 8 bit do đó có một mạng lớp C có (28 – 2) = 254 host

**Lớp D**

Gồm các địa chỉ thuộc dải: 244.0.0.0 -> 239.255.255.255

- Được sử dụng để làm địa chỉ multicast.
- Ví dụ : 224.0.0.5 dùng cho OSPF; 224.0.0.9 dùng cho RIPv2

**Lớp E**

- Từ 240.0.0.0 trở đi .
- Được sử dụng cho mục đích dự phòng

**Lưu Ý**

- Các lớp địa chỉ IP có thể sử dụng để đặt cho các host là các lớp A,B,C
- Để thuận tiện cho việc nhận diện một địa chỉ IP thuộc lớp nào , có thể quan sát octet đầu của địa chỉ, nếu octet này có giá trị nằm trong khoảng :

1 -> 126:          Địa chỉ lớp A

128 -> 191:     Địa chỉ lớp B

192 -> 223:     Đạ chỉ lớp C

224 -> 239:     Địa chỉ lớp D

240 -> 255:     Địa chỉ lớp E

## Subnet là gì ##

Khi ta chia một Network ra thành nhiều Network nhỏ hơn thì các Network nhỏ này được gọi là Subnet. Như ta đã biết mạng Internet sử dụng địa chỉ IPv4 32 bit và phân chia ra các lớp A,B,C,D , tuy nhiên, với một hệ thống địa chỉ như vậy việc quản lý vẫn rất khó khăn

















