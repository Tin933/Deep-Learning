# Website phân loại ảnh CIFAR-10 bằng Flask

## 1. Giới thiệu

Đây là một website được xây dựng bằng **Flask** để kết nối với mô hình học sâu đã huấn luyện trên bộ dữ liệu **CIFAR-10**. Người dùng có thể tải ảnh từ máy tính lên, hệ thống sẽ xử lý ảnh và trả về kết quả phân loại tương ứng như:

- con chó
- con mèo
- xe tải
- máy bay
- chim
- ...

---

## 2. Mục tiêu của website

- Tạo giao diện web để người dùng tải ảnh lên.
- Kết nối website với mô hình `cifar10_model.keras` đã train.
- Hiển thị kết quả dự đoán trực quan.
- Hiển thị lại ảnh người dùng đã chọn.
- Hỗ trợ trình bày sản phẩm trong bài lab CNN.

---

## 3. Công nghệ sử dụng

- **Python**
- **Flask**
- **TensorFlow / Keras**
- **HTML / CSS / JavaScript**
- **Pillow** để xử lý ảnh

---

## 4. Chức năng chính

### 4.1 Tải ảnh lên

Người dùng chọn ảnh từ máy tính và gửi lên hệ thống.

### 4.2 Xem trước ảnh đã chọn

Ảnh người dùng chọn sẽ được hiển thị ngay trên giao diện để dễ kiểm tra.

### 4.3 Phân loại ảnh

Ảnh được resize về đúng kích thước đầu vào của mô hình (**32x32**) và đưa vào mô hình ResNet đã huấn luyện để dự đoán lớp.

### 4.4 Hiển thị kết quả

Sau khi dự đoán, website hiển thị:

- nhãn dự đoán chính
- độ tin cậy
- top 3 dự đoán có xác suất cao nhất

### 4.5 Thông báo lỗi

Nếu người dùng chưa chọn ảnh hoặc mô hình chưa tải được, hệ thống sẽ hiển thị thông báo lỗi rõ ràng.

---

## 5. Giao diện website

Website gồm 2 khu vực chính:

### Bên trái

- Hiển thị ảnh người dùng đã chọn
- Cho phép xem trước ảnh trước khi bấm phân loại
  ![giao diện bên trái](trai.jpg)

### Bên phải

- Nút chọn ảnh
- Nút phân loại ảnh
- Khu vực hiển thị kết quả dự đoán
- Hiển thị top 3 nhãn có độ tin cậy cao nhất
  ![giao diện bên phải](/static/imgs/phai.jpg)

---

## 6. Mô tả hoạt động của hệ thống

Quy trình hoạt động của website:

1. Người dùng mở website.
2. Người dùng chọn một ảnh từ máy tính.
3. Ảnh được hiển thị trên giao diện.
4. Người dùng nhấn nút **Phân loại ảnh**.
5. Ảnh được tiền xử lý:
   - chuyển về RGB
   - resize về 32x32
   - chuẩn hóa giá trị pixel về khoảng `[0, 1]`
6. Mô hình ResNet thực hiện dự đoán.
7. Website trả về nhãn dự đoán và độ tin cậy.

---

## 7. Cấu trúc thư mục

```bash
flask_cifar10_app/
│
├── app.py
├── requirements.txt
├── cifar10_model.keras
│
├── templates/
│   └── index.html
│
├── static/
│   └── style.css
│
└── README.md
```

---

## 8. Cách chạy chương trình

### Bước 1: Cài thư viện

```bash
pip install -r requirements.txt
```

### Bước 2: Chạy ứng dụng Flask

```bash
python app.py
```

### Bước 3: Mở website

Truy cập trình duyệt tại:

```bash
http://127.0.0.1:5000
```

---

### Mô hình resnet được train với 100 epoch và đạt accuracy 90%

![Huấn luyện mô hình](/static/imgs/train.jpg)
![prediction với test dataset](/static/imgs/test.jpg)

### Giao diện tổng quan

![Giao diện tổng quan với Flask](/static/imgs/home.jpg)
![Sau khi import ảnh](/static/imgs/immport.jpg)

### Kết quả phân loại

![Kết quả phân loại](/static/imgs/predict.jpg)

```

```
