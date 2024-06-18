# Thông tin cá nhân
Họ và Tên: Nguyễn Văn Hải
MSSV: K215480106073
Lớp: K57KMT
Môn học: Hệ quản trị cơ sở dữ liệu

## Quản lý khám bệnh tại bệnh viện
Mô tả bài toán quản lý: Quản lý thông tin bệnh nhân, hồ sơ bệnh án, và thông tin bác sĩ tại bệnh viện, hỗ trợ việc tra cứu và báo cáo thông tin, giúp cải thiện công tác khám chữa bệnh và theo dõi tình trạng sức khỏe của bệnh nhân.

### Những chức năng xây dựng quản lý khám bệnh:
1. Thêm, sửa, xóa bệnh nhân, bác sĩ, phòng khám, lịch hẹn
2. Tìm kiếm, lọc bệnh nhân theo các tiêu chí như tên, ID...
3. Xem số lượng bệnh nhân
4. Quản lý lịch sử khám chữa bệnh
   
#### Các thông tin liên quan đến bệnh nhân
1. Thông tin cá nhân
- Mã bệnh nhân: mã định danh duy nhất của mỗi bệnh nhân
- Họ và tên: họ và tên đầy đủ của bệnh nhân
- Ngày sinh: ngày, tháng, năm sinh của bệnh nhân
- Giới tính: nam hoặc nữ
- Địa chỉ: địa chỉ hiện tại của bệnh nhân
- Số điện thoại: số điện thoại liên hệ của bệnh nhân
  
2. Thông tin y tế
- Mã bệnh
- Tên bệnh
- Mô tả bệnh

3. Lịch sử khám chữa bệnh
- Mã lịch sử
- Tên bệnh nhân
- Ngày khám
- Triệu chứng
- Chuẩn đoán

4. Thông tin bác sĩ
- Mã bác sĩ: mã định danh duy nhất của mỗi bác sĩ
- Họ và tên: họ và tên đầy đủ của bác sĩ
- Khoa: khoa mà bác sĩ làm việc
- Số điện thoại

5. Thông tin phòng khám
- Mã phòng
- Tên phòng
- Số lượng bệnh nhân

6. Bệnh nhân: 🔑Mã bệnh nhân, họ tên, ngày sinh, giới tính, địa chỉ, số điện thoại
7. Bác sĩ: 🔑 Mã bác sĩ, họ tên, chuyên khoa, số diện thoại
8. Phòng khám:🔑 Mã phòng, tên phòng, số lượng bệnh nhân
9. Lịch sử khám: 🔑 Mã lịch sử, mã bệnh nhân, ngày khám, triệu chứng, chuẩn đoán
10. Lịch hẹn: 🔑 Mã lịch hẹn, mã bệnh nhân, mã bác sĩ, mã phòng, ngày hẹn, giờ hẹn

- Như vậy, dựa trên những thông tin mà chúng tôi đã thu thập được chúng tôi sẽ xây dựng các bảng đáp ứng yếu cầu quản lý khám bệnh tại bệnh viện tạo các bảng như mô tả trong máy chủ SQL:


1. Bảng bệnh nhân
- Tạo bảng BenhNhan
- (
    - MaBenhNhan INT PRIMARY KEY IDENTITY(1,1),
    - HoTen NVARCHAR(100),
    - NgaySinh DATE,
    - GioiTinh NVARCHAR(10),
    - DiaChi NVARCHAR(200),
    - SoDienThoai NVARCHAR(15)
- )

