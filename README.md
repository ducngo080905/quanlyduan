3. Phân tích quy trình hiện tại  
3.1. Mô tả quy trình hiện tại

- Quy trình phát triển phần mềm hiện tại của đội CodeStream được thực hiện theo các bước sau:

    1. Lập trình viên (Developer) viết mã nguồn và commit code lên hệ thống quản lý mã nguồn (Git).

    2. Sau khi commit, hệ thống kích hoạt CI Pipeline, bao gồm:

      - Build mã nguồn

      - Chạy Unit Test

      - Chạy Integration Test

    3. Khi CI Pipeline hoàn tất, mã nguồn được chuyển sang CD Pipeline, bao gồm:

      - Thực hiện Code Review

      - Triển khai lên môi trường Staging

      - Triển khai lên Production (thủ công hoặc bán tự động)

--> Quy trình này giúp đảm bảo mã nguồn được kiểm tra trước khi đưa vào môi trường chính thức.
Sơ đồ luồng công việc workflow:  

<img width="914" height="608" alt="image" src="https://github.com/user-attachments/assets/6dc5e25d-b364-427d-bcce-4b0a7fdb57d9" />


3.2. Các điểm nghẽn (Bottlenecks) trong quy trình

  - Mặc dù đã có CI/CD, quy trình hiện tại vẫn tồn tại một số hạn chế:

  - Code Review phụ thuộc nhiều vào con người, gây chậm trễ nếu người duyệt không sẵn sàng.

  - Quy trình triển khai Production chưa tự động hoàn toàn, dễ phát sinh lỗi thao tác.

  - Integration Test chạy sau commit, nhưng chưa kiểm soát tốt chất lượng test case.

  - Khi pipeline gặp lỗi, việc xác định nguyên nhân và khắc phục còn mất thời gian.

3.3. Rủi ro trong quy trình hiện tại

  - Nguy cơ deploy lỗi lên Production nếu kiểm thử chưa đầy đủ.

  - Tốn thời gian triển khai, làm chậm tốc độ ra mắt sản phẩm.

  - Khó mở rộng quy trình khi số lượng lập trình viên tăng.

  - Phụ thuộc vào kinh nghiệm cá nhân thay vì quy trình chuẩn hóa.

3.4. Đánh giá tổng quan

  --> Quy trình hiện tại đã có nền tảng CI/CD nhưng chưa được tối ưu hóa triệt để. Việc cải tiến pipeline theo hướng tự động hóa nhiều hơn, kiểm soát chất lượng tốt hơn và giảm phụ thuộc thủ công là cần thiết để nâng cao hiệu quả phát triển phần mềm.
