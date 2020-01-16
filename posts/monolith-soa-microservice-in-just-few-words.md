---
title: Cùng tìm hiểu một chút về Monolith/SOA/MicroService
description: Cùng tìm hiểu một chút về Monolith/SOA/MicroService
date: 2020-01-15
tags:
  - microservice
  - monolith
  - monolithic
  - soa
  - architecture
layout: layouts/post.njk
---

Việc lựa chọn một architecture phù hợp cho một dự án luôn là một bài toán khó. Nó có ảnh hưởng trực tiếp đến việc maintain, khả năng scale sau này của product.

Nhiều năm trước, Twitter đã từng phải đối mặt với một bài toán đau đầu, đó là làm thế nào để hệ thống của họ có thể đáp ứng được hàng trăm triệu người dùng. Và sự lựa chọn của Twitter, tại thời điểm đó, là đập đi làm lại cả hệ thống.
Bạn có thực sự muốn đối mặt với một trường hợp tương tự? Tôi tin là không.
Vậy tại sao bạn không trang bị cho mình thêm những kiến thức cơ bản nhất, ngay bây giờ, ngay lúc này, bằng cách đọc bài viết sau đây của tôi?

##### Monolith/SOA/MicroService, mấy từ đó có nghĩa gì vậy? Google Translate giùm tôi (người đọc) có được không?
1. Monolithic: về mặt từ vựng, từ này có nghĩa là `Nguyên Khối`, và Monolithic Architecture có nghĩa là Thiết Kế Nguyên Khối
2. SOA: đây là viết tắt của cụm từ Server Oriented Architecture, dịch ra tiếng Việt thì nó là `mô hình hướng server`, hiểu đơn giản là thiết kế này đặt trọng tâm là server, dịch là vậy, còn để đi sau vào chi tiết hơn thì chúng ta sẽ tham khảo bài viết tôi sẽ viết bên dưới.
3. Microservice: bây giờ cụm từ này mình sẽ tách nó ra làm đôi, nó sẽ thành Micro và Service. Từ Service nó có nghĩa là dịch vụ, còn Micro thì dịch ra nó hơi củ chuối nhưng các bạn có thể hiểu nôm na là nó rất nhỏ, nó vi mô. Ghép lại thì mình có thể hiểu MicroService là `mô hình tập hợp nhiều dịch vụ, mỗi dịch vụ phục vụ một mục đích (có thể là duy nhất)`, và domain business của nó là rất nhỏ.

Một ứng dụng, coi như là một dự án đủ lớn, chắc chắn sẽ bao gồm những business nhỏ hơn, ví dụ như đối với một programmer như chúng ta, để hoàn thành được dự án thì mình cần thực hiện được một chuỗi các công việc như lấy requirement, thảo luận, sửa spec, code, review code, test. Tôi sẽ đề cập đến những business thực sự nhỏ như vậy, ngay sau đây.

##### Giải thích ngắn gọn
Tôi sẽ nói về microservice trước, bởi vì tôi cảm thấy việc nói về nó trước sau đó đến Monolithic, SOA giúp tôi mường tượng rõ ràng hơn về sự khác nhau giữa chúng.
1. MicroService Architecture **Do one thing and Do it well**, đối với mô hình này, tất cả các thành phần của nó được chia nhỏ tới mức mà mỗi service chỉ thực hiện một công việc duy nhất.
2. SOA **Group related things and Do them well**, đối với mô hình này, những thứ, những công việc có liên quan được group thành một cụm business để xử lý. Chính vì ở kiến trúc này, các module được tích hợp liền mạch cho nên rất dễ để có thể quản lý và tái sử dụng.
3. Một mô hình nguyên khối là một mô hình mà tất cả các thành phần của nó được gói gọn trong một application _duy nhất_. Dù các thành phần đó là giao diện, truy vấn, lưu trữ dữ liệu, business/logic code,... thì Tất cả đều được gói gọn trong một cục duy nhất, nó nguyên khối. Và đó là Monolothic Architecture.

##### Chúng phù hợp được sử dụng khi nào?
1. Monolithic Architecture: Thích hợp cho các dự án nhỏ, và cực nhỏ như kiểu các tools, các local app thực hiện những các tác vụ cơ bản, có thể cài đặt cực nhanh, tăng khả năng thân thiện với người dùng.
2. Server Oriented Architecture: Thích hợp với các dự án business, không yêu cầu khả năng scale lớn
3. Microservice Archiecture: Thích hợp với các dự án có quy mô lớn và cực lớn, đòi hỏi khả năng scale cực mạnh
_Đối với cá nhân tôi mà nói, với mỗi bài toán, tôi sẽ chọn một mô hình triển khai khác nhau phù hợp tình hình thực tế, và tôi cũng ko ngại phải migrate giữa các thiết kế mô hình trên. Xin đừng mang dao mổ trâu đi giết kiến, đừng để bị over-engineering, tạo ra các bottle-neck ko đáng có, cuộc sống của bạn sẽ khó khăn hơn rất nhiều_
 
###### Bài viết này chỉ ngắn gọn như vậy để đảm bảo khả năng tiếp thu và thẩm thấu của bạn và của tôi. Chúc các bạn sớm ngộ được tâm pháp.

##### Brain Storm:
Những điều gì cần xem xét khi lựa chọn mô hình triển khai?