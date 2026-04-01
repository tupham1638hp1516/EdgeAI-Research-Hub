**## Các khái niệm cần tìm hiểu:**



tập dữ liệu SNMP-MIB/ SNMP-MIB Dataset

các cuộc tấn công làm ngập lụt Từ chối dịch vụ (DoS)/ DoS flooding attacks

Giao thức Quản lý Mạng Đơn giản (SNMP)/ Simple Network Management

Protocol (SNMP)

&#x20;Cơ sở Thông tin Quản lý (MIB)/  Management

Information Base (MIB)

Brute Force attack

Interface, IP, TCP and ICMP

&#x20;Intrusion Detection System (IDS); IDS evaluation dataset

Network Anomaly

common Types of DoS Flooding Attack:

1\) TCP-SYN Attack

2\) UDP Flood Attack

3\) ICMP-ECHO Attack

4\) HTTP Flood Attack

5\) Slowloris Attack

6\) Slowpost Attack

User Datagram Protocol (UDP)





\# Các nhà nghiên cứu đang gặp khó khăn do thiếu hụt các tập dữ liệu thực tế. Hầu hết các tập dữ liệu hiện có đều phụ thuộc vào các phương pháp tiếp cận dựa trên mô phỏng, vốn không thể thể hiện chính xác và đúng bản chất của các kịch bản xâm nhập và bất thường mạng. Ta có thể hiểu DoS flooding attacks là các cuộc tấn công nhằm bơm một lượng thông tin rác khổng lồ làm tắc nghẽn hệ thống mạng, và để ngăn chặn các cuộc tấn công này thì ta có IDS để phát hiện các cuộc tấn công. Vấn đề được đặt ra ở đây là các dataset hiện có không đủ khả năng để mô tả lại các cuộc tấn công ngoài đời thực.Vì vậy, việc tạo ra các tập dữ liệu thực tế là rất quan trọng vì nó cho phép đánh giá chính xác và thích hợp các kỹ thuật phát hiện



Thay vì soi xét từng gói tin (packet) siêu nhỏ, việc này cực kỳ tốn tài nguyên và làm chậm hệ thống. Nhóm tác giả chọn cách tiếp cận theo hướng thống kê thông qua SNMP và MIB.



SNMP Là giao thức tầng ứng dụng dùng để quản lý và giám sát các thiết bị mạng (Router, Switch, Server...).

\# Vai trò: Nó đóng vai trò thu thập thông tin từ các thiết bị, phát hiện các thông số bất thường



MIB Là một cơ sở dữ liệu nằm trong thiết bị mạng, lưu trữ các biến số phản ánh trạng thái của thiết bị đó.

\# Mỗi khi có một hoạt động bất kỳ, các biến số trong MIB sẽ thay đổi. Ví dụ: Nếu bị tấn công từ chối dịch vụ (DoS), số lượng gói tin ICMP hoặc lỗi IP sẽ tăng vọt.



**### Vậy thành quả của tác giả có thể hiểu là:**



Thiết lập giải pháp khai thác dữ liệu thống kê từ SNMP-MIB để thay thế việc phân tích gói tin thô nặng nề. Họ đã tinh lọc và định danh bộ 34 biến MIB nhạy cảm nhất trong hàng ngàn biến số MIB có sẵn qua thuật toán đo độ lợi thông tin, giúp tối ưu hóa khả năng nhận diện tấn công đa tầng. Từ đó, nhóm xây dựng một mô hình thực nghiệm thực tế và bộ dữ liệu 4998 bản ghi chất lượng cao, chứng minh khả năng phát hiện xâm nhập một cách nhẹ nhàng và hiệu quả. Cuối cùng, nghiên cứu xác lập quy trình lấy mẫu 15 giây/lần là khoảng thời gian tối ưu để đảm bảo phát hiện nhanh các cuộc tấn công hiện đại mà không gây gánh nặng cho thiết bị mạng. Thành quả của họ là tạo ra phương pháp luận và dữ liệu thực chứng.



**## Đi vào định nghĩa:**



1\.**Bất thường mạng**:

Bất thường mạng là sự sai lệch so với hành vi bình thường của mạng khi có bất kỳ kẻ xâm nhập nào trong mạng hoặc do quá tải mạng. Những sự kiện bất thường này làm gián đoạn chức năng bình thường của các dịch vụ mạng. Hành vi mạng bình thường có thể được đặc trưng bởi nhiều yếu tố khác nhau, chẳng hạn như loại dữ liệu mạng cần đo lường, khối lượng lưu lượng của mạng và loại ứng dụng đang chạy trên mạng. Hơn nữa, Hệ thống phát hiện xâm nhập (IDS) là quá trình giám sát bất kỳ hoạt động bất thường nào xảy ra trong hệ thống máy tính hoặc mạng và so sánh nó với một sự kiện bình thường để xác định các dấu hiệu xâm nhập. Xâm nhập đề cập đến một hoạt động độc hại nhằm phá vỡ tính bảo mật, tính toàn vẹn và tính sẵn sàng của các thành phần mạng trong nỗ lực phá vỡ chính sách bảo mật của mạng



**2.Các cuộc tấn công mạng:**

Trọng tâm công việc của tác giả là phát hiện các cuộc tấn công; cụ thể là tấn công làm Dos flooding và Brute Force Attack.



Những kẻ tấn công sẽ làm ngập lụt một máy chủ (nạn nhân) bằng một lượng lớn lưu lượng truy cập để tiêu thụ tất cả các tài nguyên của máy chủ (CPU, bộ nhớ và băng thông) và ngăn nó xử lý các yêu cầu hợp pháp của người dùng. Kết quả là, điều này tạo ra sự tắc nghẽn mạng trên hệ thống mục tiêu, do đó làm gián đoạn các hoạt động bình thường và các dịch vụ của nạn nhân trở nên không khả dụng.



Một phiên bản khác của tấn công DoS là Distributed Denial of Service (DDoS). Nó gửi một lượng lớn lưu lượng truy cập đến nạn nhân bằng cách xâm phạm các máy không an toàn trong mạng gây ra sự cố từ chối dịch vụ.

Dưới đây là một số ví dụ về DoS flooding attack:



**Tấn công TCP-SYN:** Tấn công làm ngập lụt TCP SYN khai thác lỗ hổng của cơ chế bắt tay ba bước \[Đồng bộ hóa (SYN), SYN-ACK (Xác nhận), và ACK] được sử dụng giữa máy chủ (host) và máy chủ (server) để thiết lập kết nối.

&#x20;Trong cuộc tấn công, kẻ tấn công gửi các gói SYN với địa chỉ IP nguồn không tồn tại đến máy chủ.

&#x20;Máy chủ phản hồi lại một yêu cầu SYN bằng cách gửi SYN ACK, lưu trữ thông tin yêu cầu trong ngăn xếp bộ nhớ và chờ gói ACK từ máy khách.

&#x20;Trong khi máy chủ chờ gói ACK từ máy khách, yêu cầu vẫn còn trong ngăn xếp bộ nhớ.

&#x20;Máy chủ sẽ không nhận được các gói ACK vì địa chỉ IP nguồn đã giả mạo địa chỉ IP.

&#x20;Nếu kẻ tấn công gửi nhiều yêu cầu SYN trong những khoảng thời gian rất ngắn, các yêu cầu sẽ lấp đầy toàn bộ ngăn xếp bộ nhớ và sau đó tài nguyên của máy chủ sẽ cạn kiệt, khiến máy chủ không thể phản hồi thêm các yêu cầu từ người dùng hợp pháp



**Tấn công UDP Flood:** Loại tấn công này được gây ra bằng cách gửi hoặc làm ngập lụt các gói UDP hướng tới các cổng ngẫu nhiên của máy chủ.

&#x20;Máy chủ mở gói tin và không tìm thấy gì trong đó, sau đó gửi lại gói tin không thể truy cập (unreachable) về đích.

&#x20;Bởi vì lượng lớn các gói UDP này, tài nguyên của nạn nhân (băng thông) sẽ bị cạn kiệt và có thể bận rộn phục vụ các yêu cầu này.

&#x20;Điều này dẫn đến sự không khả dụng cho những người dùng hợp pháp.

&#x20;Một cuộc tấn công ngập lụt UDP có thể hiệu quả hơn trong các mạng nhỏ hơn vì kích thước của các gói UDP là khổng lồ



**Tấn công ICMP-ECHO:** Tấn công này tập trung vào việc làm ngập lụt băng thông của nạn nhân.

&#x20;Theo giao thức ICMP, khi một thiết bị trên mạng nhận được một yêu cầu “ping”, nó sẽ trả lời lại địa chỉ IP nguồn bằng một tin nhắn thông báo về trạng thái của thiết bị nhận.

&#x20;Trong cuộc tấn công này, kẻ tấn công chế tạo một số lượng lớn các gói ICMP với địa chỉ IP nguồn giả mạo giống với địa chỉ IP của nạn nhân và gửi chúng thông qua các yêu cầu ICMP echo tới một địa chỉ quảng bá (broadcast).

&#x20;Tất cả các thiết bị trên mạng đã nhận được những yêu cầu này sẽ trả lời bằng tin nhắn gửi lại cho nạn nhân.

&#x20;Cuối cùng, tất cả các tin nhắn trả lời sẽ làm cạn kiệt tài nguyên của nạn nhân.

&#x20;Sức mạnh của một cuộc tấn công ICMP-ECHO phụ thuộc vào số lượng thiết bị nhận được các yêu cầu và tốc độ gói tin tấn công



**Tấn công HTTP Flood:** Tấn công này còn được gọi là tấn công làm ngập lụt HTTP GET/POST.

&#x20;Nó cũng được coi là một cuộc tấn công không giả mạo.

&#x20;Trong cuộc tấn công này, kẻ tấn công nhằm mục đích tấn công các máy chủ web và các ứng dụng để tiêu thụ một lượng lớn tài nguyên của nạn nhân.

&#x20;Những kẻ tấn công gửi một lượng lớn các yêu cầu HTTP hợp lệ (get/post) đến một nạn nhân, như thể hiện trong Hình 3.

&#x20;Những yêu cầu như vậy thường được gửi bởi mạng botnet, nơi mỗi bot có thể tạo ra một lượng lớn các yêu cầu hợp lệ (thường là hơn 10 yêu cầu một giây).

&#x20;Tại đây, tốc độ yêu cầu kết nối phiên từ những kẻ tấn công cao hơn tốc độ yêu cầu kết nối phiên từ những người dùng bình thường.

&#x20;Một cuộc tấn công làm ngập lụt HTTP có thể là một trong những mối đe dọa không dùng lỗ hổng lớn nhất mà các máy chủ web có thể gặp phải vì rất khó để phân biệt giữa lưu lượng HTTP độc hại và lưu lượng HTTP bình thường



**Tấn công Slowloris:** Cuộc tấn công này còn được gọi là tấn công Slow Header.

Trong cuộc tấn công, kẻ tấn công với một địa chỉ IP không giả mạo sẽ gửi các phiên có yêu cầu khối lượng công việc cao.

&#x20;Các yêu cầu này là các yêu cầu HTTP header một phần, cập nhật rất chậm, phát triển nhanh chóng và liên tục, và không bao giờ đóng lại.

&#x20;Cuộc tấn công tiếp tục cho đến khi tất cả các socket kết nối có sẵn bị các yêu cầu này chiếm dụng, và máy chủ web trở nên không khả dụng đối với bất kỳ kết nối hợp pháp nào.

&#x20;Cuộc tấn công Slowloris có thể khiến máy chủ web gặp sự cố bằng cách sử dụng một số lượng hạn chế các máy tính hoặc thậm chí chỉ một máy tính duy nhất mà không gây ra bất kỳ tác dụng phụ nào đối với các dịch vụ và cổng khác



**Tấn công Slowpost:** Cuộc tấn công này còn được gọi là Slow Request Bodies và xuất hiện lần đầu tiên vào năm 2010.

&#x20;Cuộc tấn công này tương tự như một cuộc tấn công Slowloris ở chỗ những kẻ tấn công gửi các phiên với các yêu cầu khối lượng công việc cao để đánh sập các máy chủ web.

&#x20;Trong cuộc tấn công này, kẻ tấn công gửi một yêu cầu HTTP header hoàn chỉnh, định nghĩa trường độ dài nội dung (content length) trong phần thân thông điệp POST, giống như yêu cầu này được gửi cho lưu lượng truy cập bình thường.

&#x20;Dữ liệu sau đó được gửi để lấp đầy phần thân thông báo với tốc độ một byte mỗi hai phút, và đồng thời máy chủ vẫn chờ đợi mỗi phần thân thông báo được hoàn thành, dẫn đến việc từ chối các dịch vụ web



**Các bước để tạo dataset:**



Bước 1: Thiết lập môi trường mạng thực: Tác giả xây dựng một mạng cục bộ biệt lập với Internet để đảm bảo tính chân thực, bao gồm 1 bộ định tuyến (router), 2 bộ chuyển mạch (switches) và 2 mạng con. Mạng con thứ nhất có 1 máy tính đóng vai trò Attacker; mạng con thứ hai có 1 máy tính làm Victim.

Bước 2: Tạo lưu lượng mạng bình thường (Normal Traffic Generation): Sử dụng phần mềm LanTrafficV2 cài đặt trên các máy tính để tự động tạo ra các luồng dữ liệu (TCP, UDP, ICMP) qua lại giữa 2 mạng con. Lưu lượng bình thường được duy trì ở tốc độ lên tới 50 Mbps để giả lập một mạng đang hoạt động thực tế.

Bước 3: Phát động các cuộc tấn công: Máy Attacker sử dụng hàng loạt công cụ mã nguồn mở để tấn công máy Victim bằng các kịch bản khác nhau

Bước 4: Trong khi các cuộc tấn công đang diễn ra, một chương trình bằng ngôn ngữ Java sẽ "hỏi" bộ định tuyến cứ mỗi 15 giây một lần để chép lại 34 chỉ số MIB. Con số 15 giây được chọn vì nó đủ nhanh để bắt được dấu vết tấn công nhưng không làm máy móc bị quá tải.



**### Cách thức hoạt động:**



1\. Chiến lược theo dõi/ Hay Tại sao lại chọn 34 biến?

Tác giả chọn bộ định tuyến (router) làm điểm thu thập dữ liệu vì đây là nút giao thông chính mà mọi luồng dữ liệu đều phải đi qua.

Không có một thông số đơn lẻ nào đủ để phát hiện mọi loại tấn công.

Thay vì theo dõi toàn bộ hệ thống gây quá tải, tác giả chỉ chọn lọc ra 34 thông số (biến MIB) quan trọng và nhạy cảm nhất.

Phân bổ: 34 thông số này được chia vào 5 nhóm cốt lõi (Interface, IP, ICMP, TCP, UDP) nhằm bao quát mọi hoạt động của mạng, từ việc đếm dữ liệu ra/vào, định tuyến đường đi, cho đến ghi nhận các lỗi kết nối.

2\. Dấu hiệu nhận biết

Dữ liệu của 34 thông số này được đo bằng "bộ đếm 32" – tức là một dạng thông số chỉ cộng dồn liên tục tiến lên phía trước (từ 0 đến mức tối đa rồi mới quay vòng lại về 0).

Cách phát hiện kẻ tấn công: Các thông số này chịu ảnh hưởng trực tiếp từ lưu lượng truyền tải trên mạng. Ở trạng thái bình thường, các con số này sẽ tăng lên một cách đều đặn. Tuy nhiên, khi có các cuộc tấn công ngập lụt, kẻ gian sẽ bơm một lượng dữ liệu rác khổng lồ vào hệ thống. Hệ quả là các thông số đo lường này sẽ gia tăng với tốc độ đột biến. Bằng cách theo dõi tốc độ tăng bất thường của 34 thông số này, hệ thống có thể nhận diện được ngay khi nào mạng đang bị tấn công.

