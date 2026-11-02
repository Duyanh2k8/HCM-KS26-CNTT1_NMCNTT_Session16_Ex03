# Bài 3 : Xử lý Sự cố Giao diện Website Doanh nghiệp
## Phần 1: Báo cáo phân tích (I/O)
### 1.	Xác định vấn đề
-	Input: Giao diện PTIT-LMS có hai khung "Nội dung bài học" và "Danh sách video" bị chồng lấn lên nhau.
-	Process: Sử dụng Inspect Element (F12), chọn từng phần tử và mở tab Computed để kiểm tra bốn thành phần của CSS Box Model.
-	Output: Xác định nguyên nhân gây chồng lấn và đề xuất thông số CSS phù hợp để khắc phục.
### 2.	Phân tích 4 lớp Box Model
**CSS Box Model gồm 4 thành phần:**
|Thành phần |	Ý nghĩa |	Vai trò trong giao diện|
|---|---|---|
|Content |	Nội dung bên trong |	Chứa văn bản, video hoặc dữ liệu|
|Padding |	Khoảng cách từ nội dung đến viền |	Tạo khoảng trống bên trong khung|
|Border	| Đường viền phần tử	| Xác định ranh giới khung|
|Margin	| Khoảng cách bên ngoài viền | Tạo khoảng cách giữa hai khung|
### 3.	Phân tích hai phần tử bị chồng lấn
***Phần tử 1: Khung "Nội dung bài học"***
-	Content: Chứa nội dung văn bản bài học.
-	Padding: Tạo khoảng trống giữa văn bản và đường viền.
-	Border: Đường viền bao quanh khung nội dung.
-	Margin: Khoảng cách giữa khung nội dung và các phần tử xung quanh.

***Phần tử 2: Khung "Danh sách video"***
-	Content: Chứa danh sách các video bài học.
-	Padding: Tạo khoảng trống giữa danh sách video và đường viền.
-	Border: Đường viền bao quanh danh sách video.
-	Margin: Khoảng cách bên ngoài khung video.
## Phần 2: Thiết kế giải pháp
### 1.	Đề xuất thông số CSS
**Có thể thử các thông số sau để tạo khoảng cách hợp lý giữa hai khung:**
|Thuộc tính |	Khung nội dung |	Khung video|
|---|---|---|
|Padding |	16px	| 16px|
|Border|	1px solid #ddd|	1px solid #ddd|
|Margin-bottom|	20px	|20px|
|Position	|static	static|
|Box-sizing|	border-box	|border-box|

Đây là thông số đề xuất ban đầu, không phải kết quả đo thực tế từ trang PTIT-LMS.
### 2.	Mã CSS đề xuất
```CSS
/* Thiết lập kích thước phần tử */
* {
    box-sizing: border-box;
}

/* Khung Nội dung bài học */
.lesson-content {
    position: static;
    width: 100%;
    padding: 16px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
}

/* Khung Danh sách video */
.video-list {
    position: static;
    width: 100%;
    padding: 16px;
    border: 1px solid #ddd;
    margin-top: 0;
}
```
### 3.	Các bước thực hiện trên DevTools
1.	Mở trang PTIT-LMS.
2.	Nhấn F12 để mở Developer Tools.
3.	Chọn biểu tượng Inspect Element.
4.	Nhấn vào khung "Nội dung bài học".
5.	Chọn tab Computed, kéo xuống mục Box Model để kiểm tra Content, Padding, Border và Margin.
6.	Thực hiện tương tự với khung "Danh sách video".
7.	Chuyển sang tab Styles, thử điều chỉnh các thuộc tính CSS.
8.	Quan sát kết quả để đảm bảo hai khung không còn chồng lấn và giao diện vẫn cân đối.
