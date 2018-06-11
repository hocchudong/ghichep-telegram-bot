# Ghi chép ban đầu về Telegram Bot
- [1. Khái niệm về Bot](#khainiem)

- [2. Bot hoạt động như thế nào?](#hoatdong)

- [3. Các bước tạo ra một con Bot](#creatbot) 

- [4. Tài liệu tham khảo](#tailieu)

## Telegram_Bot

Bài viết này mình sẽ hướng dẫn các bạn cách tiếp cận với Bot của telegram. Qua đó, có thể giúp những người mới bắt đầu có một cái nhìn rõ hơn về cách sử dụng bot trong telegram  

<a name=khainiem></a>
### 1. Khái niệm về Bot

Như mở đầu mình có đề cập tới ``Bot``. Vậy Bot là gì? Được hiểu như thế nào?

Bot:

- Trong telegram: Nó là ứng dụng của bên thứ ba sử dụng trong telegram. Người dùng có thể tương tác với Bot bằng cách gửi tin nhắn đến nó hoặc sử dụng câu lệnh... Bạn có thể tạo ra một con Bot cho riêng mình từ BotFather của telegram và điều khiển(ra lệnh) nó thực hiện một công việc cụ thể thông qua API (VD: tự động gửi tin nhắn cho một người dùng nào đó)

- Trong internet: Thì nó được hiểu là một robot, là một ứng dụng để tự động hóa các tác vụ lặp đi lặp lại chẳng hạn như cài đặt báo thức, báo cho bạn biết thời tiết hoặc tìm kiếm trực tuyến. 

Bạn có thể làm được những gì với `Bot` ???

- Tích hợp với một dịch vụ bên ngoài. Ví dụ bạn có tích với Gmail để gửi mail thông qua telegram, hoặc với github, youtube...

VD: Thông qua Gmail Bot để gửi mail bằng cách sử dụng command để tương tác:

<img src = "https://github.com/MinhKMA/ghichep-telegram-bot/blob/master/images/bot1.png">

- Lập trình một trò chơi 
- ChatBot để tìm kiếm những người bạn nói chuyện dựa trên cùng sở thích hay cùng khu vục hoặc ngẫu nhiên 
- Thanh toán từ người dùng telegram 
- Tạo ra một chương trình để gửi nhắc nhở, thông báo cho bạn như thời tiết... 

Mình chỉ lấy một số ngữ cảnh sử dụng để mọi người dễ dàng hình dung còn rất nhiều những điều thú vị để khai thác thêm :)

<a name=hoatdong></a>
### 2. Bot hoạt động như thế nào?

Đối với Telegram, Bot là những tài khoản đặc biệt không yêu cầu sử dụng số điện thoại để thiết lập và được sinh ra từ BotFarther. Có hai cách để tương tác với Bot:

- Gửi một tin nhắn hoặc command giống như bạn thực hiện chat với một người bạn của mình. 

- Gửi một request trực tiếp.

Tin nhắn, command hoặc request do người dùng gửi đến được truyền cho phần mềm chạy trên máy chủ của bạn. Máy chủ trung gian xử lý mã hóa và giao tiếp với telegram API cho bạn. Bạn cũng có thể giao tiếp với nó thông qua  HTTPS-interface 

<a name=creatbot></a>
### 3. Các bước tạo ra một con Bot

#### Bước 1: Bạn phải có một tài khoản đăng nhập telegram 

- Tải app telegram về điện thoại của mình
- Dùng số điện thoại để đăng kí tài khoản 
- Sau khi có thông tin đăng nhập thì sử dụng telegram desktop hoặc telegram web để sử dụng cho thuận tiện.

#### Bước 2: Tìm `BotFather`

- Sau khi tìm thấy BotFather trong ô search  thì click vào nó và `start` để bắt đầu giao tiếp với nó

- Bot sẽ trả về cho mình danh sách các commands để bạn control 

- Tiếp tục sử dụng command `/newbot` để tạo ra một con Bot cho dành riêng cho mình 

- Sau đó bạn nhập tên cho Bot 

- Nhập user name cho Bot. Lưu ý đọc kỹ hướng dẫn để tạo ra một username hợp lệ

<img src ="https://github.com/MinhKMA/ghichep-telegram-bot/blob/master/images/bot2.png">

- Sau khi tạo xong bạn sẽ nhận được token để xác thực với con Bot của bạn.

***Lưu ý: chuỗi token bạn phải tuyệt đối bảo mật. Nó như là chìa khóa để vào nhà bạn*** :)

#### Bước 3: Thực hiện một số HTTP API tương tác với Bot

##### GetMe

Đây chính là method để bạn có list ra được thông tin Bot của bạn 

Bạn mở trình duyệt web lên và dán đường link ở dưới vào cùng với `string_token` vừa nhận từ Botfather.

``https://api.telegram.org/bot<string_token>/getMe``

Kết quả trả về tùy thuột vào add-on trình duyệt  :

<img src="https://github.com/MinhKMA/ghichep-telegram-bot/blob/master/images/bot3.png">

Ta sẽ thấy có:

- ID Bot
- Tên Bot
- Username Bot

##### getUpdates 

Đây là method để bạn list ra được thông tin về tin nhắn người dùng tương tác(gửi) cho con Bot đó 

Sau khi bạn đã nhắn tin cho bot của bạn, đây là phương thức để list ra các thông tin tin nhắn người dùng tương tác với con bot đó.

<img src="https://github.com/MinhKMA/ghichep-telegram-bot/blob/master/images/bot4.png">

Trong đó: 

- update_id : tham số này sẽ tăng lên khi có một tin nhắn mới 
- mesage_id : tham số cho một mesage
- id : Đây chính là id của bạn. ID này là duy nhất
- Các thông tin còn lại là thông tin về tài khoản của bạn khai báo khi đăng kí.  

###### sendMessage 

Method sendMessage để ra lệnh cho Bot gửi một tin nhắn cho người dùng telegram 

VD: gửi một tin nhắn cho người dùng với nội dung là    `anhdeptraiquatroi`

``https://api.telegram.org/bot<string_token>/sendMessage?chat_id=<id_user>&text=anhdeptraiquatroi``

Đó là những gì cơ bản nhất khi bạn muốn bắt đầu với Bot trong telegram. Còn rất nhiều method hơn tham khảo tại <a href="https://core.telegram.org/bots/api">Bot API</a>

#### Bước 4: Viết tính năng cho Bot

Lúc này bạn đã có một Bot với token. Nhiệm vụ của các bạn lúc này là dùng một ngôn ngữ lập trình mà Telegram hỗ trợ như Python, Java để viết tính năng cho Bot. Bot có khả năng đến đâu chính là phụ thuộc và code có thể làm được những gì :P.

Và tôi sẽ update những ví dụ cụ thể việc tạo một con Bot và code những tính năng cho con Bot đó trong thời gian sớm nhất.

<a name=tailieu></a>
### 4. Tài liệu tham khảo

- https://core.telegram.org/bots
- https://core.telegram.org/bots/api
