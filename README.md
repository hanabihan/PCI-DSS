## I.	Introduction.
### Định nghĩa: 
PCI DSS (Payment Card Industry Data Security Standard) là tiêu chuẩn bảo mật giúp bảo vệ dữ liệu tài khoản thanh toán bằng cách đưa ra các yêu cầu tối thiểu về kỹ thuật và vận hành. 
### Mục tiêu:
Bảo vệ dữ liệu chủ thẻ khỏi gian lận, rò rỉ và tấn công mạng; chuẩn hóa quy trình bảo mật trên toàn cầu.
### Tổ chức quản lý: 
Hội đồng Tiêu chuẩn Bảo mật PCI (PCI SSC - Payment Card Industry Security Standards Council), sáng lập bởi Visa, MasterCard, American Express, Discover và JCB.
### 12 yêu cầu chính của PCI DSS:
#### Xây dựng và duy trì mạng lưới và hệ thống an toàn:
1. Cài đặt và duy trì các biện pháp kiểm soát an ninh mạng (Network Security Controls).
2. Áp dụng cấu hình bảo mật cho mọi thành phần hệ thống.
#### Bảo vệ dữ liệu tài khoản:
3. Bảo vệ dữ liệu tài khoản được lưu trữ.
4. Mã hóa mạnh dữ liệu chủ thẻ khi truyền qua mạng công cộng.
#### Duy trì chương trình quản lý lỗ hổng bảo mật:
5. Bảo vệ tất cả hệ thống và mạng khỏi phần mềm độc hại.
6. Phát triển và duy trì hệ thống, phần mệt bảo mật.
#### Áp dụng các biện pháp kiểm soát truy cập mạnh mẽ:
7. Giới hạn quyền truy cập theo nhu cầu công việc (Need-to-Know).
8. Định danh người dùng và xác thực truy cập.
9. Hạn chế truy cập vật lý vào dữ liệu chủ thẻ.
#### Thường xuyên giám sát và kiểm tra mạng:
10. Ghi log và giám sát mọi truy cập đến hệ thống và dữ liệu chủ thẻ.
11. Kiểm tra bảo mật hệ thống và mạng định kỳ.
#### Duy trì chính sách bảo mật thông tin:
12. Duy trì chính sách và chương trình bảo mật thông tin của tổ chức.
## II.	Thông tin về phạm vi áp dụng PCI DSS.
### Dữ liệu tài khoản bao gồm:
Dữ liệu chủ thẻ (Cardholder Data (CHD)):
+ Primary Account Number (PAN): Số thẻ. 
+ Cardholder Name: Tên chủ thẻ. 
+ Expiration Date: Ngày hết hạn. 
+ Service Code: Mã gồm 3 chữ số. 

=> Có thể lưu khi cần. PAN phải được mã hóa làm cho không thể đọc được; tên chủ thẻ, ngày hết hạn và mã thì không cần mã hóa.

Dữ liệu xác thực nhạy cảm (Sensitive Authentication Data (SAD)):
+ Full Track Data: Toàn bộ dữ liệu trên dải từ, chip EMV.
+ Card Verification Code: CVV, CVC, CID.
+ PINs/PIN blocks: Mã PIN khi giao dịch.

=> Không được lưu sau khi giao dịch được xác thực (ngoại trừ một số trường hợp đặc biệt theo quy định).

## III.	Mối quan hệ giữa PCI DSS và PCI SSC.
PCI DSS hỗ trợ việc sử dụng phần mềm thanh toán an toàn trong CDE (Cardholder Data Environment) thông qua SSF (Software Security Framework). Khung này bao gồm: Secure Software Standard và Secure Software Lifecycle (Secure SLC) Standard.
- Validated Software: PCI DSS duy trì danh sách các phần mềm thanh toán. Những phần mềm này được đánh giá bởi tổ chức đánh giá đủ điều kiện.
- Qualified Software Vendors: PCI DSS cũng đánh giá các nhà phát triển phần mềm. Những nhà cung cấp đáp ứng Scure SLC Standard sẽ được công nhận là Qualified Software Vendors.
- Trước đây người ta vẫn thường sử dụng PA-DSS (Payment Application Data Security Standard) cho tới tháng 10/2022, PA-DSS đã được thay thế bởi SSF (Software Security Framework).

Việc sử dụng phần mềm được PCI SSC chứng nhận không làm cho tổ chức tuân thủ PCI DSS. Khi đánh giá PCI DSS, doanh nghiệp vẫn phải chứng minh rằng phần mềm đã được tùy chỉnh so với phiên bản đã được chứng nhận, việc đánh giá sẽ cần kỹ lưỡng hơn.

Khả năng áp dụng của PCI DSS đối với các nhà cung cấp phần mềm thanh toán:
- Lưu trữ, xử lý hoặc truyền dữ liệu tài khoản.
- Có quyền truy cập vào dữ liệu tài khoản của khách hàng.

Các nhà cung cấp phần mềm có thể thuộc phạm vi áp dụng của PCI DSS bao gồm:
- Nhà cung cấp dịch vụ thanh toán.
- Nhà cung cấp dịch vụ đám mây cung cấp:
  - Cloud Payment.
  - SaaS (Software as a Service).
  - Nền tảng thương mại điện tử.
  - Dịch vụ thanh toán.

Bespoke và Custom Software:
- Bespoke Software: Phần mềm được phát triển riêng cho 1 tổ chức.
- Custom Software: Phần mềm có sẵn nhưng được tùy chỉnh theo nhu cầu của tổ chức.

Nếu Bespoke/Custom Software lưu trữ dữ liệu thẻ, xử lý hoặc truyền dữ liệu thẻ, ảnh hưởng đến tính bảo mật của dữ liệu thẻ thì đều phải được đánh giá theo PCI DSS.
Ngay cả khi doanh nghiệp thuê công ty khác viết phần mềm, doanh nghiệp vẫn chịu trách nhiệm đảm bảo phần mềm đó đáp ứng yêu cầu của PCI DSS. 
## IV.	Phạm vi của các yêu cầu PCI DSS.
CDE:
- Thành phần hệ thống, con người và quy trình có chức năng lưu trữ, xử lý hoặc truyền dữ liệu thẻ (CHD/SAD).
- Các thành phần hệ thống không trực tiếp xử lý dữ liệu thẻ nhưng có thể truy cập trực tiếp vào các hệ thống đó.
- Mọi hệ thống, con người và quy trình có thể ảnh hưởng đến tính bảo mật của CHD/SAD, dù không trực tiếp lưu trữ hay xử lý dữ liệu thẻ.

Hệ thống bao gồm: thiết bị mạng, máy chủ, thiết bị máy tính, thảnh phần ảo hóa (Virtual), thành phần trên nền tảng đám mây (Cloud), phần mềm.
Ví dụ về thành phần hệ thống:
1. Hệ thống lưu trữ, xử lý và truyền tải dữ liệu tài khoản.
- Máy POS (payment terminal).
- Hệ thống xác thực tài khoản (authorization systems).
- Hệ thống thanh toán bù trừ (clearing systems).
- Hệ thống phần mềm trung gian thanh toán (payment middleware systems).
- Hệ thống quản lý thanh toán (payment back-office systems).
- Website bán hàng (shopping cart and store front systems).
- Payment gateway/switch systems.
- Hệ thống phát hiện gian lận (fraud monitoring systems).
2. Hệ thống bảo mật.
- Authentication servers.
- Access control servers.
- SIEM.
- Physical security systems (quyền truy cập thẻ hoặc CCTV).
- MFA.
- Anti-malware.
3. Hệ thống phân tách mạng.
- Firewall.
- Network Security Controls.
4. Các hệ thống có thể ảnh hưởng đến bảo mật dữ liệu tài khoản hoặc CDE.
- DNS.
- Web redirection.
5. Thành phần ảo hóa.
- Máy ảo.
- Switch/Router ảo.
- Application/Desktops ảo.
- Hypervisor.
6. Hạ tầng và dịch vụ đám mây.
- Containers. 
- Virtual private clouds (VPC).
- Quản lý danh tính và truy cập trên đám mây (Cloud IAM).
- Cơ sở hạ tầng đám mây.
- Kubernetes.
7. Thiết bị mạng: Switches, routers, thiết bị VoIP, điểm truy cập không dây và các thiết bị mạng khác.
8. Server: Web, application, database, authentication, mail, proxy, NTP (Network Time Protocol), DNS (Domand Name System).
9. Thiết bị người dùng: Máy tính, laptop, máy trạm, máy trạm quản trị, tablet và thiết bị di động.
10. Thiết bị ngoại vi: máy in, fax, scan.
11. Nơi lưu trữ dữ liệu tài khoản: giấy, file dữ liệu, file âm thanh, hình ảnh và video.
12.  Ứng dụng và phần mềm: Phần mềm mua sẵn, SaaS, phần mềm tự phát triển (bespoke) và phần mềm tùy chỉnh (custom), các ứng dụng nội bộ và Internet.
13. Công cụ phát triển và triển khai phần mềm: hệ thống quản lý cấu hình, kho mã nguồn và các hệ thống triển khai phần mềm đến CDE hoặc các hệ thống có thể ảnh hưởng đến CDE.

#### a) Phạm vi PCI DSS hàng năm.
Để chuẩn bị cho đánh giá PCI DSS theo Requirement 12.5.1 thì đơn vị phải xác định chính xác phạm vi đánh giá.
Để làm được điều đó, doanh nghiệp cần:
- Xác định tất cả các vị trí và luồng dữ liệu tài khoản.
- Xác định các hệ thống 
  - Kết nối với CDE.
  - Lưu trữ, xử lý hoặc truyền dữ liệu thẻ.
  - Khi bị xâm phạm có thể ảnh hưởng đến CDE (vd: authentication, remote access, logging). 

Tất cả các loại hệ thống và vị trí nên được xem xét trong quá trình xác định phạm vi, bao gồm cả các địa điểm sao lưu/phục hồi và hệ thống dự phòng.
Sau khi xác định phạm vi, cần phải lưu giữ tài liệu mô tả cách xác định phạm vi PCI DSS. Tài liệu này dùng để đánh giá và tham khảo cho các lần đánh giá tiếp theo.
Cuối cùng, đối với mỗi đánh giá PCI DSS, người đánh giá xác nhận rằng doanh nghiệp đã xác định và ghi lại chính xác phạm vi đánh giá.

**#NOTE**: Việc đánh giá PCI DSS (PCI DSS Scope) phải được doanh nghiệp đánh giá hằng năm. Tuy nhiên, hoạt động này không giống và không thể thay thế việc xác nhận phạm vi do đánh giá viên (PCI DSS Assessor) thực hiện trong quá trình đánh giá chính thức.

#### b) Phân tách mạng (Segmentation).
Phân tách mạng là tách riêng CDE khỏi phần còn lại của mạng lưới. Tuy nhiên, PCI DSS không bắt buộc phải phân tách mạng, nhưng được khuyến khích mạnh mẽ như có 1 phương pháp giảm thiểu:
- Phạm vi đánh giá PCI DSS.
- Chi phí đánh giá PCI DSS.
- Chi phí và độ khó của việc triển khai và duy trì các biện pháp kiểm soát PCI DSS.
- Rủi ro đối với dữ liệu thẻ bằng cách tập trung dữ liệu vào ít hệ thống được kiểm soát hơn.

Nếu không có phân tách đầy đủ (Flat Network) thì toàn bộ hệ thống mạng sẽ nằm trong phạm vi đánh giá PCI DSS.

Segmentation có thể thực hiện bằng các biện pháp vật lý hoặc logic, chẳng hạn như Firewall/Internal network security controls, routers với strong access control lists (ACL), VLAN, Các công nghệ khác giúp giới hạn quyền truy cập vào CDE. 

Để được coi là nằm ngoài phạm vi của PCI DSS, 1 phần hệ thống phải được phân tách hoàn toàn khỏi CDE và không thể ảnh hưởng đến tính bảo mật dữ liệu chủ thẻ ngay cả khi hệ thống đó bị tấn công.

Điều kiện trước khi phân tách mạng:
- Hiểu rõ các quy trình nghiệp vụ liên quan đến lưu trữ, xử lý và truyền dữ liệu tài khoản.
- Giảm số lượng nơi lưu dữ liệu thẻ bằng cách loại bỏ dữ liệu không cần thiết và tập trung dữ liệu cần thiết vào ít hệ thống hơn. Điều này có thể yêu cầu thay đổi hoặc thiết kế lại quy trình nghiệp vụ đang sử dụng.

Để xác định đúng phạm vi PCI DSS (Scope), doanh nghiệp nên vẽ sơ đồ luồng dữ liệu (Data Flow Diagram - DFD). DFD giúp doanh nghiệp biết:
- Dữ liệu tài khoản đi vào hệ thống từ đâu.
- Dữ liệu được lưu ở đâu.
- Dữ liệu được xử lý như thế nào.
- Dữ liệu được truyền qua những hệ thống nào.

Ngoài ra, sơ đồ còn cho thấy tất cả các vị trí lưu trữ, xử lý và truyền dữ liệu thẻ, từ đó giúp:
- Xác định chính xác CDE.
- Thiết kế và triển khai Segmentation hiệu quả.
- Kiểm tra xem Segmentation đã thực sự cô lập CDE khỏi các hệ thống ngoài phạm vi hay chưa.

Nếu doanh nghiệp dùng Segmentation để giảm Scope, thì Assessor phải kiểm tra và xác nhận rằng việc phân tách đó đủ hiệu quả. Tuy nhiên, không có 1 mô hình Segmentation áp dụng cho mọi doanh nghiệp. Việc đánh giá có đạt yêu cầu hay không sẽ phụ thuộc vào 1 số yếu tố như cấu hình mạng, công nghệ được triển khai và các biện pháp kiểm soát khác có thể được thực hiện.

#### c) Mạng không dây (Wireless).
Nếu doanh nghiệp dùng mạng không dây để lưu trữ, xử lý và truyền dữ liệu; hoặc các mạng VLAN để kết nối với CDE thì các yêu cầu PCI DSS về mạng không dây phải được áp dụng.

Ngoài ra, doanh nghiệp cần phải thường xuyên kiểm tra và phát hiện các thiết bị wifi trái phép theo Requirement 11.2.1. Điều này áp dụng ngay cả khi doanh nghiệp không sử dụng wifi trong CDE, vì kẻ tấn công có thể cắm một Access Point trái phép vào mạng.

Trước khi triển khai wireless, doanh nghiệp nên đánh giá rủi ro và chỉ sử dụng chúng khi cần thiết.

#### d) Khi dữ liệu thẻ được gửi nhầm qua một kênh không mong muốn.
Đôi khi doanh nghiệp vô tình nhận được dữ liệu thẻ hoặc dữ liệu xác thực nhạy cảm qua những kênh không được thiết kế để nhận dữ liệu này (ví dụ: email, chat, ứng dụng nhắn tin...). Khi đó, doanh nghiệp có 2 lựa chọn:
- Đưa kênh đó vào phạm vi của CDE và bảo mật theo tiêu chuẩn PCI DSS.
- Xóa dữ liệu 1 cách an toàn và thực hiện các biện pháp để ngăn chặn việc kênh gửi dữ liệu qua kênh đó trong tương lai.

#### e) Dữ liệu thẻ được mã hóa và phạm vi PCI DSS.
Chỉ mã hóa dữ liệu vẫn chưa đủ để đưa hệ thống ra khỏi phạm vi PCI DSS. Các trường hợp vẫn thuộc phạm vi của PCI DSS:
- Dữ liệu thẻ đã mã hóa (Encrypted Cardholder Data) được lưu trên cùng hệ thống hoặc cùng thiết bị lưu trữ với khóa giải mã (Decryption Key).
- Dữ liệu thẻ đã mã hóa được lưu trong cùng môi trường với khóa giải mã.
- Dữ liệu thẻ đã mã hóa có thể được truy cập bởi người hoặc hệ thống cũng có quyền truy cập vào khóa giải mã.

=> Lý do: Nếu dữ liệu mã hóa và khóa giải mã cùng tồn tại hoặc cùng có thể truy cập, kẻ tấn công có thể lấy cả 2 và giải mã dữ liệu thẻ. Vì vậy, PCI DSS vẫn coi các hệ thống này thuộc phạm vi đánh giá.

#### f) Dữ liệu chủ thẻ được mã hóa và tác động đến phạm vi tuân thủ PCI DSS đối với các nhà cung cấp dịch vụ bên thứ ba (Third-Party Service Providers – TPSPs).
Nếu các nhà cung cấp dịch vụ bên thứ 3 chỉ nhận hoặc lữu trữ dữ liệu được mã hóa bởi khách hàng, không có khả năng giải mã dữ liệu, không có khóa giải mã và không quản lý khóa mã hóa thì có thể coi dữ liệu đó nằm ngoài phạm vi PCI DSS.

Việc xác định bên nào chịu trách nhiệm đối với các biện pháp kiểm soát PCI DSS phụ thuộc vào ai có quyền truy cập vào khóa giải mã, vai trò của mỗi bên và thỏa thuận của các bên. Các trách nhiệm được quy định và ghi rõ trong hợp đồng.

#### g) Cách doanh nghiệp sử dụng nhà cung cấp dịch vụ bên thứ 3 (TPSPs) và trách nhiệm tuân thủ PCI DSS.
Doanh nghiệp (customer) có thể sử dụng TPSPs để lưu trữ, xử lý, truyền tải dữ liệu tài khoản hoặc quản lý các hệ thống thuộc phạm vi PCI DSS. Tuy nhiên, việc sử dụng TPSP có thể ảnh hưởng đến bảo mật của CDE.

**#NOTE**: Việc sử dụng TPSPs không có nghĩa doanh nghiệp đã tuân thủ PCI DSS cũng như không loại bỏ trách nhiệm của doanh nghiệp đối với tuân thủ PCI DSS. 

##### g.1) Việc sử dụng TPSPs và tác động đến việc đáp ứng yêu cầu 12.8 của PCI DSS đối với khách hàng.
Nếu sử dụng TPSPs, doanh nghiệp phải quản lý mối quan hệ với TPSPs, theo dõi tình trạng tuân thủ PCI DSS của TPSPs và đảm bảo TPSPs đáp ứng với các yêu cầu liên quan.

Requirement 12.8 áp dụng với TPSPs nếu họ có quyền truy cập vào CDE, quản lý các hệ thống thuộc phạm vi PCI DSS thay cho doanh nghiệp, có khả năng ảnh hưởng đến bảo mật dữ liệu thẻ hoặc dữ liệu xác thực.

TPSPs không bắt buộc phải có chứng nhận PCI DSS, nhưng doanh nghiệp phải quản lý và giám sát họ nếu dịch vụ của họ có liên quan đến CDE hoặc ảnh hưởng đến bảo mật dữ liệu thẻ.

##### g.2) Tác động của việc sử dụng TPSP cho các dịch vụ đáp ứng yêu cầu PCI DSS của khách hàng.
Khi TPSP thực hiện một phần yêu cầu PCI DSS thay cho khách hàng hoặc dịch vụ của họ ảnh hưởng đến bảo mật dữ liệu thẻ thì các yêu cầu PCI DSS liên quan vẫn nằm trong phạm vi đánh giá của khách hàng và TPSP phải chứng minh rằng họ đã đáp ứng các yêu cầu PCI DSS thuộc trách nhiệm của mình. Nếu TPSP không cung cấp được bằng chứng, khách hàng không thể chứng minh mình đã đáp ứng yêu cầu PCI DSS.

##### g.3) Tầm quan trọng của việc hiểu rõ trách nhiệm giữa khách hàng TPSP và TPSP.
Doanh nghiệp và TPSP phải xác định rõ trách nhiệm của mỗi bên. 2 bên cần làm rõ:
- Các dịch vụ và thành phần hệ thống nằm trong phạm vi đánh giá PCI DSS của TPSP.
- Các yêu cầu và yêu cầu phụ cụ thể của PCI DSS được TPSP đánh giá.
- Bất kỳ yêu cầu nào mà khách hàng của TPSP có trách nhiệm đưa vào đánh giá PCI DSS của riêng họ.
- Bất kỳ yêu cầu PCI DSS nào mà trách nhiệm được chia sẻ giữa TPSP và khách hàng của họ.

Theo Requirement 12.9.2, TPSP phải hỗ trợ khách hàng bằng cách cung cấp:
- Tình trạng tuân thủ PCI DSS.
- Requirement do TPSP chịu trách nhiệm.
- Requirement do khách hàng chịu trách nhiệm.
- Requirement có trách nhiệm chia sẻ.

PCI DSS cung cấp Responsibility Matrix giúp xác định rõ trách nhiệm của từng bên. Không phải mọi TPSP đều phải cung cấp Responsibility Matrix. Chỉ bắt buộc khi:
- TPSP thực hiện Requirement PCI DSS thay khách hàng.
- 1 Requirement PCI DSS là trách nhiệm chung giữa TPSP và khách hàng.
- Dịch vụ của TPSP ảnh hưởng đến bảo mật dữ liệu thẻ.

Dù không phải cung cấp Responsibility Matrix, TPSP vẫn phải cung cấp thông tin về tình trạng tuân thủ PCI DSS để khách hàng có thể quản lý và giám sát TPSP theo Requirement 12.8.

##### g.4) Các cách để TPSP chứng minh tuân thủ PCI DSS.
Nếu TPSP cung cấp dịch vụ thay khách hàng đáp ứng các yêu cầu PCI DSS hoặc dịch vụ đó ảnh hưởng đến bảo mật dữ liệu thẻ, TPSP cần chứng minh mình tuân thủ PCI DSS. Có 2 cách:
- Đánh giá hằng năm: TPSP thực hiện đánh giá PCI DSS mỗi năm và cung cấp bằng chứng cho khách hàng để chứng mình TPSP đáp ứng các yêu cầu của PCI DSS.
- Đánh giá theo yêu cầu: Nếu TPSP không thực hiện đánh giá PCI DSS hằng năm thì phải trải qua yêu cầu của khách hàng và tham gia các đánh giá PCI DSS của từng khách hàng. Kết quả đánh giá gửi cho khách hàng.

Nếu TPSP đã tự đánh giá PCI DSS thì TPSP cần:
- Cung cấp bằng chứng xác minh phạm vi đánh giá đã bao gồm dịch vụ cung cấp cho khách hàng và các yêu cầu PCI DSS liên quan đã được kiểm tra và đáp ứng.
- Nếu có AOC (Attestation of Compliance) thì phải cung cấp cho khách hàng khi được yêu cầu. 
- Khách hàng cũng có thể yêu cầu 1 phần của ROC (Report on Compliance). ROC có thể che bớt các thông tin nhạy cảm.

Nếu không có AOC, TPSP vẫn phải cung cấp bằng chứng khác để khách hàng hoặc assessor xác minh rằng TPSP đáp ứng các yêu cầu của PCI DSS.

##### g.5) Sự hiện diện của TPSP trên danh sách các nhà cung cấp dịch vụ tuân thủ PCI DSS của các thương hiệu thanh toán.
Có tên trong danh sách PCI DSS của Visa/Mastercard chỉ đủ để chứng minh trạng thái tuân thủ, không đủ để chứng minh TPSP đáp ứng các yêu cầu PCI DSS thay khách hàng. Trong trường hợp đó, khách hàng cần AOC hoặc các bằng chứng chi tiết khác.

## V.	Các phương pháp tốt nhất để tích hợp PCI DSS vào quy trình hoạt động thường ngày.
PCI DSS không chỉ được áp dụng khi đánh giá mà cần được duy trì như một phần của hoạt động hằng ngày (Business-as-Usual - BAU) để đảm bảo các biện pháp bảo mật luôn hoạt động hiệu quả.

1 số cách thực hành:
- Phân công trách nhiệm rõ ràng cho cá nhân hoặc nhóm chịu trách nhiệm về việc tuân thủ PCI DSS.
- Phát triển các chỉ số hiệu suất để đo lường hiệu quả của các biện pháp bảo mật và giám sát liên tục các kiểm soát bảo mật: tường lửa và kiểm soát an ninh mạng, IDS/IPS, cơ chế phát hiện thay đổi, phần mềm chống mã độc và kiểm soát truy cập.
- Thường xuyên xem xét log để phát hiện các xu hướng hoặc hành vi bất thường.
- Phát hiện và xử lý kịp thời các sự cố của kiểm soát bảo mật.
- Khi lỗi kiểm soát bảo mật:
  - Khôi phục kiểm soát bảo mật.
  - Xác định nguyên nhân gây ra lỗi.
  - Xác định và xử lý các vấn đề bảo mật phát sinh do sự cố.
  - Thực hiện các biện pháp khắc phục để ngăn chặn nguyên nhân gây ra lỗi tái diễn.
  - Tiếp tục giám sát (có thể tăng cường giám sát trong một thời gian) để xác nhận kiểm soát đã hoạt động bình thường.
- Đánh giá rủi ro trước khi thay đổi hệ thống, mạng hay cấu hình:
  - Đánh giá xem thay đổi có làm ảnh hưởng phạm vi PCI DSS hay tạo rủi ro mới không.
  - Xác định các yêu cầu PCI DSS áp dụng cho hệ thống mới.
  - Cập nhật phạm vi PCI DSS và triển khai các biện pháp kiểm soát bảo mật khi cần thiết.
  - Cập nhật tài liệu để phản ánh các thay đổi đã được thực hiện.
- Xem xét tác động đến phạm vi và yêu cầu của PCI DSS khi có những thay đổi trong cấu trúc tổ chức.
- Kiểm tra định kỳ các kết nối bên ngoài và quyền truy cập của TPSP.
- Kiểm tra các nhà phát triển phần mềm bên thứ 3, cần xác nhận định kỳ rằng họ vẫn tuân thủ PCI DSS Requirement 6 về phát triển phần mềm an toàn.
- Rà soát định kỳ toàn bộ môi trường: kiểm tra các yêu cầu PCI DSS vẫn được thực hiện, nhân viên có làm đúng quy trình, máy chủ và thiết bị đã được cấu hình đúng, vá lỗi đầy đủ, Anti-malware được cập nhật, log được xem xét thường xuyên và tài khoản mặc định đã bị vô hiệu hóa hoặc thay đổi.
- Lưu trữ bằng chứng phục vụ đánh giá: audit logs, báo cáo quét lỗ hổng bảo mật và đánh giá các quy tắc kiểm soát an ninh mạng. Các tài liệu này sẽ được sử dụng trong các đợt đánh giá PCI DSS tiếp theo.
- Thiết lập truyền thông với tất cả các bên ảnh hưởng khi có mối đe dọa mới và những thay đổi trong tổ chức, biện pháp giảm thiểu rủi ro và thông tin liên hệ để báo cáo xử lý hoặc sự cố.
- Đánh giá công nghệ phần cứng và phần mềm ít nhất 12 tháng 1 lần để xem chúng còn được hỗ trợ và đáp ứng các yêu cầu của PCI DSS hay không.

## VI.	Hướng dẫn người đánh giá cách lấy mẫu (sampling) khi đánh giá PCI DSS.
Sampling là việc lấy mẫu đại diện thay vì kiểm tra 100% tất cả hệ thống, thiết bị hoặc nhân sự. PCI DSS cho phép sampling khi số lượng cần đánh giá quá lớn và việc kiểm tra toàn bộ sẽ tốn nhiều thời gian và nguồn lực, điều này giúp đánh giá hiệu quả hơn.

Assessor được phép lấy mẫu kiểm tra nhưng doanh nghiệp thì không được. Assessor cũng không được chỉ đánh giá 1 số Requirement rồi bỏ qua Requirement khác. Sampling chỉ áp dụng cho đối tượng được kiểm tra, không áp dụng cho Requirement.

Tuy nhiên, PCI DSS khuyến khích Nếu có công cụ tự động và có thể kiểm tra toàn bộ hệ thống nhanh chóng thì nên kiểm tra 100%. Chỉ khi không thể kiểm tra toàn bộ bằng công cụ thì sampling là phương án phù hợp.

Assessor tự lựa chọn mẫu độc lập đại diện, không để doanh nghiệp chọn. Các mẫu phải là sự lựa chọn đại diện cho các loại đối tượng trong môi trường và phải đủ lớn để assessor có cơ sở đánh giá các biện pháp kiểm soát được triển khai trên toàn bộ môi trường.
- _Ví dụ:_ Windows Server 2019, Windows Server 2022, Ubuntu, Red Hat. Không được chọn mỗi Windows mà phải có đại diện của Windows, Ubuntu, Red Hat.
Đánh giá định kỳ (hằng tuần, hằng tháng, hằng năm) thì Assessor phải lấy mẫu trải đều trong cả kỳ đánh giá. Không dùng cùng 1 mẫu đại diện mỗi năm, assessor phải chọn các mẫu khác nhau cho mỗi lần đánh giá.

Việc lựa chọn mẫu phù hợp phụ thuộc vào nội dung hoặc yêu cầu đang được đánh giá: xác định đúng nhóm đối tượng cần kiểm tra, mẫu phải đại diện cho toàn bộ tổng thể; nếu môi trường có nhiều hệ điều hành khác nhau, không nên lấy mẫu chung từ tất cả server.

Nếu không có quy trình chuẩn hóa, mẫu phải được tăng kích thước để đủ cơ sở đánh giá.

Mẫu phải bao gồm mọi thành phần hệ thống. Nếu có nhiều CDE thì phải lấy mẫu từ tất cả CDE. Nếu lấy mẫu ứng dụng thì phải bao gồm mọi phiên bản (versions) và mọi nền tảng (platforms).

Kích thước của mẫu luôn phải lớn hơn 1 trừ khi tổng thể chỉ có 1 đối tượng, hoặc sử dụng biện pháp kiểm soát tự động đã được xác nhận hoạt động đúng trên toàn bộ tổng thể.

Nếu quá trình không hoạt động như mong đợi thì assessor phải tăng kích thước mẫu để tăng độ tin cậy của kết quả đánh giá.

Khi sử dụng sampling, assessor phải ghi lại lý do chọn phương pháp lấy mẫu và kích thước mẫu, xác minh và ghi nhân các quy trình/kiểm soát chuẩn được dùng để xác định kích thước mẫu, giải thích vì sao mẫu được chọn làm đại diện cho toàn bộ tổng thể.

Mức độ chuẩn hóa càng cao → mẫu càng nhỏ; mức độ đa dạng hoặc thiếu chuẩn hóa càng cao → mẫu càng lớn để đảm bảo kết quả đánh giá đáng tin cậy.

##  VII.	Mô tả các khung thời gian được sử dụng trong các yêu cầu của PCI DSS.
PCI DSS quy định 1 số hoạt động phải được thực hiện theo chu kỳ cố định. Mục đích là hoạt động thực hiện đều theo thời gian quy định và không được vượt quá khoảng thời gian đó. Doanh nghiệp được phép thực hiện thường xuyên hơn nhưng không được làm ít hơn.

Các mốc thời gian trong PCI DSS:
- Daily: Mỗi ngày trong năm (kể cả ngày nghỉ).
- Weekly: Ít nhất 1 tuần/lần.
- Monthly: Ít nhất 1 tháng/lần hoặc vào cùng 1 ngày mỗi tháng.
- Every three months (Quarterly): Ít nhất 3 tháng/lần hoặc vào cùng ngày mỗi quý.
- Every six months: Ít nhất 6 tháng/lần hoặc vào cùng ngày mỗi 6 tháng.
- Every 12 months (Annually): Ít nhất 1 năm/lần hoặc cùng ngày mỗi năm.
- Periodically: Không có chu kỳ cố định. Do doanh nghiệp tự xác định dựa trên phân tích rủi ro và phải chứng minh tần suất đó là phù hợp.
- Immediately: Thực hiện ngay tức thì, không trì hoãn.
- Promptly: Thực hiện càng sớm càng tốt trong phạm vi hợp lý. Không nhất thiết ngay lập tức nhưng không được chậm trễ không cần thiết.
- Significant change: Những thay đổi quan trọng có khả năng ảnh hưởng đến tính bảo mật của CDE:
  - Thêm phần cứng/phần mềm hoặc thiết bị mạng mới.
  - Thay thế hoặc nâng cấp phần cứng/phần mềm.
  - Thay đổi luồng hoặc lưu trữ dữ liệu tài khoản.
  - Thay đổi phạm vi CDE hoặc phạm vi đánh giá PCI DSS.
  - Thay đổi hạ tầng hỗ trợ (AD, DNS, NTP, logging, monitoring, ...).
  - Thay đổi nhà cung cấp hoặc dịch vụ bên thứ 3 hỗ trợ CDE.

Nếu doanh nghiệp có quy trình phát hiện và xử lý khi bỏ lỡ một hoạt động theo lịch, thì việc thực hiện muộn không đồng nghĩa với không tuân thủ PCI DSS, miễn là quy trình đó được thực hiện đúng.

Ngược lại, nếu không có quy trình hoặc việc bỏ lỡ lịch là do thiếu giám sát, quản lý kém hoặc sơ suất, thì doanh nghiệp không đáp ứng yêu cầu PCI DSS. Để đáp ứng lại yêu cầu, doanh nghiệp phải:
- Xây dựng hoặc xác nhận lại quy trình đảm bảo hoạt động được thực hiện đúng hạn.
- Thiết lập lại lịch thực hiện.
- Cung cấp bằng chứng rằng hoạt động đã được thực hiện đúng theo lịch mới.

## VIII.	Phương pháp triển khai và xác thực PCI DSS.
PCI DSS có 2 cách tiếp cận để triển khai và đánh giá yêu cầu:
1. Phương pháp xác định (Defined Approach).
- Thực hiện các yêu cầu và thủ tục kiểm tra được quy định sẵn trong PCI DSS.
- Doanh nghiệp triển khai các biện pháp bảo mật đúng theo yêu cầu của tiêu chuẩn.
- Assessor sẽ kiểm tra theo các thủ tục đã được xác định để xác nhận yêu cầu đã được đáp ứng.
- Nếu không thể đáp ứng một yêu cầu do ràng buộc kỹ thuật hoặc kinh doanh hợp lý, doanh nghiệp có thể sử dụng Compensating Controls (biện pháp kiểm soát bù trừ).
- Biện pháp bù trừ phải giảm thiểu rủi ro liên tương đương với yêu cầu ban đầu, phải được ghi nhận và xem xét hằng năm, được assessor xác thực.

2. Phương pháp tùy chỉnh (Customized Approach).
- Tập trung vào mục tiêu bảo mật của từng yêu cầu PCI DSS.
- Doanh nghiệp có thể tự thiết kế các biện pháp kiểm soát khác với cách quy định sẵn, miễn là vẫn đạt được mục tiêu bảo mật.
- Assessor phải xây dựng hoặc áp dụng các thủ tục kiểm tra phù hợp để xác minh biện pháp đó đáp ứng mức độ bảo mật.
- Phù hợp với các tổ chức có hệ thống quản lý rủi ro tốt và trưởng thành.
- Cách này linh hoạt hơn nhưng yêu cầu nhiều tài liệu, công sức và bằng chứng xác thực hơn.

## IX. Bảo vệ thông tin về tình trạng an ninh của một tổ chức.
- Các tài liệu liên quan đến PCI DSS có thể chứa thông tin nhạy cảm và cần được bảo vệ:
  - Sơ đồ mạng, luồng dữ liệu, cấu hình và quy tắc bảo mật.
  - Tiêu chuẩn cấu hình hệ thống.
  - Phương pháp và giao thức mã hóa/quản lý khóa.
- Doanh nghiệp phải bảo vệ các tài liệu này theo chính sách bảo mật của mình.
- TPSP phải cung cấp cho khách hàng:
  - Thông tin để theo dõi tình trạng tuân thủ PCI DSS.
  - Bằng chứng cho thấy TPSP đáp ứng các yêu cầu PCI DSS liên quan.
- QSA Company phải có quy trình bảo vệ thông tin bí mật/nhạy cảm, đảm bảo bảo mật, riêng tư và ngăn truy cập trái phép.

## X. Các phương pháp kiểm tra đáp ứng yêu cầu PCI DSS.
- Có 3 phương pháp kiểm tra chính:
  - Examine (Kiểm tra): Đánh giá bằng chứng như tài liệu, screenshot, file cấu hình, audit log, data file.
  - Observe (Quan sát): Quan sát trực tiếp hoạt động của nhân viên, hệ thống hoặc các biện pháp kiểm soát vật lý.
  - Interview (Phỏng vấn): Trao đổi với nhân viên để xác nhận hoạt động có được thực hiện và họ có hiểu quy trình hay không.
- Mục đích: Giúp Assessor xác định doanh nghiệp có đáp ứng yêu cầu PCI DSS hay không và ghi nhận phương pháp kiểm tra + kết quả kiểm tra trong báo cáo đánh giá.

## XI. Hướng dẫn và nội dung báo cáo về việc tuân thủ.
- Report on Compliance (ROC) phải được lập theo mẫu PCI DSS ROC Template do PCI SSC cung cấp.
- Việc có phải tuân thủ hoặc đánh giá PCI DSS hay không phụ thuộc vào tổ chức quản lý chương trình tuân thủ (ví dụ: payment brands, acquirers).
- Doanh nghiệp cần liên hệ các tổ chức này để biết yêu cầu về báo cáo và hướng dẫn thực hiện.


