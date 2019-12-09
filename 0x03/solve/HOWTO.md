## [Bài 1](https://ksnctf.sweetduet.info/problem/8)

Dùng wireshark xem file pcap, follow http thì thấy trong header gói tin có trường `Authorization : Basic` trường này chứa user/pass dưới dạng base64 ngăn các nhau bởi `":"`.
 Ta thử decode base64 `cTg6RkxBR181dXg3eksyTktTSDhmU0dB = q8:FLAG_5ux7zK2NKSH8fSGA` trong gói tin cũng cho ta biết thêm thông tin luôn `The flag is q8's password.`-> pass chính là flag của chall này.
