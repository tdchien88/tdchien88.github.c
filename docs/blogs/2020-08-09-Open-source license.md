---
layout: default
parent: Blogs
title: Open-source license
last_modified_date: 2020-08-09
tags: [tag1, tag2]
summary: Summary of the article
---

# Open-source license
{: .no_toc }


## 1. Quyền quản lý
- Các license phổ biến đều có một đặc điểm chung quan trọng đó là đều được phê duyệt bởi Open Source Initiative (OSI). OSI được thành lập vào năm 1998 với mục tiêu thúc đẩy sự phát triển của phần mềm mã nguồn mở. OSI đã tạo ra Open Source Definition (OSD) để định nghĩa mã nguồn mở là gì.
- Dưới đây cách OSI nói về chính họ:
> Open Source Initiative (OSI) là một công ty phi lợi nhuận với phạm vi toàn cầu được thành lập để phổ biến và ủng hộ các lợi ích của mã nguồn mở, góp phần xây dựng cầu nối giữa các thành phần trong cộng đồng mã nguồn mở.

## 2. License
- Hầu hết các license mã nguồn mở đều bao gồm các phát biểu sau:
1. Phần mềm có thể được sửa đổi, sử dụng thương mại và phân phối.
1. Phần mềm có thể được sửa đổi và sử dụng với quyền riêng tư.
1. Phần mềm phải bao gồm license và thông tin bản quyền.
1. Tác giả phần mềm không cấp sự đảm bảo và không phải chịu trách nhiệm cho bất cứ điều gì.
- Chúng ta tìm hiểu các license phổ biến nhất theo thứ tự từ hạn chế nhất đến dễ dãi nhất (theo quan điểm của người dùng)

### a. GNU General Public License v3 (GPLv3)
- GPLv3 là một trong những license hạn chế nhất. Nó tạo ra để bảo vệ với mức độ cao cho tác giả của phần mềm.
1. Mã nguồn phải được công khai bất cứ khi nào phần mềm được phân phối.
1. Các sửa đổi của phần mềm phải được phát hành với chung một license.
1. Những thay đổi được thực hiện cho mã nguồn phải được ghi lại.
1. Nếu tài liệu được cấp bằng sáng chế đã được sử dụng trong việc tạo ra phần mềm thì nó cấp quyền cho người sử dụng nó. Nếu người dùng kiện bất ký ai về việc sử dụng tài liệu được cấp bằng sáng chế thì họ sẽ mất quyền sử dụng phần mềm.

- GPLv2 cũng rất phổ biến. Sự khác biệt so với GPLv3 là điều khoản về cấp bằng sáng chế. Điều khoản này đã được thêm vào phiên bản 3 để ngăn chặn các công ty tính phí với người dùng sử dụng bằng sáng chế của họ.
- Các dự án sử dụng GPLv3 tiêu biểu có Bash và GIMP, Linux sử dụng GPLv2.
- Ezequiel Foncubierta đã chỉ ra một điều quan trọng đối với GPL license:
> License của mã nguồn bạn tạo ra phải tương thích với license của mã nguồn mở mà bạn đang liên kết. Ví du: Nếu mã nguồn của bạn là độc quyền thì bạn sẽ không được phép sử dụng thư viện theo GPL license. Đây là sai lầm mà mọi người hay mắc phải.

### b. Apache License 2.0
- Apache License 2.0 cũng cấp nhiều sự linh hoạt hơn cho người dùng.
1. Mã nguồn không cần công khai khi phần mềm được phân phối.
1. Các chỉnh sửa của phần mềm có thể được phát hành dưới bất kỳ license nào.
1. Những thay đổi của mã nguồn phải được ghi lại.
1. Cung cấp cách bảo vệ sử dụng bằng sáng chế giống như GPLv3.
1. Cấm sử dụng tên thương hiệu được tìm thấy trong dự án.
- Các dự án phổ biến sử dụng Apache License 2.0 là Android, Apache và Swift

### c. Berkeley Software Distribution (BSD)
- BSD có hai phiên bản chính: 2-clause và 3-clause. Cả hai đều cung cấp sự linh hoạt hơn cho người dùng so với Apache License 2.0
1. Mã nguồn không cần công khai khi phần mềm được phân phối.
1. Các chỉnh sửa của phần mềm có thể được phát hành dưới bất kỳ license nào.
1. Những thay đổi của mã nguồn có thể không được ghi lại.
1. Không cung cấp vị trí rõ ràng về việc sử dụng bằng sáng chế.
1. License và thông tin bản quyền phải được đưa vào tài liệu của phiên bản đã được biên dịch của mã nguồn (khác với chỉ có trong mã nguồn).
1. BSD 3-clause nói rằng tên của tác giả và những người đóng góp không thể được sử dụng để quảng bá các sản phần có nguồn gốc từ phần mềm mà không được phép.
- Các dự án phổ biến sử dụng BSD license là Go (3-clause), Pure.css (3-clause) và Sentry (3-clause).

### d. MIT License
- MIT là một trong những license dễ chịu nhất. Nó cũng là một trong những license phổ biến nhất. MIT cung cấp sự bảo vệ rất thấp cho tác giả của phần mềm.
1. Mã nguồn không cần công khai khi phần mềm được phân phối.
1. Các sửa đổi của phần mềm có thể được phát hành theo bất kỳ license nào.
1. Những thay đổi của mã nguồn có thể không được ghi lại.
1. Không cung cấp vị trí rõ ràng về việc sử dụng bằng sáng chế.
- Các dự án phổ biến sử dụng MIT là Angular.js, jQuery, Rails, Bootstrap và nhiều dự án khác.

## 3. Cách sử dụng license trong dự án mã nguồn mở.
- Chúng ta sẽ thêm file LICENSE, LICENSE.txt hoặc LICENSE.md trong thư mục gốc của repository. Với Github thì mọi chuyện càng dễ dàng hơn:
1. Mở Github repository cần tạo license.
1. Trong thư mục gốc, chọn Create new file
1. Đặt tên cho file LICENSE
1. Chọn Choose a license template
1. Chọn license phù hợp
1. Sau đó chọn Review and submit
1. Commit file!

## 4. Kết
1. Một trong những license hạn chế nhất là GPL.
1. Một trong những license dễ dãi nhất là MIT.
1. Các license phổ biến khác là Apache License 2.0 và BSD.
1. Để sử dụng license cho dự án GitHub của chũng ta, chỉ cần tạo file LICENSE bằng các mẫu của Github.

~ Nguồn([link](https://viblo.asia/p/tim-hieu-cach-hoat-dong-cua-cac-loai-license-ma-nguon-mo-open-source-license-GrLZDknOKk0))~
{: .text-right }