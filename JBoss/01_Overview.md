# Tổng quan về JBoss

- **Red Hat JBoss Enterprise Application Platform 7 (JBoss EAP)** là một nền tảng middleware được build dựa trên các tiêu chuẩn mở và tương thích với phiên bản **Java Enterprise 7**. Nó được tích hợp **WildFly Application Server 10** với các tính năng messaging, high-availability clustering và các công nghệ khác.
- **JBoss EAP** bao gồm một cấu trúc module cho phép chỉ kích hoạt dịch vụ khi được yêu cầu, cải thiện tốc độ khởi động.
- Management console và management CLI làm cho việc chỉnh sửa các file cấu hình XML trở nên không cần thiết và thêm khả năng script để tự động hóa các task.
- **JBoss EAP** cung cấp 2 chế độ hoạt động cho các phiên bản **JBoss** : standalone server hoặc managed domain :
    - ***Standalone server :*** đại diện cho việc chạy **JBoss EAP** dưới dạng một server instance duy nhất.
    - ***Managed domain :*** cho phép quản lý nhiều phiên bản JBoss EAP từ một điểm kiểm soát duy nhất.
- Ngoài ra, **JBoss** cung cấp một hệ thống các API và các development framework để nhanh chóng phát triển các ứng dụng Java EE bảo mật và khả năng mở rộng cao.