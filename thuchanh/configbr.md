# Hướng dẫn configure Network Bridge in Ubuntu

Linux hỗ trợ thực hiện một Network bridge sotfware để tái tạo chức năng của cầu nối mạng, một thiết bị mạng kết nối hai hoặc nhiều mạng truyền thông hoặc phân đoạn mạng cung cấp cách thức để chúng hoạt đọng như một mạng duy nhất. Nó hoạt động gần giống như một switch, nó sử dụng để hỗ trợ cho việc "**Virtual network switch**".


Một trường hợp sử dụng điển hình của bắc cầu mạng phần mềm là trong mỗi trường ảo hóa để kết nối các máy ảo VM trực tiếp với mạng máy chủ lưu trữ và có thể truy cập các dịc vụ như **DHCP** và hơn thế nữa.


Trong bài viết  này,bạn sẽ tìm hiểu các kahcs nhau để thiết lập cầu nối mạng trong Ubuntu và sử dụng nó trong môi trường ảo hóa để tạo mạng ảo ở chế độ bridge network trong Ubuntu và sử dụng nó 