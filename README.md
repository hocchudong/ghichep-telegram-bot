# Ghi chép ban đầu về telegram bot

## Link tham khảo chính hãng
https://telegram.org/blog/bot-revolution
https://core.telegram.org/bots

## Cách tạo bots
Chat với ông [BotFather](https://telegram.me/botfather) để đăng ký tạo bot mới. Sẽ có thông báo tường minh trên màn hình những gì cần làm. Sau khi đăng ký xong sẽ có token để truy cập vào API
Link truy cập API có dạng:
https://api.telegram.org/chuỗi token/chức năng
Phần chức năng được đặc tả theo tài liệu https://core.telegram.org/bots/api#making-requests

Đính kèm repo:
Lib gửi message tới chatID bằng python. Với nhu cầu gửi tin nhắn chủ động (notify, alert) chỉ cần post thẳng vào API của telegram là đã có thể gửi được, không cần phải webhook phức tạp như facebook hay skype. Hiện mình đang sử dụng để làm hệ thống alert cho zabbix và PRTG.