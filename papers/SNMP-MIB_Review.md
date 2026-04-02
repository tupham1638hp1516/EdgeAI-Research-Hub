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



**## Đi vào định nghĩa:**



1\.**Bất thường mạng**:

Bất thường mạng là sự sai lệch so với hành vi bình thường của mạng khi có bất kỳ kẻ xâm nhập nào trong mạng hoặc do quá tải mạng. Những sự kiện bất thường này làm gián đoạn chức năng bình thường của các dịch vụ mạng. Hành vi mạng bình thường có thể được đặc trưng bởi nhiều yếu tố khác nhau, chẳng hạn như loại dữ liệu mạng cần đo lường, khối lượng lưu lượng của mạng và loại ứng dụng đang chạy trên mạng. Hơn nữa, Hệ thống phát hiện xâm nhập (IDS) là quá trình giám sát bất kỳ hoạt động bất thường nào xảy ra trong hệ thống máy tính hoặc mạng và so sánh nó với một sự kiện bình thường để xác định các dấu hiệu xâm nhập. Xâm nhập đề cập đến một hoạt động độc hại nhằm phá vỡ tính bảo mật, tính toàn vẹn và tính sẵn sàng của các thành phần mạng trong nỗ lực phá vỡ chính sách bảo mật của mạng



**2.Các cuộc tấn công mạng:**

Trọng tâm công việc của tác giả là phát hiện các cuộc tấn công; cụ thể là tấn công làm Dos flooding và Brute Force Attack.



Những kẻ tấn công sẽ làm ngập lụt một máy chủ (nạn nhân) bằng một lượng lớn lưu lượng truy cập để tiêu thụ tất cả các tài nguyên của máy chủ (CPU, bộ nhớ và băng thông) và ngăn nó xử lý các yêu cầu hợp pháp của người dùng. Kết quả là, điều này tạo ra sự tắc nghẽn mạng trên hệ thống mục tiêu, do đó làm gián đoạn các hoạt động bình thường và các dịch vụ của nạn nhân trở nên không khả dụng.



Một phiên bản khác của tấn công DoS là Distributed Denial of Service (DDoS). Nó gửi một lượng lớn lưu lượng truy cập đến nạn nhân bằng cách xâm phạm các máy không an toàn trong mạng gây ra sự cố từ chối dịch vụ.

Dưới đây là một số ví dụ về DoS flooding attack:



***# Tấn công vào lớp giao vận:***



**Tấn công TCP-SYN:**

Cơ chế : Kẻ tấn công gửi hàng loạt gói tin SYN với địa chỉ IP giả mạo. Máy chủ phản hồi SYN-ACK và đưa kết nối vào trạng thái "Nửa mở" (Half-open) trong hàng đợi Backlog. Vì IP nguồn là giả, máy chủ không bao giờ nhận được gói ACK cuối cùng.

Hệ quả: Cạn kiệt Backlog Queue và bộ nhớ RAM. CPU bị bắt làm quá mức



**Tấn công UDP Flood:**

Cơ chế: Khác với TCP, UDP là giao thức phi kết nối. Vì UDP không cần thiết lập kết nối, các kẻ tấn công rất dễ gửi chúng đi, thậm chí là hàng triệu. Điều đáng lo ở đây là các gói UDP đó thường được gửi vào các cổng không có thật hoặc không có ứng dụng nào ở đó. Máy chủ thì lại phải phản hồi rất lâu: mở gói tin, kiểm tra ứng dụng, gửi một gói tin ICMP mới.

Hệ quả: Khi có hàng triệu gói UDP vô nghĩa, máy chủ dùng hết băng thông và CPU chỉ để gửi các gói ICMP thông báo ngược lại.



***# Tấn công vào Lớp mạng:***



**Tấn công ICMP-ECHO:**

Cơ chế: Ngược lại với UDP Flood, kẻ tấn công chế tạo một số lượng lớn các gói ICMP với địa chỉ IP nguồn giả mạo giống với địa chỉ IP của nạn nhân và gửi chúng thông qua các yêu cầu ICMP echo tới một broadcast. Tất cả các thiết bị trên mạng đã nhận được những yêu cầu này sẽ trả lời bằng tin nhắn gửi lại cho nạn nhân,

Hệ quả: Làm cạn kiệt tài nguyên của nạn nhân.



***# Tấn công vào Lớp ứng dụng:***



**Tấn công HTTP Flood:** Những kẻ tấn công gửi một lượng lớn các yêu cầu HTTP hợp lệ (get/post) đến một nạn nhân. Những yêu cầu như vậy thường được gửi bởi mạng botnet, nơi mỗi bot có thể tạo ra một lượng lớn các yêu cầu hợp lệ (thường là hơn 10 yêu cầu một giây). Tại đây, tốc độ yêu cầu kết nối phiên từ những kẻ tấn công cao hơn tốc độ yêu cầu kết nối phiên từ những người dùng bình thường. Và vì tốc độ đến lớn hơn tốc độ xử lý, hàng đợi sẽ dài ra vô hạn.

Hệ quả: CPU bị ép làm việc ở mức cao, RAM bị chiếm dụng, website bị treo.



**Tấn công Slowloris:** Trong giao thức HTTP, khi một Client gửi yêu cầu đến máy chủ Server, nó phải gửi một bộ HTTP Header hoàn chỉnh để máy chủ biết cần phải làm gì. Máy chủ sẽ mở một Socket và giữ nó mở cho đến khi nhận được toàn bộ Header. Tương tự http flood, cách tấn công này không nhắm vào lỗ hổng. Kẻ tấn công sẽ mở nhiều kết nối đến máy chủ web nhưng lại chỉ gửi các Http Header không hoàn chỉnh, thường thì chỉ vài dòng. Vì chúng vẫn đang ở trạng thái gửi dở, Slowris có thể chiếm dụng hàng nghìn kết nối, khiến máy chủ không còn socket nào trống.

Hậu quả: Dịch vụ web bị tê liệt, không còn khả dụng với các kết nối hợp pháp khác.



**Tấn công Slowpost:** Nếu Slowloris có thể được ngăn chặn bằng việc kiểm tra cấu trúc Header, Slowpost lại có cách tinh vi hơn. Kẻ tấn công gửi một yêu cầu HTTP POST hoàn toàn hợp lệ về mặt cấu trúc (đầy đủ Header). Tuy nhiên, điểm mấu chốt nằm ở trường Content-Length được khai báo một con số rất lớn. Thay vì gửi toàn bộ dữ liệu ngay lập tức, kẻ tấn công chỉ gửi từng byte một sau những khoảng thời gian nghỉ rất dài. Máy chủ buộc phải giữ kết nối luôn ở trạng thái mở để chờ đợi phần thân thông điệp hoàn tất.

Hậu quả: Toàn bộ Connection Pool của máy chủ web sẽ bị lấp đầy bởi các yêu cầu đang chờ xử lý, dẫn tới không còn khả năng tiếp nhận bất kỳ yêu cầu mới nào từ người dùng thực tế, gây ra tình trạng từ chối dịch vụ hoàn toàn.



**### Khó khăn:** Các nhà nghiên cứu đang gặp khó khăn do thiếu hụt các tập dữ liệu thực tế. Hầu hết các tập dữ liệu hiện có đều phụ thuộc vào các phương pháp tiếp cận dựa trên mô phỏng, vốn không thể thể hiện chính xác và đúng bản chất của các kịch bản xâm nhập và bất thường mạng. Ta có thể hiểu DoS flooding attacks là các cuộc tấn công nhằm bơm một lượng thông tin rác khổng lồ làm tắc nghẽn hệ thống mạng, và để ngăn chặn các cuộc tấn công này thì ta có IDS để phát hiện các cuộc tấn công. Vấn đề được đặt ra ở đây là các dataset hiện có không đủ khả năng để mô tả lại các cuộc tấn công ngoài đời thực.Vì vậy, việc tạo ra các tập dữ liệu thực tế là rất quan trọng vì nó cho phép đánh giá chính xác và thích hợp các kỹ thuật phát hiện



Thay vì soi xét từng gói tin (packet) siêu nhỏ, việc này cực kỳ tốn tài nguyên và làm chậm hệ thống. Nhóm tác giả chọn cách tiếp cận theo hướng thống kê thông qua SNMP và MIB.



SNMP Là giao thức tầng ứng dụng dùng để quản lý và giám sát các thiết bị mạng (Router, Switch, Server...).

\# Vai trò: Nó đóng vai trò thu thập thông tin từ các thiết bị, phát hiện các thông số bất thường



MIB Là một cơ sở dữ liệu nằm trong thiết bị mạng, lưu trữ các biến số phản ánh trạng thái của thiết bị đó.

\# Mỗi khi có một hoạt động bất kỳ, các biến số trong MIB sẽ thay đổi. Ví dụ: Nếu bị tấn công từ chối dịch vụ (DoS), số lượng gói tin ICMP hoặc lỗi IP sẽ tăng vọt.



**### Thành quả của tác giả là:**



Thiết lập giải pháp khai thác dữ liệu thống kê từ SNMP-MIB để thay thế việc phân tích gói tin thô nặng nề. Họ đã tinh lọc và định danh bộ 34 biến MIB nhạy cảm nhất trong hàng ngàn biến số MIB có sẵn qua thuật toán đo độ lợi thông tin, giúp tối ưu hóa khả năng nhận diện tấn công đa tầng. Từ đó, nhóm xây dựng một mô hình thực nghiệm thực tế và bộ dữ liệu 4998 bản ghi chất lượng cao, chứng minh khả năng phát hiện xâm nhập một cách nhẹ nhàng và hiệu quả. Cuối cùng, nghiên cứu xác lập quy trình lấy mẫu 15 giây/lần là khoảng thời gian tối ưu để đảm bảo phát hiện nhanh các cuộc tấn công hiện đại mà không gây gánh nặng cho thiết bị mạng. Thành quả của họ là tạo ra phương pháp luận và dữ liệu thực chứng.



**# Ta sẽ đi sâu vào quá trình nghiên cứu của tác giả:**



Trong mạng máy tính, một chỉ số tăng vọt có thể do nhiều nguyên nhân khác nhau—cả bình thường lẫn độc hại, do đó không có biến đơn lẻ nào có khả năng nắm bắt tất cả các bất thường trên mạng.
Do đó, tác giả tập trung vào việc sử dụng các biến SNMP-MIB hiệu quả để phát hiện bất thường chính xác hơn.



**## Cách thức hoạt động:**



1\. Chiến lược của tác giả

Tác giả chọn bộ định tuyến (router) làm điểm thu thập dữ liệu vì đây là nút giao thông chính mà mọi luồng dữ liệu đều phải đi qua.

Thay vì theo dõi toàn bộ hệ thống gây quá tải, tác giả chỉ chọn lọc ra 34 thông số (biến MIB) quan trọng và nhạy cảm nhất.

Phân bổ: 34 thông số này được chia vào 5 nhóm cốt lõi (Interface, IP, ICMP, TCP, UDP) nhằm bao quát mọi hoạt động của mạng, từ việc đếm dữ liệu ra/vào, định tuyến đường đi, cho đến ghi nhận các lỗi kết nối.

Bằng các cuộc khảo sát toàn diện, tác giả đã chọn các biến này trong số các biến MIB khác trong các nhóm vì chúng bị ảnh hưởng nhiều hơn bởi lưu lượng tấn công, nơi các biến này liên tục được cập nhật với lưu lượng vào và ra trên mạng; do đó, chúng có thể hiệu quả hơn cho việc phát hiện tấn công.



2\. Dấu hiệu nhận biết



Dữ liệu của 34 thông số này được đo bằng "bộ đếm 32" – tức là một dạng thông số chỉ cộng dồn liên tục tiến lên phía trước (từ 0 đến mức tối đa rồi mới quay vòng lại về 0).

Cách phát hiện kẻ tấn công: Các thông số này chịu ảnh hưởng trực tiếp từ lưu lượng truyền tải trên mạng. Ở trạng thái bình thường, các con số này sẽ tăng lên một cách đều đặn. Tuy nhiên, khi có các cuộc tấn công ngập lụt, kẻ gian sẽ bơm một lượng dữ liệu rác khổng lồ vào hệ thống. Hệ quả là các thông số đo lường này sẽ gia tăng với tốc độ đột biến. Bằng cách theo dõi tốc độ tăng bất thường của 34 thông số này, hệ thống có thể nhận diện được ngay khi nào mạng đang bị tấn công.



**# Các nhóm MIB-II cùng các biến tương ứng được khảo sát và sử dụng như sau:**



a) Nhóm Interface (Giao diện): Nhóm này không liên quan đến một tầng cụ thể nào, nó định nghĩa thông tin về tất cả các giao diện của nút bao gồm số giao diện, địa chỉ vật lý và địa chỉ IP. Tác giả đã chọn 8 biến MIB từ nhóm này:

1. ifInOctets: Biến này đại diện cho tổng số octet nhận được trên giao diện, bao gồm cả các ký tự tạo khung (framing).

2\. ifOutOctets: Tổng số octet truyền ra khỏi giao diện, bao gồm cả các ký tự tạo khung.

3\. ifoutDiscards: Số lượng các gói tin đi ra ngoài đã được chọn để loại bỏ mặc dù không có lỗi nào được phát hiện để ngăn chúng truyền đi.

4\. ifInUcastPkts: Số lượng gói tin, được phân lớp phụ này chuyển đến một (phân) lớp cao hơn, không được định địa chỉ đến một địa chỉ đa hướng (multicast) hoặc quảng bá (broadcast) ở phân lớp phụ này.

5\. ifInNUcastPkts: Số lượng gói tin, được phân lớp phụ này chuyển đến một (phân) lớp cao hơn, được định địa chỉ đến một địa chỉ đa hướng hoặc quảng bá ở phân lớp phụ này.

6\. ifInDiscards: Số lượng các gói tin đi vào đã được chọn để loại bỏ mặc dù không có lỗi nào được phát hiện để ngăn chúng phân phối đến giao thức ở lớp cao hơn.

7\. ifOutUcastPkts: Tổng số gói tin mà các giao thức cấp cao hơn yêu cầu truyền và không được định địa chỉ đến một địa chỉ đa hướng hoặc quảng bá ở phân lớp phụ này.

8\. ifOutNUcastPkts: Tổng số gói tin mà các giao thức cấp cao hơn yêu cầu truyền, và được định địa chỉ đến một địa chỉ đa hướng hoặc quảng bá ở phân lớp phụ này, bao gồm cả những gói tin bị loại bỏ hoặc không được gửi.

b) Nhóm IP: Nhóm này cung cấp thông tin tầng mạng liên quan đến IP, chẳng hạn như bảng định tuyến và địa chỉ IP.

Tác giả đã chọn 8 biến MIB từ nhóm này:

1. ipInReceives: Tổng số datagram đầu vào nhận được từ các giao diện, bao gồm cả những datagram nhận được khi có lỗi.

2\. ipInDelivers: Tổng số datagram đầu vào được phân phối thành công đến các giao thức người dùng IPv4 (bao gồm cả ICMP).

3\. ipOutRequests: Tổng số datagram IPv4 mà các giao thức người dùng IPv4 cục bộ (bao gồm cả ICMP) cung cấp cho IPv4 trong các yêu cầu truyền tải.

4\. ipOutDiscards: Số lượng các datagram IPv4 đầu ra không gặp phải sự cố nào ngăn cản việc truyền tải đến đích của chúng, nhưng đã bị loại bỏ.

5\. ipInDiscards: Số lượng các datagram IPv4 đầu vào không gặp sự cố nào ngăn cản việc tiếp tục xử lý chúng, nhưng đã bị loại bỏ.

6\. ipForwDatagrams: Số lượng các datagram đầu vào mà thực thể này không phải là đích IPv4 cuối cùng của chúng, kết quả là một nỗ lực đã được thực hiện để tìm tuyến đường chuyển tiếp chúng đến đích cuối cùng đó.

7\. ipOutNoRoutes: Số lượng các datagram IPv4 bị loại bỏ vì không tìm thấy tuyến đường nào để truyền chúng đến đích. Lưu ý rằng điều này bao gồm mọi datagram mà máy chủ không thể định tuyến vì tất cả các bộ định tuyến mặc định của nó đều ngừng hoạt động.

8\. ipInAddrErrors: Số lượng các datagram đầu vào bị loại bỏ vì địa chỉ IPv4 trong trường đích của header IPv4 không phải là một địa chỉ hợp lệ để được nhận tại thực thể này. Bộ đếm này bao gồm các datagram bị loại bỏ vì địa chỉ đích không phải là địa chỉ cục bộ.

c) Nhóm ICMP: Nhóm này định nghĩa thông tin liên quan đến ICMP, chẳng hạn như số lượng gói tin đã gửi và nhận và tổng số lỗi được tạo ra.

Tác giả đã chọn 6 biến MIB từ nhóm này:

1. icmpInMsgs: Tổng số các thông điệp ICMP mà thực thể đã nhận được.

2\. icmpInDestUnreachs: Số lượng các thông điệp ICMP Destination Unreachable nhận được.

3\. icmpOutMsgs: Tổng số các thông điệp ICMP mà thực thể này đã nỗ lực gửi đi.

4\. icmpOutDestUnreachs: Số lượng các thông điệp ICMP Destination Unreachable đã gửi.

5\. icmpInEchos: Số lượng các thông điệp ICMP Echo (yêu cầu) nhận được.

6\. icmpOutEchoReps: Số lượng các thông điệp ICMP Echo Reply đã gửi.

d) Nhóm TCP: Nhóm này cung cấp thông tin tầng giao vận liên quan đến TCP, chẳng hạn như bảng kết nối, giá trị thời gian chờ (time-out), số lượng cổng, và số lượng gói tin đã gửi và nhận. Tác giả đã chọn 8 biến MIB từ nhóm này:

1. tcpOutRsts: Số lượng các phân đoạn (segment) TCP đã gửi chứa cờ RST.

2\. tcpInSegs: Tổng số các phân đoạn nhận được, bao gồm cả những phân đoạn nhận được khi có lỗi. Bộ đếm này bao gồm các phân đoạn nhận được trên các kết nối hiện đang được thiết lập.

3\. tcpActiveOpens: Số lần các kết nối TCP đã thực hiện một quá trình chuyển đổi trực tiếp sang trạng thái SYN-SENT từ trạng thái CLOSED

4\. tcpOutSegs: Tổng số các phân đoạn đã gửi, bao gồm cả những phân đoạn trên các kết nối hiện tại nhưng loại trừ những phân đoạn chỉ chứa các octet được truyền lại.

5\. tcpPassiveOpens: Số lần các kết nối TCP đã thực hiện quá trình chuyển đổi trực tiếp sang trạng thái SYN-RCVD (lưu ý: bản gốc ghi là SYN state nhưng ý nghĩa chính xác là chuyển trạng thái SYN).

6\. tcpRetransSegs: Tổng số các phân đoạn được truyền lại; nghĩa là, số lượng các phân đoạn TCP được truyền đi chứa một hoặc nhiều octet đã được truyền trước đó.

7\. tcpCurrEstab: Số lượng các kết nối TCP có trạng thái hiện tại là ESTABLISHED hoặc CLOSE-WAIT.

8\. tcpEstabResets: Số lần các kết nối TCP đã thực hiện một quá trình chuyển đổi trực tiếp sang trạng thái CLOSED từ trạng thái ESTABLISHED hoặc trạng thái CLOSE-WAIT.

e) Nhóm UDP: Nhóm này cung cấp thông tin tầng giao vận liên quan đến UDP, chẳng hạn như số lượng cổng và số lượng gói tin đã gửi và nhận.

&#x20;Tác giả đã chọn 4 biến MIB từ nhóm này:

1. udpInDatagrams: Tổng số datagram UDP được phân phối cho người dùng UDP.

2\. udpOutDatagrams: Tổng số datagram UDP được gửi từ thực thể này.

3\. udpInErrors: Số lượng các datagram UDP nhận được không thể phân phối vì các lý do khác ngoài việc thiếu ứng dụng ở cổng đích.

4\. udpNoPorts: Tổng số các datagram UDP nhận được mà không có ứng dụng nào ở cổng đích



**Các bước để tạo dataset:(OVERALL)**



Bước 1: Thiết lập môi trường mạng thực: Tác giả xây dựng một mạng cục bộ biệt lập với Internet để đảm bảo tính chân thực, bao gồm 1 bộ định tuyến (router), 2 bộ chuyển mạch (switches) và 2 mạng con. Mạng con thứ nhất có 1 máy tính đóng vai trò Attacker; mạng con thứ hai có 1 máy tính làm Victim, cả 2 mạng con đều chứa 5 PC.



Bước 2: Tạo lưu lượng mạng bình thường (Normal Traffic Generation):

Sử dụng phần mềm LanTrafficV2 cài đặt trên các máy tính để tự động tạo ra các luồng dữ liệu (TCP, UDP, ICMP) qua lại giữa 2 mạng con. Lưu lượng bình thường được duy trì ở tốc độ lên tới 50 Mbps để giả lập một mạng đang hoạt động thực tế.



Bước 3: Phát động các cuộc tấn công:

Máy Attacker sử dụng hàng loạt công cụ mã nguồn mở để tấn công máy Victim bằng các kịch bản khác nhau.



Bước 4: Trong khi các cuộc tấn công đang diễn ra, một chương trình bằng ngôn ngữ Java sẽ "hỏi" bộ định tuyến cứ mỗi 15 giây một lần để chép lại 34 chỉ số MIB. Con số 15 giây được chọn vì nó đủ nhanh để bắt được dấu vết tấn công nhưng không làm máy móc bị quá tải.



**#Phân tích sâu hơn**



*Nhóm tác giả đã sử dụng một số công cụ tấn công mã nguồn mở nổi tiếng để thử nghiệm:*



Các công cụ này cung cấp một số tham số cấu hình, chẳng hạn như loại gói (TCP, UDP, ICMP), số lượng gói được gửi, kích thước gói, độ trễ, v.v.

. Những điều này có thể rất hữu ích trong việc tạo ra các cuộc tấn công

. Trong bài báo này, chúng tôi đã tiến hành một cuộc tấn công Brute Force và sáu loại tấn công làm ngập lụt DoS, được thực hiện bằng cách sử dụng các công cụ đã đề cập trước đó với thời lượng và tham số khác nhau, như được giải thích bên dưới

. Các loại tấn công với các công cụ tương ứng được minh họa trong Bảng 2

. Như được minh họa trong Bảng 2, chúng tôi đã thực hiện các cuộc tấn công bằng cách sử dụng các công cụ khác nhau

. Mỗi loại tấn công được phát động chống lại máy chủ (nạn nhân) trong các kịch bản khác nhau



*Các công cụ tấn công được nhóm tác giả sử dụng bao gồm:*



**Công cụ HyenaeFE** (Tác động lên nhóm Interface và IP - 16 biến): Công cụ này tạo ra các cuộc tấn công ngập lụt (như TCP-SYN, UDP flood, ICMP-ECHO) nhằm làm cạn kiệt băng thông và tài nguyên hệ thống. Trong quá trình thử nghiệm, tải lưu lượng mạng có lúc bị đẩy lên tới mức 50 Mbps. Sự thay đổi ở 16 biến này chủ yếu phản ánh sự quá tải về khối lượng gói tin và tràn bộ nhớ đệm:



Nhóm Interface (8 biến): Phản ánh sự thay đổi ở tầng vật lý và liên kết dữ liệu.

1. ifInOctets \& ifOutOctets: Hai biến này tăng vọt do khối lượng lớn gói tin rác tràn vào và hệ thống cố gắng gửi các gói tin phản hồi lại.

2\. ifInUcastPkts \& ifOutUcastPkts: Chúng tăng mạnh vì phần lớn lưu lượng tấn công nhắm trực tiếp vào địa chỉ IP của nạn nhân.

3\. ifInNUcastPkts \& ifOutNUcastPkts: Chúng gia tăng nếu kẻ tấn công sử dụng các gói tin quảng bá (ví dụ: tấn công Smurf/ICMP dùng địa chỉ IP giả mạo).

4\. ifInDiscards \& ifoutDiscards: Chúng tăng theo cấp số nhân vì bộ nhớ đệm (buffer) của card mạng bị tràn do không thể xử lý kịp lượng gói tin ồ ạt.

Nhóm IP (8 biến): Phản ánh sự tắc nghẽn ở tầng mạng.

1. ipInReceives: Biến này đạt đỉnh (spike) dữ dội trong bất kỳ cuộc tấn công ngập lụt nào.

2\. ipInDelivers: Biến này có thể tăng, nhưng tỷ lệ (ratio) của nó so với ipInReceives sẽ giảm mạnh (dưới 30%) vì hệ thống không thể xử lý nổi.

3\. ipOutRequests: Tăng mạnh do máy chủ cố gắng tạo các gói phản hồi (như RST hoặc ICMP).

4\. ipOutDiscards \& ipInDiscards: Tăng mạnh do cạn kiệt không gian bộ nhớ đệm.

5\. ipForwDatagrams: Tăng nếu bộ định tuyến bị lợi dụng để chuyển tiếp các gói tin giả mạo.

6\. ipOutNoRoutes: Gia tăng khi kẻ tấn công sử dụng địa chỉ IP nguồn giả mạo không có tuyến đường phản hồi hợp lệ.

7\. ipInAddrErrors: Tăng nếu kẻ tấn công gửi gói tin đến các địa chỉ sai lệch



**Công cụ DOSHTTP 2.5.1** (Tác động lên nhóm ICMP - 6 biến) Khi tạo tấn công HTTP Flood, công cụ này tạo ra các yêu cầu hợp lệ lặp đi lặp lại làm cạn kiệt tài nguyên máy chủ. Khi máy chủ bị quá tải và không thể phản hồi qua TCP/HTTP, nó hoặc các thiết bị mạng xung quanh sẽ sinh ra các thông báo lỗi ICMP để báo hiệu sự cố:

1. icmpInMsgs \& icmpOutMsgs: Chúng tăng lên khi hệ thống mạng liên tục trao đổi các thông báo lỗi do quá tải.

2\. icmpInDestUnreachs \& icmpOutDestUnreachs: Biến icmpOutDestUnreachs tăng đột biến khi các cổng của máy chủ nạn nhân bị chiếm dụng hoàn toàn, khiến nó phải gửi thông báo từ chối kết nối mới.

3\. icmpInEchos \& icmpOutEchoReps: Chúng biến động mạnh khi hệ thống kiểm tra sự sống còn của máy chủ (ping) trong lúc máy chủ đang bị treo hoặc phản hồi chậm chạp



Nhận định: Khi máy chủ bị quá tải bởi các yêu cầu HTTP từ DOSHTTP, nó không thể xử lý tiếp và mạng phải phản hồi bằng các thông báo lỗi. Nhóm tác giả đã định nghĩa rõ rằng 6 biến nhóm ICMP được thu thập để theo dõi "số lượng gói tin đã gửi và nhận và tổng số lỗi được tạo ra". Các biến như icmpInDestUnreachs (thông báo lỗi đích không thể truy cập) sẽ có sự thay đổi rõ rệt khi máy chủ từ chối phục vụ lưu lượng mới.



**Công cụ Slowloris script / ActivePerl** (Tác động lên nhóm TCP - 8 biến) Tấn công Slowloris không dùng khối lượng lớn mà gửi các HTTP header cực chậm và không bao giờ hoàn thành để "treo" các kết nối. Nhóm TCP ghi nhận sự biến đổi thông qua các trạng thái duy trì kết nối bất thường:

1. tcpCurrEstab: Biến này tăng lên mức trần (đạt giới hạn tối đa của máy chủ) và duy trì liên tục ở mức cao đó, phản ánh việc toàn bộ socket bị chiếm dụng. Đây là dấu hiệu nhận biết rõ nhất của Slowloris.

2\. tcpPassiveOpens: Tăng mạnh khi kẻ tấn công liên tục khởi tạo hàng nghìn kết nối  mới ban đầu.

3\. tcpInSegs: Trái ngược với tấn công ngập lụt, biến này có xu hướng giảm hoặc thấp hơn bình thường (negative deviation) do kết nối bị treo lại, không có dữ liệu mới nào được gửi hay nhận thêm.

4\. tcpOutSegs: Giảm mạnh do máy chủ bị "đóng băng" và không thể gửi dữ liệu ra ngoài.

5\. tcpOutRsts: Tăng cao do máy chủ buộc phải từ chối các kết nối mới khi đã cạn kiệt tài nguyên socket.

6\. tcpAttemptFails: Tăng vọt khi các nửa kết nối bị treo và rớt do quá thời gian chờ (timeout).

7\. tcpEstabResets: Gia tăng khi hệ thống hoặc tường lửa nỗ lực ngắt các kết nối bị treo quá lâu.

8\. tcpActiveOpens: Thường phản ánh các nỗ lực kết nối ra ngoài của máy chủ, có thể giảm do máy chủ hết tài nguyên



Nhận định: Do không dùng băng thông lớn, các biến Interface không thay đổi nhiều. Thay vào đó, tác giả định nghĩa 8 biến TCP để theo dõi "bảng kết nối và trạng thái của kết nối" ở tầng giao vận. Công cụ Slowloris khiến biến tcpCurrEstab (số lượng kết nối đang duy trì ở trạng thái ESTABLISHED) và tcpPassiveOpens (chuyển sang trạng thái chờ SYN) biến đổi mạnh do hàng ngàn phiên kết nối bị treo cứng.





**Công cụ HttpDosTool4.0 \& THC-Hydra** (Tác động lên nhóm UDP - 4 biến) Bên cạnh việc quét mật khẩu (Brute Force) và tấn công thân HTTP chậm (Slowpost), sự biến đổi của nhóm UDP thường thể hiện rõ nhất khi xảy ra việc cạn kiệt tài nguyên hoặc quét các cổng ngẫu nhiên khiến hệ thống không thể xử lý các dịch vụ dựa trên UDP (như DNS, NTP):

1. udpInDatagrams \& udpOutDatagrams: Chúng ghi nhận sự thay đổi bất thường về lưu lượng UDP, có thể là sự suy giảm do máy chủ đang bận xử lý Brute Force/Slowpost nên không thể xử lý các gói tin UDP hợp lệ.

2\. udpNoPorts: Biến này tăng rất mạnh do kẻ tấn công thường rà quét hoặc gửi dữ liệu rác vào các cổng ngẫu nhiên đóng kín để làm tiêu hao năng lực xử lý của máy chủ.

3\. udpInErrors: Biến này gia tăng vì máy chủ đã bị vắt kiệt tài nguyên CPU/RAM bởi Slowpost hoặc Brute Force, dẫn đến không thể xử lý kịp các datagram UDP đến.



Nhận định: Cả hai công cụ này đều nhắm vào việc vắt kiệt tài nguyên xử lý của tầng ứng dụng (CPU, RAM xử lý mã nguồn PHP/Apache). Khi máy chủ bận rộn xử lý các đăng nhập sai hoặc các header chậm, nó mất khả năng phản hồi các giao thức nền khác. Để theo dõi sự kiệt quệ tài nguyên gián tiếp này, nhóm tác giả sử dụng 4 biến UDP, trong đó biến udpInErrors theo dõi các datagram bị lỗi "do các lý do khác ngoài việc thiếu ứng dụng ở cổng đích" (như tràn bộ nhớ RAM hoặc CPU quá tải không xử lý kịp).



**# Cách thức tiến hành các cuộc tấn công:**



Để đảm bảo bộ dữ liệu mang tính thực tế (Realistic) và không bị phụ thuộc vào các công cụ mô phỏng ảo - vốn là điểm yếu của nhiều tập dữ liệu IDS trước đây, nhóm tác giả đã xây dựng một mạng thử nghiệm phần cứng thực tế.



Chi tiết thiết lập:

Cấu trúc mạng biệt lập: Gồm 1 bộ định tuyến (Router) ở giữa, kết nối 2 mạng con (Subnet) thông qua 2 Switch. Máy Attacker nằm ở mạng con 1, máy Server (Victim - chạy Apache, VNC, FTP) nằm ở mạng con 2.

Tạo nhiễu nền: Tác giả dùng phần mềm LanTrafficV2 để sinh ra lưu lượng mạng bình thường liên tục với cấu hình 70% TCP và 30% UDP, đẩy băng thông lên tới mức 50 Mbps.

Kịch bản tấn công: Các công cụ tấn công (HyenaeFE, DOSHTTP, Slowloris script, THC-Hydra) được cấu hình thực tế. Ví dụ, với Slowloris, kẻ tấn công chỉ cần gửi 1000 socket mỗi 10 giây nhưng đã đủ để đánh sập máy chủ Apache chỉ trong 3 phút.

Cơ chế thu thập: Một chương trình Java (dùng webNMS Agent Toolkit) gửi truy vấn GET/GET-NEXT đến Router để đọc 34 biến MIB với tần suất 15 giây một lần.



***Nhận xét:***



Việc tác giả cô lập hoàn toàn mạng thử nghiệm khỏi Internet là một quyết định hợp lý. Nó giúp loại bỏ các "nhiễu" không xác định từ Internet, đảm bảo dữ liệu thu được đáng tin cậy. Bên cạnh đó, việc sử dụng LanTrafficV2 để duy trì mức băng thông nền 50 Mbps giúp tập dữ liệu không bị rơi vào trạng thái sterile network – một sai lầm mà nhiều nghiên cứu IDS mắc phải khi chỉ thu thập dữ liệu lúc mạng rảnh rỗi.

Lựa chọn tần suất 15 giây: Tác giả đã phân tích và kế thừa từ các nghiên cứu trước đó để tìm ra điểm cân bằng hoàn hảo. Nếu lấy mẫu quá nhanh (ví dụ 1 giây/lần), chính truy vấn của SNMP sẽ tự biến thành một cuộc tấn công DoS làm treo Router. Nếu lấy mẫu quá chậm (ví dụ 1 phút/lần), IDS sẽ trở nên vô dụng vì máy chủ có thể đã sập trước khi hệ thống kịp cảnh báo (như kịch bản Slowloris đánh sập server trong 3 phút).





***# Đánh giá và Phân tích tập dữ liệu thu được:***



Quá trình thực nghiệm đã thu về một tập dữ liệu gồm 4998 bản ghi, bao phủ đa dạng các kịch bản: 600 bản ghi lưu lượng bình thường và 4398 bản ghi tấn công (chia đều cho TCP-SYN, UDP flood, ICMP-ECHO, HTTP flood, Slowloris, Slowpost, Brute Force).



Thay vì cung cấp dữ liệu thô, nhóm tác giả đã thực hiện phân tích thống kê thông qua 2 lăng kính: Độ lệch chuẩn (STD) và Độ lợi thông tin (Information Gain).

1\. Phân tích qua Độ lệch chuẩn (STD): Dữ liệu cho thấy sự biến động cực kỳ dữ dội trong quá trình mạng bị tấn công. Biến ifInOctets (tổng byte nhận vào) có độ lệch chuẩn lên tới mức cực lớn: hơn 1,2 tỷ.



Phân tích: Độ lệch chuẩn khổng lồ này phản ánh chính xác bản chất của các cuộc tấn công ngập lụt băng thông (như UDP hay ICMP flood). Tuy nhiên, tác giả cũng ngầm chỉ ra một cảnh báo: nếu chỉ dùng các thuật toán dựa trên ngưỡng thông thường để thiết lập giới hạn cho các biến này, hệ thống sẽ rất dễ sinh ra cảnh báo giả vì ranh giới giữa lưu lượng bình thường lúc cao điểm và lưu lượng tấn công là rất mong manh.



2\. Phân tích qua Độ lợi thông tin (Information Gain - IG): Tác giả dùng thuật toán IG để xếp hạng độ quan trọng của 34 biến trong việc phân biệt giữa trạng thái "bình thường" và "bị tấn công".

Kết quả cho thấy: Biến ipOutDiscards (số datagram IP bị vứt bỏ dù không có lỗi) giữ Hạng 1 với điểm IG cao nhất (0.6338). Các vị trí tiếp theo thuộc về các gói tin báo lỗi như icmpOutDestUnreachs (Hạng 2) và ipInDiscards (Hạng 3).

Ngược lại Biến ifInOctets (tổng số byte đầu vào) - chỉ số mà các quản trị trị viên mạng thường nhìn vào đầu tiên để xem mạng có bị nghẽn hay không - lại bị xếp ở Hạng 34 (hạng bét) với điểm IG = 0.



***Nhận xét:***



Kết quả của bảng xếp hạng IG mang tính "cách mạng". Nó chứng minh rằng: Việc nhìn vào lưu lượng mạng lớn hay nhỏ không giúp ích gì cho Machine Learning trong việc nhận diện một cuộc tấn công tinh vi. (Ví dụ: Tấn công Slowloris hoàn toàn không làm tăng băng thông nhưng vẫn đánh sập mạng). Thay vào đó, Machine Learning cực kỳ nhạy bén với các "chỉ số cạn kiệt tài nguyên". Khi Router bắt đầu phải "vứt bỏ" các gói tin hợp lệ (ipOutDiscards) hoặc liên tục gửi các thông báo "không thể kết nối" (icmpOutDestUnreachs), đó mới là lời tố cáo rõ ràng nhất rằng hệ thống đang bị tổn thương sâu sắc từ bên trong.



Mặc dù bộ dữ liệu rất chất lượng, nhưng ta có thể thấy có sự mất cân bằng lớp khá rõ: 600 bản ghi Normal so với 4398 bản ghi Attack. Sự mất cân bằng này có thể khiến mô hình bị bias và dễ dàng phán đoán mọi thứ là "Attack". Các nghiên cứu sử dụng lại bộ dữ liệu này chắc chắn sẽ phải dùng thêm các kỹ thuật cân bằng dữ liệu (như SMOTE) trước khi đưa vào huấn luyện.





***# Kết luận của tác giả và Ý nghĩa nghiên cứu***





1\. Tác giả khẳng định họ đã tạo ra một tập dữ liệu thực tế, hoàn toàn không thiên vị (unbiased), không chứa các thuộc tính ngoài ý muốn trong cả lưu lượng bình thường lẫn lưu lượng bất thường. Tập dữ liệu này thành công trong việc bao phủ các cuộc tấn công hiện đại trên cả 3 tầng mạng: Tầng mạng (Network), Tầng giao vận (Transport) và Tầng ứng dụng (Application).



***Nhận xét:***

Trong những cuộc nghiên cứu trước,nhiều người thường bị mắc kẹt với các tập dữ liệu cũ kỹ vốn được tạo ra từ môi trường giả lập (simulated) và không còn phản ánh đúng các cuộc tấn công hiện đại. Việc tác giả tự xây dựng Test-bed và công bố 4998 bản ghi thực tế này là một đột phá.

Tính "sạch" của dữ liệu: Bằng cách cô lập mạng thử nghiệm, tác giả đảm bảo rằng nhãn (label) của dữ liệu là chính xác tuyệt đối. Khi một bản ghi được dán nhãn là "tấn công Slowloris", các nhà nghiên cứu sau này có thể tin tưởng 100% rằng sự biến động của 34 biến MIB lúc đó hoàn toàn là do Slowloris gây ra, không bị lẫn lộn bởi các tác nhân nhiễu (noise) ngẫu nhiên từ Internet.



2\. Khẳng định SNMP-MIB là một giải pháp thay thế rất hiệu quả và siêu nhẹ.

Phương pháp tạo dữ liệu của tác giả cung cấp bằng chứng về khả năng và tính hiệu quả của dữ liệu SNMP-MIB trong việc phát hiện bất thường mạng thông qua việc nhận diện thành công số lượng lớn các cuộc tấn công phổ biến.



***Nhận xét:***

SNMP-MIB giải quyết bài toán trên một cách khác biệt. Nó không quan tâm nội dung gói tin là gì, nó chỉ nhìn vào các thống kê như: có bao nhiêu gói tin bị vứt bỏ, có bao nhiêu kết nối đang chờ. Việc sử dụng MIB biến IDS từ một hệ thống cồng kềnh thành một module giám sát "siêu nhẹ", tiết kiệm tối đa tài nguyên CPU/RAM của hệ thống.



3\. Khi áp dụng các thuật toán phân loại lên 5 nhóm MIB, nhóm tác giả phát hiện ra rằng hiệu suất của mỗi bộ phân loại biến thiên rất khác nhau trên từng nhóm.



***Nhận xét:***

Vì sự thay đổi của mạng khi bị tấn công là sự cộng hưởng phức tạp của hàng chục biến số (ví dụ: biến TCP tăng nhưng biến UDP giảm, biến ICMP báo lỗi...), bộ não con người hoặc các bộ quy tắc (rule-based IF/ELSE) truyền thống không thể xử lý nổi. Sự phân hóa về hiệu suất trên 5 nhóm MIB rất phù hợp để áp dụng Học máy (Machine Learning).

Từ kết luận này của tác giả, ta có thể thấy một hướng nghiên cứu tiềm năng: Xây dựng các Mô hình học máy kết hợp. Thay vì dùng 1 thuật toán cho toàn bộ 34 biến, ta có thể huấn luyện Thuật toán A chuyên giám sát nhóm TCP, Thuật toán B chuyên giám sát nhóm UDP, sau đó tổng hợp kết quả của chúng lại để đưa ra phán quyết cuối cùng. Điều này sẽ đẩy độ chính xác của IDS lên mức tối đa.



