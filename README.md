# MomoPayment
Các bạn có thể test thử chức năng thanh toán trực tuyến của MOMO tại đây:

https://test-payment.momo.vn/qr/index.php


MOMO có cung cấp cho chúng ta app và thông tin tài khoản để thực hiện thanh toán trên môi trường test:

Quét mã QR để tải app MOMO Test
<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image1.png">
</p>
<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image2.png">
</p>

- Mật khẩu: 000000
- Mã xác thực (OTP): 000000
- Tham khảo thêm: https://developers.momo.vn/#/docs/aiov2/ 

# Chúng ta bắt tay vào thực hiện thôi nào!
-------------------------
## Bước 1: Đăng ký tài khoản doanh nghiệp

Các bạn truy cập vào https://business.momo.vn/signup và đăng ký một tài khoản.

Sau khi đăng ký thành công, các bạn truy cập vào link https://business.momo.vn/merchant/integrateInfo để lấy PARTNER CODE, ACCESS KEY, SECRET KEY, API ENDPOINT

</p>
<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image3.png">
</p>

## Bước 2: Tích hợp MOMO vào website

- Tạo class MoMoSecurity hỗ trợ việc Hash data

<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image4.png">
</p>

Tham khảo code tại đây: https://github.com/anvndev/Momo-Payment/blob/master/MomoPayment/Others/MoMoSecurity.cs

- Tạo class PaymentRequest để tạo request

<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image5.png">
</p>

Tham khảo code tại đây: https://github.com/dinhtnguyenn/MomoPayment/blob/main/MomoPayment/Others/PaymentRequest.cs

Tạo action Payment để tạo link thanh toán trên hệ thống MOMO
Các data cần gửi lên MoMo để thực hiện thanh toán thông qua cổng thanh toán AIO bao gồm.

<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image6.png">
</p>
<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image7.png">
</p>


Tham khảo code tại: https://github.com/dinhtnguyenn/MomoPayment/blob/main/MomoPayment/Controllers/HomeController.cs 


Sử dụng Ngrok để public localhost

https://dinhnt.com/read/chia-se-local-website-localhost-ra-ben-ngoai-670


Tham khảo thêm tại: https://developers.momo.vn/#/docs/aio/?id=ph%c6%b0%c6%a1ng-th%e1%bb%a9c-thanh-to%c3%a1n 

--------------------

## returnUrl và notifyUrl:
- Là 2 url của Server mà MoMo sẽ gửi HTTP Response chứa kết quả thông tin thanh toán.
- Với returnUrl MoMo sẽ gửi qua method GET, redirect từ MoMo về returnUrl sau khi user thực hiện thanh toán xong.
- Với notifyUrl MoMo sẽ gửi qua method POST, MoMo thực hiện IPN để gửi data về notifyUrl sau khi user thực hiện thanh toán xong.
- Với returnUrl và notifyUrl thực hiện kiểm tra data nhận về từ MoMo có khớp với data gửi lên MoMo hay không.
- Tránh trường hợp user tự gõ url để update order mà không thông qua thanh toán MoMo.
- Ta cần sử dụng cả returnUrl và notifyUrl để tránh trường hợp MoMo không redirect về returnUrl (do timeout, user tắt trình duyệt) thì server vẫn nhận được data thông qua notifyUrl.

---------------------
## Data mà MoMo trả về:
Các data cần gửi lên MoMo để thực hiện thanh toán thông qua cổng thanh toán AIO bao gồm.

<p align="center">
	<img src="https://raw.githubusercontent.com/anvndev/Momo-Payment/master/Images/image8.png">
</p>


```````````````````
Cảm ơn và chúc bạn học tốt!
by Anvndev
