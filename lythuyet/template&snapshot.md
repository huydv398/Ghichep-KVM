# Tìm hiểu về Template và snapshot trong KVM
1. [Hướng dẫn tao Template từ VM](#1)
2. [Giới thiệu về Template trong KVM]()
3. [Hướng dẫn tạo và quản lý Template]()
4. [Hướng dẫn tạo snapshot]()
5. [Hướng dẫn tạo và quản lý Internal Snapshot]()
6. [Hướng dẫn tạo và quản lý External Snapshot]()

## Hướng dẫn tao Template từ VM

### 1. Giới thiệu về Template trong KVM
* Template là một dạng file image pre-configured của hệ điều hành dùng để tạo nhanh các máy ảo. Sử dụng Template sẽ tránh những bước cài đặt lặp đi lặp lại và tiết kiệm nhiều thời gian hơn so với từng bước một.
* Việc sử dụng Template, số bước mà người dùng phải thực hiện sẽ được rút ngắn đi rất nhiều, chỉ cần thực hiện 1 lần các bước trùng lặp rồi tạo Template là bạn có thể rút ngắn được thời gian
### 2. Hướng dẫn tạo và quản lý Template
* Hai khái niệm cần phân biệt là `clone` và `Template`.
  * `Clone`: Tạo ra một bản sao của máy ảo
  * `Template`: nó có thể được dùng để tạo ra nhiều clone của máy khác nữa.
* Có hai phương thức để triển khai máy ảo từ Template là Thin và Clone:
  * Thin: Máy ảo được tạo ra theo phương thức này sẽ sử dụng như một base image, lúc này nó sẽ chuyển sang trạng thái read-only. Cùng với đó, sẽ ó một ổ mới hỗ trợ "copy on read" được thêm vào để lưu trữ mới. Phương thức này sẽ tốn phương thức này sẽ tốn ít dung lượng hơn tuy nhiên các VM tạo ra sẽ phụ thuộc vào base image, chúng sẽ không chạy được nếu không có base image.

## Tạo Template
* Template thực chất là máy ảo được chuyển đổi sang. Quá trình này gồm 3 bước:
  * Bước 1: Cài đặt máy ảo với đầy đủ các phần mềm cần thiết để biến nó thành một Template, ví dụ(LAMP, LEMP, WordPress hoặc WordOps)
  * Bước 2: Loại bỏ tất cả các cài đặt cụ thể ví dụ như Password SSH, địa chỉ MAC.. để đảm bảo rằng nó sẽ không được áp dụng giống với nhau tới tất cả các máy ảo đươc tạo ra sau này.
  * Bước 3: Đánh dấu máy ảo là Template bằng việc đổi tên.
