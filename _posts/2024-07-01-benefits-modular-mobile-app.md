---
layout:     post
title:      Mobile Modular Architecture
subtitle:   The Benefits of a Modular Architecture in Mobile Development
author:     NDA
header-img: img/posts/header-ava.avif
header-mask: 0.5
catalog:    true
tags:
    - Mobile Development
---

>Việc phát triển ứng dụng trên nền tảng di động ngày nay vượt xa so với một thập kỷ trước về độ phức tạp và chức năng. Thời điểm bắt đầu, các ứng dụng từng là các dự án đơn giản với một vài tính năng giờ đã phát triển thành các hệ thống tinh vi kết hợp mọi thứ từ xác thực sinh trắc học và AI đến tích hợp camera tiên tiến. Sự phát triển này đòi hỏi một chiến lược kiến ​​trúc quản lý hiệu quả sự phức tạp trong khi vẫn duy trì cơ sở mã nguồn chất lượng tốt.

>Trong bài viết này, chúng ta sẽ khám phá giải pháp kiến ​​trúc mạnh mẽ cho thách thức này: kiến ​​trúc module hoặc có thể cấu hình trong phát triển di động, lấy cảm hứng từ kiến ​​trúc microservice của các nền tảng Backend.

# Kiến trúc module là gì?
Tương tự như microservices, chúng ta phân tách một ứng dụng lớn thành các thư viện di động tập trung nhỏ, mỗi thư viện giải quyết một mảng nghiệp vụ hoặc chức năng cụ thể. Kiến trúc module này cho phép xây dựng nhiều ứng dụng bằng các thành phần có thể tái sử dụng này, đảm bảo rằng mỗi module vẫn được kết nối lỏng lẻo. Điều này tối đa hóa tính linh hoạt, khả năng kiểm tra và khả năng tương thích cho từng thành phần.

Hãy cùng tìm hiểu sâu hơn về lợi ích của kiến ​​trúc module trong phát triển di động.

Câu hỏi thứ nhất đặt ra là:

# Tại sao nên sử dụng kiến ​​trúc module trong phát triển di động?
## Chia tách mối quan tâm với kiến trúc Mô-đun
Việc áp dụng kiến ​​trúc module trong phát triển di động tạo ra sự tách biệt rõ ràng giữa các mối quan tâm. Điều này cho phép mở rộng thêm từ mã nguồn đến cấu trúc tổ chức của dự án. Mỗi module hoạt động như một đơn vị độc lập, đại diện cho một phạm vi trách nhiệm riêng biệt, được phát triển và duy trì riêng biệt. Điều này không chỉ nâng cao khả năng đọc và quản lý dự án mà còn hợp lý hóa sự cộng tác và gỡ lỗi. Do đó, triết lý thiết kế kiến ​​trúc module tạo ra một hệ thống gắn kết, trong đó ranh giới thành phần được thể hiện ngay lập tức, tức là chúng ta có thể hiểu tổng quan cấu trúc dự án mà không cần đọc sâu vào mã nguồn

## Modular Architecture nâng cao khả năng tái sử dụng và bảo trì mã nguồn
Kiến trúc module làm rõ cấu trúc dự án và thúc đẩy đáng kể khả năng tái sử dụng và bảo trì mã. Bằng cách phân chia ứng dụng thành các module, chúng ta tạo ra các thành phần có thể tái sử dụng có thể được tích hợp trên các phần khác nhau của ứng dụng hoặc thậm chí trong các dự án hoàn toàn mới. Việc tái sử dụng mã này giảm thiểu công việc dư thừa, cho phép các nhà phát triển tập trung vào đổi mới thay vì phát minh lại bánh xe cho mỗi tính năng mới.

Hơn nữa, kiến ​​trúc module đơn giản hóa việc bảo trì và cập nhật ứng dụng. Các module hoạt động độc lập, cho phép áp dụng các cải tiến hoặc sửa lỗi cho một module mà không vô tình làm gián đoạn các module khác. Sự tách biệt này đơn giản hóa việc thử nghiệm, cho phép xác thực có mục tiêu các thay đổi, đảm bảo ứng dụng ổn định và đáng tin cậy hơn. Do đó, phương pháp tiếp cận module cung cấp một cơ sở mã không chỉ chắc chắn hơn mà còn linh hoạt hơn, cho phép ứng dụng thích ứng nhanh chóng với các yêu cầu mới hoặc các tiến bộ công nghệ.

## Kiến trúc module tăng cường khả năng kiểm thử
Một trong những lợi thế lớn nhất của việc áp dụng kiến ​​trúc module trong các dự án phát triển di động lớn là khả năng kiểm thử được cải thiện. Trong các dự án di động nguyên khối lớn, thời gian xây dựng có thể rất đáng kể, thường dẫn đến quy trình làm việc không hiệu quả.

Ví dụ, trong trường hợp bạn đang làm việc trên một ứng dụng nền tảng Xamarin lớn, không có khả năng *Hot Reload*. Bất kỳ hành vi sai trái nào của UI cũng sẽ yêu cầu xây dựng toàn bộ ứng dụng và trải qua toàn bộ luồng. Và nếu luồng này phụ thuộc vào các cuộc gọi web do nhóm khách hàng duy trì, thì chúng ta đang phải đối mặt với một quy trình cực kỳ tốn thời gian và không hiệu quả.

>Hot Reload là tính năng cho phép các nhà phát triển xem ngay kết quả của những thay đổi mã mới nhất mà không làm mất trạng thái của ứng dụng. Đây là một sự thay đổi đáng kể so với mô hình truyền thống “Code, Compile, Run” model.

## Ưu điểm của Kiến trúc Mô-đun trong Kiểm thử Di động

Việc sử dụng kiến ​​trúc module cho các dự án phát triển di động mang lại một loạt lợi thế quan trọng về mặt kiểm thử:

* **Isolated Testing - Kiểm thử độc lập**
Với kiến ​​trúc module, chúng ta có thể mô phỏng mọi phụ thuộc dữ liệu của một module và thử nghiệm nó như một ứng dụng độc lập. Sự cô lập này cho phép tập trung thử nghiệm vào các chức năng cụ thể mà không cần phải chạy toàn bộ ứng dụng.

* **Reduced Build Times - Giảm thời gian build**
Việc xây dựng toàn bộ ứng dụng cho mọi thay đổi là không cần thiết, giúp giảm đáng kể thời gian thử nghiệm đầu cuối. Hiệu quả này dẫn đến chu kỳ phát triển nhanh hơn và lặp lại nhanh hơn, nó quan trọng để duy trì năng suất cao.

* **Stable Testing Environment - Môi trường thử nghiệm ổn định**
Việc tách rời các module giúp giảm thiểu rủi ro một thành phần ảnh hưởng đến thành phần khác, đảm bảo các thử nghiệm đáng tin cậy hơn và theo dõi lỗi dễ dàng hơn.

* **Parallel Development and Testing - Song song quá trình phát triển và kiểm thử**
Các nhóm có thể phát triển và thử nghiệm nhiều module khác nhau cùng lúc mà không cần chờ cơ sở mã chung ổn định, giúp đẩy nhanh quá trình phát triển và cho phép quy trình làm việc năng động, linh hoạt.

Kiến trúc module tạo ra quy trình phát triển di động hiệu quả hơn, đáng tin cậy hơn và có khả năng mở rộng hơn, giảm thiểu rủi ro liên quan đến kiến ​​trúc đơn khối. Bằng cách tập trung vào tính module, chúng ta cải thiện cả giai đoạn phát triển và thử nghiệm, dẫn đến chất lượng phần mềm tổng thể tốt hơn.

![](https://www.datocms-assets.com/46256/1719403649-screenshot-2024-06-26-at-14-07-17.png)

# Định nghĩa các module trong phát triển di động
Khi phát triển các module ứng dụng, sự hợp tác với các chuyên gia trong lĩnh vực là rất quan trọng để nắm bắt đầy đủ các chức năng khác nhau trong một tổ chức. Quan hệ đối tác này cho phép hiểu rõ cách phân đoạn ứng dụng một cách hợp lý. Tài liệu về các vai trò, kết hợp với các yêu cầu cụ thể của từng lĩnh vực, nên được giải quyết như một quy trình lặp đi lặp lại, cho phép tinh chỉnh liên tục phù hợp với nhu cầu đang phát triển của tổ chức, đảm bảo mỗi module được xác định rõ ràng và hướng đến mục đích.

# Module Cơ sở - Base Module
Trong kiến ​​trúc module, chúng ta sử dụng một module cơ sở nền tảng. Hãy coi đây là mã di truyền của ứng dụng — cốt lõi mà mọi module khác kế thừa. Mô-đun cơ sở này chứa tất cả các tính năng được chia sẻ, không phụ thuộc vào miền, bao gồm các thành phần thiết kế và điều khiển chung. Việc tập trung các khía cạnh chung này sẽ thiết lập giao diện và cảm nhận nhất quán trong toàn bộ ứng dụng. Mỗi module chuyên biệt, được xây dựng trên cơ sở này, vốn áp dụng các đặc điểm chung này, hợp lý hóa quá trình phát triển và đảm bảo rằng các thay đổi đối với các khía cạnh cơ bản chỉ cần được thực hiện một lần, lan tỏa khắp toàn bộ ứng dụng.

# Tạo module đầu tiên
Sau khi module cơ sở được đưa vào vị trí, bước tiếp theo là tạo module có thể cấu hình đầu tiên. Cấu trúc mô phỏng kiến ​​trúc phân lớp cổ điển (các dự án Dữ liệu, Miền và Trình bày), với một dự án Kiểm tra bổ sung để tạo điều kiện cho việc kiểm tra module. Dự án Kiểm tra này gọi trực tiếp module. Đây là một ứng dụng di động đơn giản, thường bao gồm một nút để khởi động thành phần. Vai trò của nó là cung cấp các định nghĩa giả cho tất cả các phụ thuộc bắt buộc của module, cho phép triển khai module trên thiết bị hoặc trình giả lập để kiểm tra.

## Cấu trúc dự án cho kiến ​​trúc module
* **Data Project:**
    * Xác định các thực thể dữ liệu và giao diện dữ liệu bắt buộc.

* **Domain Project:**
    * Chứa logic kinh doanh cốt lõi và mô hình miền.
    * Xác định các trường hợp sử dụng và quy tắc kinh doanh hoạt động trên dữ liệu.

* **Presentation Project:**
    * Quản lý các thành phần UI và logic trình bày.
    * Bao gồm các chế độ xem và tiện ích liên quan đến UI.

* **Test Project:**
    * Dự án độc lập tương tác trực tiếp với module.
    * Cung cấp các triển khai giả cho các phụ thuộc.
    * Tạo điều kiện cho việc thử nghiệm riêng biệt chức năng của module.

## Xác định các phụ thuộc dữ liệu trong kiến ​​trúc module
Đối với mọi thư viện có thể cấu hình, việc xác định các phụ thuộc dữ liệu thông qua hợp đồng (ví dụ: giao diện) thay vì mã hóa cứng các nguồn dữ liệu là rất quan trọng. Điều này đảm bảo thư viện không phụ thuộc vào nguồn gốc dữ liệu, cho dù từ cơ sở dữ liệu cục bộ hay API web. Tiêm phụ thuộc cung cấp các triển khai dữ liệu phù hợp cho module.

Cách tiếp cận này cho phép người dùng quyết định nguồn dữ liệu. Bằng cách đảm bảo thư viện có thể cấu hình chỉ quan tâm đến loại dữ liệu mà nó yêu cầu, thay vì nguồn gốc của dữ liệu, việc chế nhạo các hợp đồng dữ liệu và mô phỏng các kịch bản chức năng dự kiến ​​sẽ đơn giản hóa. Cách tiếp cận có thể kiểm tra và module này cải thiện đáng kể tính linh hoạt và khả năng bảo trì của cơ sở mã.

![](https://www.datocms-assets.com/46256/1719403868-screenshot-2024-06-26-at-14-10-59.png)

# Sử dụng Mô-đun hoặc Thành phần trong Phát triển Di động
Việc tích hợp một module đã phát triển vào ứng dụng của bạn rất đơn giản do có các giao diện và phụ thuộc được xác định rõ ràng:
* Nhập Mô-đun: Bao gồm module trong dự án của bạn. Điều này thường liên quan đến việc thêm một phụ thuộc vào cấu hình dựng của dự án.
* Tiêm Phụ thuộc: Sử dụng tiêm phụ thuộc để cung cấp các nguồn dữ liệu và dịch vụ cần thiết mà module yêu cầu. Điều này giúp thành phần không biết về nguồn gốc dữ liệu của mình, thúc đẩy tính linh hoạt và khả năng tái sử dụng.
* Khởi tạo Mô-đun: Thiết lập bất kỳ cấu hình hoặc trạng thái ban đầu nào cần thiết cho module, chẳng hạn như dữ liệu ban đầu hoặc cài đặt cụ thể.
* Sử dụng API của Mô-đun: Tương tác với module thông qua API công khai của module, thường bao gồm các phương thức để bắt đầu luồng trả về dữ liệu hoặc tích hợp chế độ xem với ứng dụng của bạn.

# Kết luận: Tương lai của Phát triển Di động nằm ở Kiến trúc Mô-đun
Việc áp dụng kiến ​​trúc module trong phát triển di động mang lại nhiều lợi ích, nâng cao cả quy trình phát triển và sản phẩm cuối cùng. Bằng cách phân chia các ứng dụng thành các thành phần nhỏ hơn, dễ quản lý hơn, chúng tôi thực thi việc tách biệt các mối quan tâm, thúc đẩy khả năng tái sử dụng mã và cải thiện đáng kể khả năng bảo trì. Các module cho phép thử nghiệm riêng biệt, giảm thời gian xây dựng và tạo ra môi trường thử nghiệm ổn định, cuối cùng dẫn đến quy trình phát triển hiệu quả và đáng tin cậy hơn.

Src: https://acagroup.be/en/blog/the-benefits-of-a-modular-architecture-in-mobile-development/