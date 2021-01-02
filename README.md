# Yêu cầu
- Sử dụng 1 file ảnh GLB, in ra kích thước chiều dài, chiều rộng và chiều sâu trên 3 đường thẳng trên model

# Ý tưởng
- Sample Filament đã có sẵn ModelViewer để model từ file hiển thị lên màn hình, lấy thông số trực tiếp từ từ ModelViewer, nhưng vì không tìm được cách lấy trực tiếp nên sẽ lấy qua Boundingbox của ModelViewer, sau khi lấy được HalfExtend thì sẽ lấy được 3 kích thước chiều dài, rộng và chiều sâu.
- Sau khi đã có giá trị của 3 chiều rồi thì vẽ trực tiếp 3 đường thẳng lên ModelViewer
