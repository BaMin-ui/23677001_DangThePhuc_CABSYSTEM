# TÀI LIỆU ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS)

## HỆ THỐNG ĐẶT XE TRỰC TUYẾN - CAB SYSTEM



---



## 1. Giới thiệu

### 1.1 Mục đích

Tài liệu này mô tả chi tiết các yêu cầu chức năng và phi chức năng cho nền tảng đặt xe trực tuyến (**CAB System**) của Công ty ABC, phục vụ cho đội ngũ phát triển, kiểm thử và ban quản lý dự án.



### 1.2 Phạm vi hệ thống

Hệ thống cung cấp giải pháp kết nối giữa khách hàng có nhu cầu di chuyển và tài xế, đồng thời cung cấp công cụ quản trị toàn diện cho nhân viên vận hành. Hệ thống hỗ trợ quy trình khép kín từ đặt xe, điều phối tự động, thực hiện chuyến đi, thanh toán, đến đánh giá và báo cáo.



---



## 2. Mô tả tổng quan

### 2.1 Các tác nhân (Actors)



* **Khách hàng (Customer / Passenger):** Người dùng cuối trực tiếp sử dụng nền tảng để thiết lập yêu cầu đặt xe, lựa chọn loại dịch vụ, theo dõi hành trình và vị trí tài xế theo thời gian thực, thực hiện thanh toán cước phí an toàn, cũng như đánh giá chất lượng dịch vụ sau mỗi chuyến đi.

* **Tài xế (Driver):** Đối tác cung cấp dịch vụ vận chuyển trực tiếp, quản lý hồ sơ phương tiện và trạng thái sẵn sàng, nhận hoặc từ chối các điều phối chuyến đi, liên tục cập nhật các mốc trạng thái hành trình và truyền dữ liệu định vị GPS về hệ thống.

* **Nhân viên vận hành (Operations Staff):** Bộ phận quản trị hệ thống chịu trách nhiệm thực thi các tác vụ vận hành hàng ngày, giám sát các chuyến đi đang diễn ra, hỗ trợ xử lý sự cố, quản lý tài khoản người dùng và kiểm soát phân quyền đối với các thao tác nhạy cảm.

* **Ban lãnh đạo / Ban giám đốc (Management):** Nhóm người ra quyết định chiến lược và phê duyệt dự án, quan tâm đến khả năng mở rộng kiến trúc, tối ưu hóa doanh thu và theo dõi hệ thống báo cáo vận hành tổng quan (số lượng chuyến, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế). *(Đóng vai trò tác nhân định hướng và giám sát cao nhất trên hệ thống)*.

* **Nhà cung cấp thanh toán bên ngoài (Payment Gateway Provider):** Hệ thống/đối tác tích hợp bên thứ ba chịu trách nhiệm xử lý các giao dịch thanh toán điện tử an toàn, đảm bảo nguyên tắc không lưu trữ thông tin nhạy cảm của thẻ trực tiếp trong hệ thống CAB.

### 2.2 stakeholder matrix

quadrantChart



    title Biểu đồ Phân tích Stakeholder (Power/Interest Grid)

    x-axis "Mức độ quan tâm (Interest): Thấp" --> "Cao"

    y-axis "Mức độ ảnh hưởng (Power): Thấp" --> "Cao"

    quadrant-1 "Quản lý chặt chẽ (Manage Closely)"

    quadrant-2 "Giữ sự hài lòng (Keep Satisfied)"

    quadrant-3 "Giám sát (Monitor)"

    quadrant-4 "Giữ thông tin (Keep Informed)"

    

    "Ban lãnh đạo / Ban giám đốc": [0.8, 0.85]

    "Nhân viên vận hành": [0.8, 0.55]

    "Khách hàng (Customer / Passenger)": [0.85, 0.25]

    "Tài xế (Driver)": [0.85, 0.20]

    "Nhà cung cấp thanh toán": [0.2, 0.15]

### 2.3 Sơ đồ tổng quan hệ thống (Use Case / Context Diagram)

Dưới đây là sơ đồ Mermaid thể hiện tương tác giữa các tác nhân và hệ thống CAB:



```mermaid

mindmap

  root((Stakeholders<br/>CAB System))

  

    Ban lãnh đạo / Ban giám đốc

      Người ra quyết định, phê duyệt dự án

      Quan tâm khả năng mở rộng hệ thống

      Theo dõi doanh thu & báo cáo vận hành

      Đánh giá tỷ lệ chuyến hoàn thành/hủy & hiệu quả tài xế



    Nhân viên vận hành

      Thực thi các thao tác quản trị hàng ngày

      Theo dõi chuyến đi & xử lý sự cố

      Phân quyền truy cập (giới hạn thao tác nhạy cảm)



    Khách hàng (Customer/Passenger)

      Người dùng cuối đặt xe trực tuyến

      Trải nghiệm đặt xe (chọn điểm đi/đến, loại xe)

      Theo dõi thời gian thực & vị trí tài xế

      Thanh toán cước phí & đánh giá tài xế



    Tài xế (Driver)

      Người dùng cuối cung cấp dịch vụ vận chuyển

      Quản lý hồ sơ, phương tiện & trạng thái sẵn sàng

      Nhận/từ chối chuyến & cập nhật trạng thái chuyến đi

      Truyền dữ liệu định vị GPS thời gian thực



    Nhà cung cấp thanh toán bên ngoài

      Đối tác tích hợp bên thứ ba

      Xử lý giao dịch thanh toán điện tử an toàn

      Bảo mật (không lưu thông tin nhạy cảm thẻ trong hệ thống CAB)
