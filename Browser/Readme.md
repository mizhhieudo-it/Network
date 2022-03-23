 **Cách Browser hoạt động**

Các công việc chủ yếu của một trình duyệt sẽ gồm:

- Phân giải DNS
- Truyền HTTP
- Hiển thị
- Lặp lại các công việc trên

### Phân giải DNS

Quá trình này giúp đảm bảo khi một người dùng nhập vào địa chỉ, trình duyệt sẽ biết được máy chủ nào kết nối với địa chỉ đó. Trình duyệt sẽ liên hệ với một máy chủ DNS để chuyển `google.com` thành `216.58.207.110`, và một địa chỉ IP mà trình duyệt có thể kết nối tới.

### Trao đổi HTTP

Sau khi trình duyệt đã xác định được máy chủ nào sẽ lắng nghe các request nó gửi tới, nó sẽ khởi tạo một kết nối TCP và bắt đầu trao đổi HTTP. Trao đổi HTTP là cách một trình duyệt giao tiếp với server, gửi cho server các yêu cầu và đợi server phản hồi lại.

HTTP là tên một giao thức phổ biến được dùng để giao tiếp trên web, các trình duyệt chủ yếu sử dụng HTTP để giao tiếp với server. Một trao đổi HTTP thường có **client** (trình duyệt) gửi **request** và **server** phản hồi lại bằng một **response**

Ví dụ sau khi trình duyệt đã kết nối thành công tới máy chủ của `google.com`, nó sẽ gửi một request như thế này

```none
GET / HTTP/1.1
Host: google.com
Accept: */*
```

- `GET / HTTP/1.1:` trình duyệt yêu cầu server lấy các file từ thư mục `/`, và sử dụng giao thức `HTTP/1.1` để trao đổi
- `Host: google.com`: Đây là **header bắt buộc duy nhất** của HTTP/1.1. Vì một server có thể có nhiều tên miền khác nhau (`google.com`, `google.co.uk`), phía client chỉ rõ request sẽ gửi tới host nào
- `Accept: */*`: đây là một header tùy chọn, browser nói với server rằng nó sẽ chấp nhận bất kỳ loại response nào. Server có thể trả về response với bất cứ định dạng nào: JSON, XML hoặc HTML.

Sau khi browser đã gửi request xong, server sẽ gửi về response

```none
HTTP/1.1 200 OK
Cache-Control: private, max-age=0
Content-Type: text/html; charset=ISO-8859-1
Server: gws
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
Set-Cookie: NID=1234; expires=Fri, 18-Jan-2019 18:25:04 GMT; path=/; domain=.google.com; HttpOnly
<!doctype html><html">
...
...
</html>
```

Trong gói tin trả về kia server cho biết rằng request đã được thực hiện thành công(`200 OK`), server nào thực hiện xử lý request(`Server: gws`), các chính sách `X-XSS-Protection` của phản hồi, vân vân. Hiện tại mọi người chưa cần hiểu hết từng dòng một trong response kia. Chúng ta sẽ bàn đến nó sau khi đề cập tới giao thức HTTP ở riêng một bài khác. Tất cả những gì chúng ta cần nhớ tính tới thời điểm này là client và server thực hiện trao đổi thông tin bằng giao thức HTTP

### Hiển thị

Một website sẽ như thế nào nếu tất cả những gì chúng hiển thị chỉ là những ký tự vô nghĩa? Đó là lí do một trình duyệt hoàn chỉnh cần có chức năng render.

```none
<!doctype html><html">
...
...
</html>
```

Trong phần body của response trả về, server sẽ gửi theo cách mà response đó được hiển thị như thế nào trong header `Content-Type`. Trong ví dụ của chúng ta content-type là `text/html`, nên response trả về sẽ chứa các thẻ của HTML. Và đây là lúc trình duyệt thực hiện nhiệm vụ của mình. Nó sẽ phân tách đoạn HTML, tải thêm các tài nguyên đính kèm (các file Javascript hoặc CSS), và hiển thị chúng cho người dùng. Kết quả là chúng ta có một trang web mà ai cũng có thể đọc được. Để hiểu rõ hơn quá trình browser render một trang web, mọi người có thể đọc thêm bài viết [này](https://github.com/alex/what-happens-when), nó giải thích rất kĩ các cơ chế đằng sau quá trình render.

Về vấn đề bảo mật, những kẻ tấn công có thể **dễ dàng tìm ra các lỗ hổng trong quá trình trao đổi HTTP và render** của một trình duyệt. Hiểu rõ về hai chức năng này của trình duyệt sẽ giúp bạn có thể tăng cường bảo mật cho các ứng dụng web của bạn.
