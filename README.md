3. Mô tả quy trình phát triển và triển khai phần mềm hiện tại
  Quy trình phát triển và triển khai phần mềm của nhóm hiện nay được thực hiện qua 05 bước chính, diễn ra theo thứ tự như sau:

    Bước 1: Developer
      Lập trình viên viết code trên máy cá nhân dựa theo yêu cầu đã được phân công.

    Bước 2: Commit / Push Code
      Sau khi hoàn thành phần việc của mình, lập trình viên lưu lại mã nguồn (commit) và đẩy code lên kho mã nguồn chung (Git).

   Bước 3: Build thủ công
      Mã nguồn được build thủ công để tạo ra sản phẩm chạy được. Bước này do lập trình viên hoặc người phụ trách thực hiện trực tiếp.

   Bước 4: Test thủ công
      Sau khi build xong, phần mềm được kiểm tra thủ công để phát hiện lỗi và đảm bảo các chức năng hoạt động đúng.

   Bước 5: Deploy thủ công
      Cuối cùng, phần mềm được triển khai thủ công lên môi trường chạy thử hoặc môi trường chính thức để đưa vào sử dụng.

Sơ đồ workflow:
<img width="1035" height="739" alt="image" src="https://github.com/user-attachments/assets/f0273a71-f65a-4b89-9860-98d8170f17d6" />


3.1  Xác định điểm nghẽn, các bước tốn thời gian và rủi ro cao

Dựa trên quy trình phát triển và triển khai phần mềm hiện tại, nhóm xác định các điểm nghẽn và rủi ro chính như sau:

1. Bước Build thủ công

Tốn thời gian: Mỗi lần build phải thực hiện bằng tay, đặc biệt mất nhiều thời gian khi dự án lớn hoặc nhiều module.

Dễ xảy ra lỗi: Có thể sai phiên bản thư viện, sai cấu hình môi trường hoặc quên bước build.

--> Đây là một trong những điểm nghẽn lớn nhất của quy trình.

2. Bước Test thủ công

Tốn nhiều công sức: Việc kiểm thử phụ thuộc vào con người, phải test lại nhiều lần khi có thay đổi code.

Rủi ro bỏ sót lỗi: Không thể kiểm tra hết mọi trường hợp, đặc biệt là lỗi tiềm ẩn.

--> Chất lượng phần mềm không ổn định, dễ phát sinh lỗi sau khi triển khai.

3. Bước Deploy thủ công

Rủi ro cao nhất: Chỉ cần thao tác sai (sai lệnh, sai môi trường) là có thể gây lỗi hệ thống.

Khó rollback: Khi xảy ra lỗi, việc quay lại phiên bản cũ mất thời gian và phức tạp.

--> Đây là bước có rủi ro gây lỗi cao nhất.

4. Bước Commit / Push Code

Thiếu kiểm soát: Không có kiểm tra tự động trước khi merge code.

Dễ đưa lỗi vào hệ thống nếu lập trình viên chưa test kỹ trên máy cá nhân.

Giải thích lý do các điểm nghẽn chính
1. Build thủ công là điểm nghẽn lớn của quy trình

Lý do:

Quá trình build phải được thực hiện bằng tay, mỗi lần có thay đổi code đều cần build lại từ đầu.

Việc build phụ thuộc vào máy và môi trường của từng người, dễ xảy ra tình trạng “chạy được trên máy này nhưng lỗi trên máy khác”.

Nếu dự án có nhiều thư viện hoặc cấu hình phức tạp, chỉ cần thiếu hoặc sai một bước là build thất bại.

Khi có nhiều lập trình viên cùng làm việc, việc build thủ công không theo một chuẩn chung, gây mất thời gian kiểm tra và sửa lỗi.

--> Kết quả: Build thủ công làm chậm tiến độ, dễ phát sinh lỗi và trở thành điểm nghẽn trong toàn bộ quy trình.

3. Deploy thủ công là bước có rủi ro gây lỗi cao nhất

Lý do:

Quá trình deploy yêu cầu thực hiện nhiều thao tác như copy file, chạy lệnh, cấu hình môi trường…, tất cả đều do con người thực hiện.

Chỉ cần thao tác sai (chạy nhầm lệnh, deploy nhầm môi trường, thiếu file) có thể khiến hệ thống không hoạt động.

Không có cơ chế kiểm tra tự động trước khi deploy nên lỗi từ các bước trước vẫn có thể lọt vào môi trường chạy thật.

Khi deploy xảy ra sự cố, việc quay lại phiên bản cũ (rollback) thường làm thủ công, mất thời gian và tiềm ẩn rủi ro thêm.

--> Kết quả: Deploy thủ công có khả năng gây lỗi nghiêm trọng, ảnh hưởng trực tiếp đến hệ thống và người dùng.
