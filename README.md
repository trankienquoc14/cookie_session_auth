# Cookie Session Auth

## 1. Cài đặt và chạy server
- Mở cmd, chuyển đến thư mục `cookie_session_auth`.
- Cài đặt package:
	```bash
	npm install
	```
![alt text](public/image/image1.png)
- Khởi động server:
	```bash
	node app.js
	```
	Server running on `http://localhost:3000`
![alt text](public/image/image2.png)
## 2. Test API với POSTMAN

### b. Register
- **Method:** POST
- **URL:** `http://localhost:3000/auth/register`
- **Body (JSON):**
	```json
	{
		"username": "admin",
		"password": "12345"
	}
	```
- **Kết quả thành công:**
	```json
	{ "message": "User registered successfully!" }
	```
![alt text](public/image/image3.png)
- **Kiểm tra trong MongoDB:**
	- Mở MongoDB Compass :
	- Truy cập database `SessionAuth`, collection `users`.
	- Xác nhận user mới đã được tạo.
![alt text](public/image/image4.png)   
- **Trường hợp lỗi:**
	- Trùng username: `{ "error": "User registration failed", ... }`
![alt text](public/image/image5.png)  
### c. Login
- **Method:** POST
- **URL:** `http://localhost:3000/auth/login`
- **Body (JSON):**
	```json
	{
		"username": "admin",
		"password": "12345"
	}
	```
- **Kết quả thành công:**
	```json
	{ "message": "Login successful!" }
	```
![alt text](public/image/image6.png)  
- **Kiểm tra trong MongoDB:**
	- Collection `sessions` sẽ có session mới.
![alt text](public/image/image7.png)  
- **Trường hợp lỗi:**
	- Sai username/password: `{ "error": "Invalid username or password" }`
![alt text](public/image/image8.png)  
### d. Xem thông tin cá nhân (profile)
- **Method:** GET
- **URL:** `http://localhost:3000/auth/profile`
- **Kết quả thành công:**
![alt text](public/image/image9.png)  
- **Trường hợp lỗi:**
	- Chưa đăng nhập: `{ "error": "Unauthorized" }`
![alt text](public/image/image10.png)  
### e. Logout
- **Method:** GET
- **URL:** `http://localhost:3000/auth/logout`
- **Kết quả thành công:**
	```json
	{ "message": "Logout successful!" }
	```
![alt text](public/image/image11.png)  
- **Kiểm tra trong MongoDB:**
	- Collection `sessions` sẽ bị xóa session tương ứng.
![alt text](public/image/image12.png)  
