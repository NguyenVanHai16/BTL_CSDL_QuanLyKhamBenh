# Thông tin cá nhân
   - Họ và Tên: Nguyễn Văn Hải
   - MSSV: K215480106073
   - Lớp: K57KMT
   - Môn học: Hệ quản trị cơ sở dữ liệu

## ĐỀ TÀI: Quản lý khám bệnh tại bệnh viện
- Mô tả bài toán quản lý: Quản lý thông tin bệnh nhân, hồ sơ bệnh án, và thông tin bác sĩ tại bệnh viện, hỗ trợ việc tra cứu và báo cáo thông tin, giúp cải thiện công tác khám chữa bệnh và theo dõi tình trạng sức khỏe của bệnh nhân.

### Những chức năng xây dựng quản lý khám bệnh
1. Quản lý

1.1. Quản Lý Bệnh nhân

   - Thêm danh sách bệnh nhân: Cho phép thêm mới một bệnh nhân mới vào cơ sở dữ liệu
   - Chỉnh sửa thông tin bệnh nhân: Cho phép chỉnh sửa thông tin của một bệnh nhân đã tồn tại
   - Xóa bệnh nhân: Cho phép xóa một bệnh nhân cũ khỏi cơ sở dữ liệu
   - Tìm kiếm bệnh nhân: Cho phép tìm kiếm bệnh nhân theo tên, ID, ...
   - Xem danh sách bệnh nhân: Hiển thị danh sách tất cả các bệnh nhân trong bệnh viện

1.2. Quản lý bác sĩ
   - Thêm danh sách bác sĩ: Cho phép thêm mới một bác sĩ mới vào cơ sở dữ liệu
   - Chỉnh sửa thông tin bác sĩ: Cho phép chỉnh sửa thông tin của một bác sĩ đã tồn tại
   - Xóa bác sĩ: Cho phép xóa một bác sĩ cũ khỏi cơ sở dữ liệu
   - Tìm kiếm bác sĩ: Cho phép tìm kiếm bác sĩ theo tên, ID, ...
   - Xem danh sách bác sĩ: Hiển thị danh sách tất cả các bác sĩ trong bệnh viện
     
2. Chức năng truy vấn
   - Tìm kiếm bệnh nhân theo tên
   - Tìm kiếm bác sĩ theo chuyên khoa
   - Hiển thị thông tin bệnh nhân
   - Hiển thị thông tin bác sĩ
   - Hiển thị thông tin phòng khám
   - Hiển thị thông tin lịch sử khám
   - Hiển thị thông tin lịch hẹn
     
### Các thông tin liên quan đến bệnh nhân
1. Thông tin cá nhân
   - Mã bệnh nhân: mã định danh duy nhất của mỗi bệnh nhân
   -  Họ và tên: họ và tên đầy đủ của bệnh nhân
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

## Xây dựng chương trình quản lý khám bệnh tại bệnh viện trong SQL:

1. Bảng bệnh nhân
   - Tạo bảng BenhNhan
   - MaBenhNhan🔑: khóa chính được sử dụng để xác định từng bệnh nhân một cách duy nhất, tự động tăng lên.
   - HoTen: họ vã tên của bệnh nhân
   - NgaySinh: ngày, tháng, năm sinh của bệnh nhân
   - GioiTinh: giới tính của bệnh nhân
   - DiaChi: địa chỉ của bệnh nhân
   - SoDienThoai: thông tin liên lạc của bệnh nhân

```
   CREATE TABLE BenhNhan (
       MaBenhNhan INT PRIMARY KEY IDENTITY(1,1),
       HoTen NVARCHAR(100),
       NgaySinh DATE,
       GioiTinh NVARCHAR(10),
       DiaChi NVARCHAR(200),
       SoDienThoai NVARCHAR(15)
   );
```
   - ![image](https://github.com/NguyenVanHai16/BTL_CSDL_QuanLyKhamBenh/assets/168853303/9dd63f49-a8bf-4c42-8bf1-10db5cbab248)

1. Bảng Bác sĩ
   - Tạo bảng BacSi
   - MaBacSi🔑: khóa chính được sử dụng để xác định từng bác sĩ một cách duy nhất, tự động tăng lên.
   - HoTen: họ và tên của bác sĩ
   - ChuyenKhoa: bác sĩ chuyên về khoa...
   - SoDienThoai: thông tin liên lạc của bác sĩ
  
```
   CREATE TABLE BacSi (
       MaBacSi INT PRIMARY KEY IDENTITY(1,1),
       HoTen NVARCHAR(100),
       ChuyenKhoa NVARCHAR(100),
       SoDienThoai NVARCHAR(15)
   );
```

   - ![image](https://github.com/hoadain/demo-git/assets/168853303/cdfddc6d-4988-4f2f-8233-3066555c4f58)

2. Bảng phòng khám
   - Tạo bảng PhongKham
   - MaPhong🔑: khóa chính
   - TenPhong: tên của phòng khám
   - SoLuongBenhNhan: số lượng bệnh nhân trong phòng khám

```
   CREATE TABLE PhongKham (
       MaPhong INT PRIMARY KEY IDENTITY(1,1),
       TenPhong NVARCHAR(100),
       SoLuongBenhNhan INT
   );
```

   - ![image](https://github.com/hoadain/demo-git/assets/168853303/4438bcd0-cf9d-455c-9a92-fabace60c956)

2. Bảng lịch sử khám
   - Tạo bảng LichSuKham
   - MaLichSu🔑: khóa chính
   - MaBenhNhan: mã của bệnh nhân
   - NgayKham: ngày bệnh nhân đi khám
   - TrieuChung: triệu chứng của bệnh nhân
   - ChanDoan: chuẩn đoán bệnh nhân mắc bệnh gì
   - MaBenhNhan🔑: khóa ngoại (FOREIGN KEY) tham chiếu MaBenhNhan của bảng BenhNhan. Điều này thiết lập mối liên hệ giữa các bảng và cho phép truy cập thông tin.

```
   CREATE TABLE LichSuKham (
       MaLichSu INT PRIMARY KEY IDENTITY(1,1),
       MaBenhNhan INT,
       NgayKham DATE,
       TrieuChung NVARCHAR(MAX),
       ChanDoan NVARCHAR(MAX),
       FOREIGN KEY (MaBenhNhan) REFERENCES BenhNhan(MaBenhNhan)
   );
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/b99b818e-91b5-4851-9361-dcd6a0ea612b)

2. Bảng lịch hẹn
   - Tạo bảng LichHen
   - MaLichHen🔑: khóa chính
   - MaBenhNhan: mã của bệnh nhân
   - MaBacSi: mã của bác sĩ
   - MaPhong: mã phòng
   - NgayHen: ngày hẹn khám
   - GioHen: giờ hẹn khám
   - TrangThai: trạng thái hẹn
   - MaBenhNhan🔑: khóa ngoại (FOREIGN KEY) tham chiếu MaBenhNhan của bảng BenhNhan. Điều này thiết lập mối liên hệ giữa các bảng và cho phép truy cập thông tin.
   - MaBacSi🔑: khóa ngoại (FOREIGN KEY) tham chiếu MaBacSi của bảng BacSi. Điều này thiết lập mối liên hệ giữa các bảng và cho phép truy cập thông tin.
   - MaPhong🔑: khóa ngoại (FOREIGN KEY) tham chiếu MaPhong của bảng PhongKham. Điều này thiết lập mối liên hệ giữa các bảng và cho phép truy cập thông tin.
```
   CREATE TABLE LichHen (
       MaLichHen INT PRIMARY KEY IDENTITY(1,1),
       MaBenhNhan INT,
       MaBacSi INT,
       MaPhong INT,
       NgayHen DATE,
       GioHen TIME,
       TrangThai NVARCHAR(20),
       FOREIGN KEY (MaBenhNhan) REFERENCES BenhNhan(MaBenhNhan),
       FOREIGN KEY (MaBacSi) REFERENCES BacSi(MaBacSi),
       FOREIGN KEY (MaPhong) REFERENCES PhongKham(MaPhong)
   );
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/db855978-32cb-40fa-abcf-25ec612dac86)
     
3. Sơ đồ liên kết
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/144a9a00-808c-46e7-85ae-95f98a00aa4b)
     
## Thêm dữ liệu vào bảng

- Add data vào bảng BenhNhan
```
  (N'Tran Thi A', '1982-03-03', N'Nu', N'486 Le Thanh Ton, Quan 3, TP HN','0911225436')
  (N'Nguyen Van B', '1982-07-04', N'Nam', N'653 Le Thanh , Quan 7, TP HN', '0911225763')
  (N'Nguyen van C', '1982-03-09', N'Nam', N'454 Thanh Ton, Quan 5, TP HN', '0911225123')
```
- Add data vào bảng BacSi
```
  (N'MR. Pham Hoa', zN'Tai mui hong', '0999888777')
  (N'Dr. Nguyen Van C', N'Răng hàm mặt', '0888777666')
```
- Add data vào bảng PhongKham
```
  (N'Phong kham 101')
  (N'Phòng khám 102')
  (N'Phòng khám 103')
```
- Add data vào bảng LichSuKham
```
   - (@MaBenhNhan'2024-06-19', N'Đau đầu, sốt cao', N'Cảm cúm')
   - (@MaBenhNhan = 2, '2024-06-20', N'Đau bụng và buồn nôn', N'Viêm dạ dày')
```
- Add data vào bảng LichHen
```
   - (@MaBenhNhan, @MaBacSi, @MaPhong, 2024-06-21', '12:00:00')
   - (@MaBenhNhan , @MaBacSi, @MaPhong, '2024-06-22', '14:30:00')
```

## Các chức năng 

- Quản Lý bệnh nhân
```
-- Thêm bệnh nhân (ThemBenhNhan)
CREATE PROCEDURE ThemBenhNhan (
    @HoTen NVARCHAR(100),
    @NgaySinh DATE,
    @GioiTinh NVARCHAR(10),
    @DiaChi NVARCHAR(200),
    @SoDienThoai NVARCHAR(15)
)
AS
BEGIN
    INSERT INTO BenhNhan (HoTen, NgaySinh, GioiTinh, DiaChi, SoDienThoai)
    VALUES (@HoTen, @NgaySinh, @GioiTinh, @DiaChi, @SoDienThoai);
END

--Sửa đổi thông tin bệnh nhân (SuaThongTinBenhNhan)
CREATE PROCEDURE SuaThongTinBenhNhan (
    @MaBenhNhan INT,
    @HoTen NVARCHAR(100),
    @NgaySinh DATE,
    @GioiTinh NVARCHAR(10),
    @DiaChi NVARCHAR(200),
    @SoDienThoai NVARCHAR(15)
)
AS
BEGIN
    UPDATE BenhNhan
    SET HoTen = @HoTen,
        NgaySinh = @NgaySinh,
        GioiTinh = @GioiTinh,
        DiaChi = @DiaChi,
        SoDienThoai = @SoDienThoai
    WHERE MaBenhNhan = @MaBenhNhan;
END

--Xóa bệnh nhân (XoaBenhNhan)
CREATE PROCEDURE XoaBenhNhan (
    @MaBenhNhan INT
)
AS
BEGIN
    DELETE FROM BenhNhan
    WHERE MaBenhNhan = @MaBenhNhan;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/5536873d-230a-413a-b70b-3173a414c74e)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/2ae7a1c2-22ba-4012-a752-41e205ed796c)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/09843e0a-0e9e-4c6e-acc9-dac48b316497)

- Quản lý bác sĩ
```
--Thêm bác sĩ (ThemBacSi)
CREATE PROCEDURE ThemBacSi (
    @HoTen NVARCHAR(100),
    @ChuyenKhoa NVARCHAR(100),
    @SoDienThoai NVARCHAR(15)
)
AS
BEGIN
    INSERT INTO BacSi (HoTen, ChuyenKhoa, SoDienThoai)
    VALUES (@HoTen, @ChuyenKhoa, @SoDienThoai);
END

--Sửa đổi thông tin bác sĩ (SuaThongTinBacSi)
CREATE PROCEDURE SuaThongTinBacSi (
    @MaBacSi INT,
    @HoTen NVARCHAR(100),
    @ChuyenKhoa NVARCHAR(100),
    @SoDienThoai NVARCHAR(15)
)
AS
BEGIN
    UPDATE BacSi
    SET HoTen = @HoTen,
        ChuyenKhoa = @ChuyenKhoa,
        SoDienThoai = @SoDienThoai
    WHERE MaBacSi = @MaBacSi;
END

--Xóa bác sĩ (XoaBacSi)
CREATE PROCEDURE XoaBacSi (
    @MaBacSi INT
)
AS
BEGIN
    DELETE FROM BacSi
    WHERE MaBacSi = @MaBacSi;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/401dbaf0-40ca-4dac-85a3-744634201a9e)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/7b2b56ff-1ad8-4422-8d5e-e2d9d7628332)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/272c036e-6fc0-445b-92d2-bb2609e85d96)

- Quản lý phòng khám
```
--Thêm phòng khám (ThemPhongKham)
CREATE PROCEDURE ThemPhongKham (
    @TenPhong NVARCHAR(100)
)
AS
BEGIN
    INSERT INTO PhongKham (TenPhong, SoLuongBenhNhan)
    VALUES (@TenPhong, 0); -- Mặc định số lượng bệnh nhân ban đầu là 0
END

--Sửa đổi thông tin phòng khám (SuaThongTinPhongKham)
CREATE PROCEDURE SuaThongTinPhongKham (
    @MaPhong INT,
    @TenPhong NVARCHAR(100)
)
AS
BEGIN
    UPDATE PhongKham
    SET TenPhong = @TenPhong
    WHERE MaPhong = @MaPhong;
END

--Xóa phòng khám (XoaPhongKham)
CREATE PROCEDURE XoaPhongKham (
    @MaPhong INT
)
AS
BEGIN
    DELETE FROM PhongKham
    WHERE MaPhong = @MaPhong;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/6f978bf0-1762-40b8-9355-783570dd61e6)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/96bb89c1-0ebb-4354-9c12-049c0527956e)
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/78db82e5-0377-4864-a7cc-51e3a339af0d)

- Quản lý lịch sử khám bệnh
```
--Thêm lịch sử khám (ThemLichSuKham)
CREATE PROCEDURE ThemLichSuKham (
    @MaBenhNhan INT,
    @NgayKham DATE,
    @TrieuChung NVARCHAR(MAX),
    @ChanDoan NVARCHAR(MAX)
)
AS
BEGIN
    INSERT INTO LichSuKham (MaBenhNhan, NgayKham, TrieuChung, ChanDoan)
    VALUES (@MaBenhNhan, @NgayKham, @TrieuChung, @ChanDoan);
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/1c49de35-b5b6-4f75-a1c2-84d84a1ad716)

- Quản lý lịch hẹn khám bệnh
```
--Thêm lịch hẹn (ThemLichHen)
CREATE PROCEDURE ThemLichHen (
    @MaBenhNhan INT,
    @MaBacSi INT,
    @MaPhong INT,
    @NgayHen DATE,
    @GioHen TIME
)
AS
BEGIN
    INSERT INTO LichHen (MaBenhNhan, MaBacSi, MaPhong, NgayHen, GioHen, TrangThai)
    VALUES (@MaBenhNhan, @MaBacSi, @MaPhong, @NgayHen, @GioHen, 'Chua kham');
    
    UPDATE PhongKham
    SET SoLuongBenhNhan = SoLuongBenhNhan + 1
    WHERE MaPhong = @MaPhong;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/3287457a-8b50-4798-b57b-33df711210de)

## Chức năng nâng cao

1. Sử dụng Trigger
   - Tự động cập nhật lại số lượng bệnh nhân trong phòng khám khi xóa lịch hẹn
```
-- Xóa trigger cũ nếu tồn tại
IF OBJECT_ID('XoaLichHen', 'TR') IS NOT NULL
    DROP TRIGGER XoaLichHen;
GO

--trigger XoaLichHen
CREATE TRIGGER XoaLichHen
ON LichHen
AFTER DELETE
AS
BEGIN
    DECLARE @MaPhong INT;
    
    SELECT @MaPhong = MaPhong FROM DELETED;
    
    UPDATE PhongKham
    SET SoLuongBenhNhan = SoLuongBenhNhan - 1
    WHERE MaPhong = @MaPhong;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/db956013-dfc8-4557-942d-2f2529c790a3)

2. Sử dụng cursor
   - gửi thông báo nhắc nhở bệnh nhân khi tới ngày hẹn khám bệnh
```
--Cursor gửi thông báo nhắc nhở (GuiThongBaoNhacNho)
CREATE PROCEDURE GuiThongBaoNhacNho
AS
BEGIN
    DECLARE @benhnhan NVARCHAR(100);
    DECLARE @ngayhen DATE;

    DECLARE cur CURSOR FOR 
        SELECT b.HoTen, l.NgayHen
        FROM BenhNhan b
        JOIN LichHen l ON b.MaBenhNhan = l.MaBenhNhan
        WHERE l.TrangThai = 'Chua kham' AND l.NgayHen = CAST(GETDATE() AS DATE);

    OPEN cur;
    FETCH NEXT FROM cur INTO @benhnhan, @ngayhen;

    WHILE @@FETCH_STATUS = 0
    BEGIN
        -- Gửi thông báo nhắc nhở (ở đây chỉ là ví dụ, cần tích hợp hệ thống gửi tin nhắn thực tế)
        PRINT CONCAT('Nhắc nhở: Bệnh nhân ', @benhnhan, ' có lịch hẹn vào ngày ', @ngayhen);
        
        FETCH NEXT FROM cur INTO @benhnhan, @ngayhen;
    END;

    CLOSE cur;
    DEALLOCATE cur;
END
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/5886389d-4934-40bc-ba8f-258c479f5cf4)

## Tìm kiếm và hiển thị thông tin

   - Hiển thị view bệnh nhân
```
--View hiển thị thông tin các bệnh nhân (View_BenhNhan)
CREATE VIEW View_BenhNhan AS
SELECT 
    MaBenhNhan,
    HoTen,
    NgaySinh,
    GioiTinh,
    DiaChi,
    SoDienThoai
FROM 
    BenhNhan;
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/9812c452-873a-4ad6-a22b-ff81f7b36ce5)
   - Kết quả
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/d2cac214-5dd5-44b9-81dc-757f1b332619)
     
   - Hiển thị view bác sĩ
```
--View hiển thị thông tin các bác sĩ (View_BacSi)
CREATE VIEW View_BacSi AS
SELECT 
    MaBacSi,
    HoTen,
    ChuyenKhoa,
    SoDienThoai
FROM 
    BacSi;
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/988fdd23-0a7e-42ba-b74c-345063144dcc)
   - Kết quả
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/439b59da-622c-4817-9ae1-ca549a029da6)
     
   - Hiển thị view phòng khám
```
--View hiển thị thông tin các phòng khám (View_PhongKham)
CREATE VIEW View_PhongKham AS
SELECT 
    MaPhong,
    TenPhong,
    SoLuongBenhNhan
FROM 
    PhongKham;
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/584a9fa9-9c0c-406d-b186-0f2bd47d3775)
   - Kết quả
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/e2113389-0de5-482f-a5b9-b7e09926a73a)

   - Hiển thị view lịch sử khám bệnh
```
--Hiển thị thông tin lịch sử khám trong View (View_LichSuKham)
	CREATE VIEW View_LichSuKham AS
SELECT 
    ls.MaLichSu,
    bn.HoTen AS TenBenhNhan,
    ls.NgayKham,
    ls.TrieuChung,
    ls.ChanDoan
FROM 
    LichSuKham ls
JOIN 
    BenhNhan bn ON ls.MaBenhNhan = bn.MaBenhNhan;
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/6fbd414a-384d-493c-b2ab-9e5e5bd5c703)
   - Kết quả
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/d985744c-f811-478d-b102-5df389e9e94d)
     
   - Hiển thị view lịch hẹn
```
--View hiển thị thông tin các lịch hẹn (View_LichHen)
CREATE VIEW View_LichHen AS
SELECT 
    lh.MaLichHen,
    bn.HoTen AS TenBenhNhan,
    bs.HoTen AS TenBacSi,
    pk.TenPhong,
    lh.NgayHen,
    lh.GioHen,
    lh.TrangThai
FROM 
    LichHen lh
JOIN 
    BenhNhan bn ON lh.MaBenhNhan = bn.MaBenhNhan
JOIN 
    BacSi bs ON lh.MaBacSi = bs.MaBacSi
JOIN 
    PhongKham pk ON lh.MaPhong = pk.MaPhong;
```
   - ![image](https://github.com/hoadain/demo-git/assets/168853303/b736ea5c-0fa1-4505-b6c6-1013b25a1ea0)
   - Kết quả
   - ![image](https://github.com/NguyenVanHai16/BTL_CSDL_QuanLyKhamBenh/assets/168853303/b8d0a776-f736-4abe-84a3-abac8855818c)


