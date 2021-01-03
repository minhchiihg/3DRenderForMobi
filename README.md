SE04-Nhom13.1
Thành viên trong nhóm:
Nguyễn Phong Lưu
Nguyễn Thị Minh Chi
Nguyễn Thu Hòa
Dương Thị Mỹ Duyên
Hoàng Đức Anh
1. Ý tưởng dự án
   Hiện nay các công cụ Marketing bất động sản đều hướng tới mục tiêu làm sao có thể khiến cho khách hàng ghi nhớ hình ảnh dự án vào tiềm thức. Với các sản phẩm bất động sản nhìn chung, khách hàng rất khó để đánh giá về tổng thể chất lượng. 
   Để giải quyết vấn đề đó, hình ảnh 3D thiết kế công trình và diễn họa được sản xuất để mang đến cái nhìn tổng thể về ngôi nhà hơn cho khách hàng. Ở đây, nhóm chúng em lựa chọn đề tài dự án là mô tả vật thể qua hình ảnh 3D và các thông số kích thước của vật thể.
2. Goals
Sử dụng 1 file ảnh GLB, in ra kích thước chiều dài, chiều rộng và chiều sâu trên 3 đường thẳng trên model
3. Công nghệ và công cụ sử dụng
3.1. Công nghệ
Ngôn ngữ lập trình:
Kotlin
3.2. Công cụ sử dụng
Visual Studio Code
Android Studio
4.Objectives:
   Sample Filament đã có sẵn ModelViewer để model từ file hiển thị lên màn hình, lấy thông số trực tiếp từ từ ModelViewer, nhưng vì không tìm được cách lấy trực tiếp nên sẽ lấy qua Boundingbox của ModelViewer, sau khi lấy được HalfExtend thì sẽ lấy được 3 kích thước chiều dài, rộng và chiều sâu.

![image](https://user-images.githubusercontent.com/71346057/103465358-610dcb00-4d6d-11eb-9707-07731d75a38b.png)

   Sau khi đã có giá trị của 3 chiều rồi thì vẽ trực tiếp 3 đường thẳng lên ModelViewer

