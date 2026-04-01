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



**Các bước để tạo dataset:**



Bước 1: Thiết lập môi trường mạng thực: Tác giả xây dựng một mạng cục bộ biệt lập với Internet để đảm bảo tính chân thực, bao gồm 1 bộ định tuyến (router), 2 bộ chuyển mạch (switches) và 2 mạng con. Mạng con thứ nhất có 1 máy tính đóng vai trò Attacker; mạng con thứ hai có 1 máy tính làm Victim.

Bước 2: Tạo lưu lượng mạng bình thường (Normal Traffic Generation): Sử dụng phần mềm LanTrafficV2 cài đặt trên các máy tính để tự động tạo ra các luồng dữ liệu (TCP, UDP, ICMP) qua lại giữa 2 mạng con. Lưu lượng bình thường được duy trì ở tốc độ lên tới 50 Mbps để giả lập một mạng đang hoạt động thực tế.

Bước 3: Phát động các cuộc tấn công: Máy Attacker sử dụng hàng loạt công cụ mã nguồn mở để tấn công máy Victim bằng các kịch bản khác nhau

Bước 4: Trong khi các cuộc tấn công đang diễn ra, một chương trình bằng ngôn ngữ Java sẽ "hỏi" bộ định tuyến cứ mỗi 15 giây một lần để chép lại 34 chỉ số MIB. Con số 15 giây được chọn vì nó đủ nhanh để bắt được dấu vết tấn công nhưng không làm máy móc bị quá tải.

