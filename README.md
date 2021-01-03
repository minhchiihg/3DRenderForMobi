# SE04-Nhom13.1
# Người hướng dẫn
- Thầy Bùi Sỹ Nguyên
# Thành viên trong nhóm:
- Nguyễn Phong Lưu
- Nguyễn Thị Minh Chi
- Nguyễn Thu Hòa
- Dương Thị Mỹ Duyên
- Hoàng Đức Anh

# Ý tưởng dự án
- Hiện nay các công cụ Marketing đều hướng tới mục tiêu làm sao có thể khiến cho khách hàng ghi nhớ hình ảnh của sản phẩm một cách chính xác nhất vào tiềm thức. Với các sản phẩm nhìn chung, khách hàng rất khó để đánh giá về tổng thể chất lượng, hình ảnh sản phẩm.
- Để giải quyết vấn đề đó, hình ảnh 3D được áp dụng để mang đến cái nhìn tổng thể và chính xác hơn về sản phẩm cho khách hàng, và Google Filament là 1 công cụ hỗ trợ rất tốt cho việc hiển thị vật thể 3D. Ở đây, nhóm chúng em lựa chọn công việc cho dự án là mô tả vật thể qua hình ảnh 3D và hiển thị các thông số kích thước của vật thể sử dụng Google Filament.

# Goals
- Sử dụng 1 file ảnh GLB, in ra kích thước chiều dài, chiều rộng và chiều sâu trên 3 đường thẳng trên model

# Công nghệ và công cụ sử dụng
- Công cụ: Visual Studio 2019, Android Studio, Git for Windows( Git Bash), Cmake, Ninja, Clang, Python 3, Windows 10 SDK, Android SDK, Android NDK, JDK.
- Ngôn ngữ sử dụng: Kotlin.
- Công cụ hỗ trợ 3D cho Android: Google Filament
- Công cụ phát triển phần mềm: Github

# Triển khai:
## Build Filament
- Sau khi cài đầy đủ các công cụ ở trên thì bắt đầu thực hiện việc build Filament.
### Desktop Tools

- Chạy cmake ở thư mục Filament.

```
mkdir out\cmake-release
cd out\cmake-release
cmake ^
    -G Ninja ^
    -DCMAKE_INSTALL_PREFIX=..\release\filament ^
    -DFILAMENT_ENABLE_JAVA=NO ^
    -DCMAKE_BUILD_TYPE=Release ^
    ..\..
```

- Build công cụ cần thiết.

  ```
  ninja matc resgen cmgen
  ```
  sau khi cài xong tiếp tục chạy
  ```
  ninja install
  ```

### Build

- Tạo thư mục build.
  ```
  mkdir out\cmake-android-release-aarch64
  mkdir out\cmake-android-release-arm7
  mkdir out\cmake-android-release-x86_64
  mkdir out\cmake-android-release-x86
  ```

- Chạy cmake cho từng thư mục.

  ```
  cd out\cmake-android-release-aarch64
  cmake ^
    -G Ninja ^
    -DCMAKE_BUILD_TYPE=Release ^
    -DCMAKE_INSTALL_PREFIX=..\android-release\filament ^
    -DCMAKE_TOOLCHAIN_FILE=..\..\build\toolchain-aarch64-linux-android.cmake ^
    ..\..

  cd out\cmake-android-release-arm7
  cmake ^
    -G Ninja ^
    -DCMAKE_BUILD_TYPE=Release ^
    -DCMAKE_INSTALL_PREFIX=..\android-release\filament ^
    -DCMAKE_TOOLCHAIN_FILE=..\..\build\toolchain-arm7-linux-android.cmake ^
    ..\..

  cd out\cmake-android-release-x86_64
  cmake ^
    -G Ninja ^
    -DCMAKE_BUILD_TYPE=Release ^
    -DCMAKE_INSTALL_PREFIX=..\android-release\filament ^
    -DCMAKE_TOOLCHAIN_FILE=..\..\build\toolchain-x86_64-linux-android.cmake ^
    ..\..

  cd out\cmake-android-release-x86
  cmake ^
    -G Ninja ^
    -DCMAKE_BUILD_TYPE=Release ^
    -DCMAKE_INSTALL_PREFIX=..\android-release\filament ^
    -DCMAKE_TOOLCHAIN_FILE=..\..\build\toolchain-x86-linux-android.cmake ^
    ..\..
  ```
- Build.
  ở mỗi thư mục chạy lệnh
  ```
  ninja install
  ```
### Tạo file AAR

  ```
  cd android
  gradlew -Pfilament_dist_dir=..\out\android-release\filament assembleRelease
  copy filament-android\build\outputs\aar\filament-android-release.aar ..\..\out\
  ```
## Chạy Sample-gltf-viewer để thực hiện yêu cầu
- Sample Filament đã có sẵn ModelViewer để model từ file hiển thị lên màn hình, lấy thông số trực tiếp từ từ ModelViewer, nhưng vì không tìm được cách lấy trực tiếp nên sẽ lấy qua Boundingbox của ModelViewer, sau khi lấy được HalfExtend thì sẽ lấy được 3 kích thước chiều dài, rộng và chiều sâu.

![image](https://user-images.githubusercontent.com/71346057/103465358-610dcb00-4d6d-11eb-9707-07731d75a38b.png)

- Sau khi đã có giá trị của 3 chiều rồi thì vẽ trực tiếp 3 đường thẳng lên ModelViewer



