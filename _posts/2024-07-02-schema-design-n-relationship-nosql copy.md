---
layout:     post
title:      Thiết kế lược đồ và mối quan hệ trong cơ sở dữ liệu dựa trên tài liệu NoSQL
subtitle:   
author:     NDA
header-img: img/post/bg15.png
header-mask: 0.5
catalog:    true
tags:
    - NoSQL
---

>Trong những năm gần đây, một số ứng dụng khác nhau được gọi là cơ sở dữ liệu NoSQL đã trở nên phổ biến. Nhưng sự khác biệt giữa cơ sở dữ liệu SQL và NoSQL là gì khi nói đến Thiết kế lược đồ và Mối quan hệ? Bài viết này mô tả về Lược đồ và mối quan hệ trong cơ sở dữ liệu NoSQL dựa trên tài liệu.

Bằng cách tránh xa cơ sở dữ liệu quan hệ, cơ sở dữ liệu NoSQL cung cấp một cách để làm việc tự do hơn nhiều với dữ liệu và cung cấp mức độ linh hoạt và đơn giản cao. Có một số loại cơ sở dữ liệu NoSQL. Bất kể loại cơ sở dữ liệu nào, mô hình hóa dữ liệu và thiết kế lược đồ đều là những khái niệm quan trọng trong bất kỳ ứng dụng nào. Tuy nhiên, đôi khi người ta nói rằng NoSQL không có lược đồ để mô hình hóa dữ liệu, nhưng đây là một quan niệm sai lầm. Bài viết này tập trung vào thiết kế lược đồ trong phạm vi của cơ sở dữ liệu NoSQL dựa trên tài liệu.

# Thiết kế lược đồ và mối quan hệ trong NoSQL dựa trên tài liệu
Cơ sở dữ liệu NoSQL được phát triển để thoát khỏi các hàng và cột được sử dụng trong cơ sở dữ liệu quan hệ. Tuy nhiên, một quan niệm sai lầm phổ biến là tin rằng cơ sở dữ liệu NoSQL không áp dụng bất kỳ loại mô hình dữ liệu nào. Thiết kế lược đồ hoặc mô hình dữ liệu cho NoSQL là một vấn đề quan trọng trong bất kỳ ứng dụng nào. Lược đồ là mô tả hữu ích về cách dữ liệu nên được tổ chức bên trong cơ sở dữ liệu. Sau khi chọn cơ sở dữ liệu NoSQL, nhiệm vụ tiếp theo là thiết kế lược đồ cho cơ sở dữ liệu đã chọn.

# Chuẩn hóa (tham chiếu) hay phi chuẩn hóa (nhúng) dữ liệu?
Vì NoSQL hoạt động với các bộ sưu tập và tài liệu, nên điều quan trọng là phải hiểu các khái niệm về chuẩn hóa và phi chuẩn hóa. Hai cách tiếp cận này xác định cách dữ liệu được lưu trữ trong cơ sở dữ liệu NoSQL.

![](https://blog.usu.com/hs-fs/hubfs/Normalization%20Denormalization.png?width=500&name=Normalization%20Denormalization.png)

**Chuẩn hóa** - có nghĩa là dữ liệu được lưu trữ trong nhiều bộ sưu tập bằng cách tham chiếu giữa chúng. Dữ liệu được định nghĩa một lần và giúp cập nhật dễ dàng hơn. Khi nói đến việc đọc dữ liệu, nhược điểm của chuẩn hóa là rõ ràng. Nếu bạn muốn truy xuất dữ liệu từ nhiều bộ sưu tập, bạn cần thực hiện nhiều truy vấn. Do đó, quá trình đọc chậm hơn.

**Phi chuẩn hóa** - Lưu trữ một lượng lớn dữ liệu lồng nhau trong một tài liệu. Mô hình này thực hiện đọc tốt hơn nhưng chậm hơn đối với việc chèn và cập nhật. Phương pháp lưu trữ dữ liệu này chiếm nhiều bộ nhớ hơn.

# Cấu trúc dữ liệu trong cơ sở dữ liệu NoSQL Document-base
Cấu trúc của cơ sở dữ liệu dựa trên tài liệu khác với cơ sở dữ liệu quan hệ, vốn có vấn đề với việc lưu trữ dữ liệu bên ngoài các cột và hàng. Thay vì các bảng và hàng, cơ sở dữ liệu dựa trên tài liệu NoSQL sử dụng các bộ sưu tập và tài liệu, mỗi tài liệu là một tệp json duy nhất có thể là json đơn giản hoặc lồng nhau. Chúng thích ứng theo cách linh hoạt với nhiều loại dữ liệu khác nhau, thay đổi nhu cầu ứng dụng và mô hình dữ liệu.

![](https://blog.usu.com/hs-fs/hubfs/NoSQL.png?width=1198&name=NoSQL.png)

# Nhúng hay tham chiếu; phương pháp mô hình hóa dữ liệu nào tốt hơn trong cơ sở dữ liệu NoSQL dựa trên tài liệu?
Có thể thực hiện mô hình lược đồ dựa trên tài liệu theo hai cách cho mọi phần dữ liệu. Bạn có thể nhúng dữ liệu trực tiếp hoặc tham chiếu dữ liệu khác. Hãy xem xét ưu và nhược điểm của cả hai tùy chọn trong mô hình lược đồ.

## Phương pháp nhúng

Đối với cơ sở dữ liệu dựa trên Tài liệu, lồng nhau hoặc nhúng có nghĩa là phi chuẩn hóa các thực thể bằng cách lồng một thực thể vào một thực thể khác dưới dạng một tài liệu phụ. Trong Hình 2, tài liệu được tạo từ năm thực thể (Hình 3). Năm thực thể này được phi chuẩn hóa để lồng vào một tài liệu duy nhất.

![](https://blog.usu.com/hs-fs/hubfs/Embedding%20approach.png?width=1386&name=Embedding%20approach.png)

Phương pháp nhúng có một số ưu điểm và nhược điểm sẽ được xem xét trong các bước tiếp theo.

**Ưu điểm**
* Người ta có thể lấy tất cả thông tin có liên quan chỉ bằng một truy vấn.
* Tránh triển khai lệnh nối trong mã ứng dụng hoặc sử dụng lệnh populate/lookup (Join).
* Cập nhật thông tin liên quan dưới dạng một hoạt động nguyên tử duy nhất. Theo mặc định, tất cả các hoạt động CRUD trên một tài liệu duy nhất đều tuân thủ ACID.
**Hạn chế**
Có giới hạn kích thước tài liệu trong cơ sở dữ liệu dựa trên tài liệu - ví dụ MongoDB có giới hạn 16 MB cho một mục nhập tài liệu duy nhất. Ngoài ra, mức độ nhúng của các tài liệu phụ là một vấn đề khác cần được lưu ý. Ví dụ, MongoDB hỗ trợ nhúng dữ liệu cho đến độ sâu 100. Nếu nhúng nhiều dữ liệu bên trong một tài liệu duy nhất, người ta nên cân nhắc đến giới hạn này.

## Phương pháp tham chiếu
Nhúng là phương pháp đảm bảo hành vi tốt nhất và tính nhất quán của dữ liệu trong nhiều trường hợp. Nhưng trong một số trường hợp, việc có một mô hình chuẩn hóa sẽ hoạt động tốt hơn. Trên thực tế, một lập luận rõ ràng cho việc chuẩn hóa bộ sưu tập dữ liệu của bạn thành nhiều bộ sưu tập là tính linh hoạt mà nó cung cấp khi thực hiện các truy vấn.

Tham chiếu tài liệu và bộ sưu tập trong một tài liệu khác bằng ID đối tượng trong phương pháp này là một phương pháp phổ biến và giống với tính năng khóa chính/khóa ngoại được biết đến từ cơ sở dữ liệu quan hệ. Theo cách này, có thể phân chia dữ liệu và thiết lập mối quan hệ giữa các dữ liệu. Trong Hình 4, dữ liệu được chuẩn hóa và chia thành hai bộ sưu tập với tham chiếu của mối quan hệ. Khi đọc và truy xuất dữ liệu, có một số phương pháp tương tự như hàm JOIN trong SQL.

![](https://blog.usu.com/hs-fs/hubfs/Referencing%20approach.png?width=1025&name=Referencing%20approach.png)

Phương pháp tham chiếu cũng có một số ưu điểm và nhược điểm sẽ được xem xét ở phần tiếp theo.

**Ưu điểm**
* Khi chia nhỏ dữ liệu, người ta sẽ có các tài liệu nhỏ hơn.
* Truy xuất dữ liệu có chọn lọc, vì trong hầu hết các truy vấn, không cần thiết phải truy xuất tất cả dữ liệu của một bộ sưu tập
* Tránh trùng lặp dữ liệu.
**Hạn chế**
Để truy xuất dữ liệu trong các tài liệu được tham chiếu, ít nhất hai truy vấn hoặc hàm populate/lookup (join) cần thiết để lấy dữ liệu.
Vì vậy, chúng ta đã thấy các cách tiếp cận đối với thiết kế lược đồ trong cơ sở dữ liệu dựa trên tài liệu, nhưng vẫn còn một câu hỏi; cách tiếp cận nào được sử dụng trong một trường hợp sử dụng cụ thể?

# Phần kết luận
Trong cơ sở dữ liệu dựa trên tài liệu, cách bạn mô hình hóa dữ liệu của mình hoàn toàn phụ thuộc vào các mẫu truy cập dữ liệu ứng dụng và kế hoạch kinh doanh của bạn. Bạn muốn cấu trúc dữ liệu của mình để phù hợp với cách ứng dụng của bạn truy vấn và cập nhật dữ liệu. Tuy nhiên, vẫn có một số khuyến nghị chung cho dữ liệu liên quan có thể được xem xét như bên dưới.

**Khuyến nghị chung cho mô hình hóa lược đồ và mối quan hệ:**

* Mối quan hệ một-một: mô hình nhúng được ưa chuộng
* Mối quan hệ một đến vài: mô hình nhúng được ưu tiên
* Mối quan hệ một-nhiều: mô hình tham chiếu được ưu tiên
* Mối quan hệ nhiều-nhiều: mô hình tham chiếu được ưu tiên
* Ưu tiên nhúng trừ khi có lý do bắt buộc không nhúng
* Nhu cầu truy cập vào một đối tượng riêng lẻ là một lý do thuyết phục để không nhúng nó
* Tránh các phép nối và điền (tra cứu) nếu có thể, nhưng đừng sợ nếu chúng có thể cung cấp thiết kế lược đồ tốt hơn
* Mảng không nên phát triển không giới hạn. Nếu có hơn vài trăm tài liệu ở nhiều mặt, đừng nhúng chúng; nếu có hơn vài nghìn tài liệu ở nhiều mặt, đừng sử dụng mảng tham chiếu ObjectID.

## Tài liệu tham khảo:
https://www.arangodb.com/docs/stable/data-modeling-concepts.html
https://www.guru99.com/nosql-tutorial.html
https://www.mongodb.com/docs/manual/ lõi/data-modeling-introduction
https://dev.to/damcosset/mongodb-normalization-vs-denormalization