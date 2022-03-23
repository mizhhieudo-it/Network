**HTTP là gì ?**

Http (HyperText Transfer Protocol) là giao thức truyền tải siêu văn bản được sử dụng trong www dùng để truyền tải dữ liệu giữa Web server đến các trình duyệt Web và ngược lại. Giao thức này sử dụng cổng 80 (port 80) là chủ yếu.

Hay bạn có thể hiểu khi bạn gõ vào 1 địa chỉ vào trình duyệt Web, lúc này trình duyệt Web sẽ gửi 1 yêu cầu qua giao thức Http đến Web server. Web server và sẽ nhận yêu cầu này và trả lại kết quả cho trình duyệt Web.

*Ta có hiêu hiểu đơn giản HTTP là phương thức truyền tải siêu văn từ client đến server*

**Các thành chính của HTTP**

 ** 1. HTTP Request **

  HTTP Request :  phía client gửi tới sever 

các thành phần trong HTTP request : 

 1.1 **Request URL** ( End Point ) : xác định điểm đích mầ http request đến có dạng http/https:// Domain/Path?queryStringKey = Value 

1.2 **Request Method** : Phương thức để đưa ra các phương thức chuẩn để gửi dữ liệu 

- Danh sách các phương sử dụng:
  
  - GET : Phương thức này dùng để truy xuất dữ liệu từ server
  
  - HEAD : Phương thức này dùng để trả về nội dung HEAD của tài nguyên mà không quan tâm đến body 
  
  - POST : Dùng gửi dữ liệu lên server
  
  - PUT : dùng ghi đè dữ liệu cũ
  
  - DELETE : Xóa tài nguyên phái server

1.3 **Request HEADER** : Có dạng Key : Value 

- Keyword :
  
  - User-Agent : đưa thông tin thiết bị gửi gói tin ( Tên brower , app v.vv)
  
  - Key Accept : Kiểu định dạng mong muốn mà Brower muốn nhận như text , json ( Chứa trong Respon )
  
  - Accept-Encoding : Kiểu định dạng mã hóa mong muốn mà Brower muốn nhận như gzip v..v ( Chứa trong Respon )
  
  - Content-type: Định dạng kiểu định dạng được sử dụng trong body request
  
  - Content-Lenght : Độ dài tính dài tính bằng byte của body request
  
  - Connection : Yêu cầu duy trì kết nối với server (Value : keepLine /cLOSE)
  
  - Cache-Control : Duy trì tài nguyên trong những lần tiếp theo 

1.4 Request Body : chứa nội dung thông tin chứa dữ liệu cho Sever xử lý 

Safe : Độ an toàn ( khi có request nhiều lần nhưng không làm cho data trong server thay đổi   )

Idempotent : Tính bất biến ( thật hiện request nhiều lần nhưng respon cùng trả về 1 kết quá)

Cache : Dùng lại t rong những lần tiếp theo

| Method | Request  | Respon | safe | Idempotent | Cacheable |
| ------ | -------- | ------ | ---- | ---------- | --------- |
| GET    | Optional | Yes    | yes  | yes        | yes       |
| HEAD   | Optional | no     | yes  | yes        | yes       |
| POST   | Yes      | yes    | No   | no         | yes       |
| PUT    | yes      | yes    | no   | yes        | no        |
| Delete | optional | yes    | no   | yes        | yes       |

**2 . HTTP Respon**

- Respon Status Code :  Mã trạng thái mà serve trả về cho client (số nguyên có 3 chữ số )

            1XX : thông báo cho đã chấp nhận yêu cầu hoặc tiếp tục thông tin gì đó

            2XX: Thông báo thành công , ( server xác nhận và thực thi)

            3XX: Client phải thực  thi hành động bổ xung để hoàn thành nghiệm vụ server             (Cache )

            4XX : Nhóm mã thông báo lỗi từ phía client 

            5XX : Nhóm mã thống báo lỗi từ phía server

- Respon Header : tương tự như Request Header

- Respon Body : Text,Javascript,CSS,JSON,XML,HTML




