# Hướng Dẫn Thêm Project Mới

Hướng dẫn này giúp bạn thêm một dự án mới vào website Tad.atelier một cách nhanh chóng và dễ dàng.

---

## Tổng Quan

Mỗi project cần **2 thành phần**:

1. **Folder ảnh** - chứa hình ảnh dự án
2. **Folder project** - chứa file `index.html` và thông tin dự án

---

## Các Bước Thêm Project Mới

### Bước 1: Chuẩn Bị Ảnh

1. Tạo folder mới trong `/assets/projects/`
2. Đặt tên theo format: `[SỐ]-[TÊN-THƯỜNG-KHÔNG-DẤU]`

Ví dụ:
```
/assets/projects/15-nha-mai/
```

3. Copy tất cả ảnh của dự án vào folder này
4. **Đặt tên ảnh front-page** là `00.Front-Page.JPG` (sẽ dùng làm thumbnail)

---

### Bước 2: Tạo Folder Project

1. Copy folder template từ `/projects/_template/`
2. Đặt tên folder mới **TRÙNG VỚI** tên folder trong `projects-data.js`

Ví dụ:
```
/projects/15-nha-mai/
```

3. Mở file `index.html` trong folder mới và chỉnh sửa:

#### 3.1. Sửa phần `<head>` (dòng 9)

```html
<title>Tad.atelier - [TÊN PROJECT CỦA BẠN]</title>
```

#### 3.2. Sửa phần mô tả (dòng ~56-60)

```html
<h1 class="fs-2">[TÊN PROJECT]</h1>
<p class="mt-2 mb-0 pb-0">[NĂM]</p>
<p class="mt-1">Location: [ĐỊA ĐIỂM]</p>
```

#### 3.3. Sửa mô tả tiếng Anh (dòng ~65-75)

Thay đoạn `[MÔ TẢ TIẾNG ANH]` bằng nội dung giới thiệu dự án.

#### 3.4. Sửa phần ảnh (từ dòng ~90 trở đi)

Mỗi ảnh cần 2 thay đổi:
- `data-src`: đường dẫn ảnh
- `src`: đường dẫn ảnh (giống data-src)

```html
<a data-src="/assets/projects/15-nha-mai/FILE-ẢNH.JPG" data-fancybox="gallery">
    <img src="/assets/projects/15-nha-mai/FILE-ẢNH.JPG" class="img-fluid">
</a>
```

**Mẹo về class ảnh:**
- `img-fluid` - ảnh bình thường
- `img-fluid img-horizontal` - ảnh ngang trong khung cao
- `img-fluid img-vertical` - ảnh dọc trong khung rộng

---

### Bước 3: Cập Nhật Data File

Mở file: `/assets/js/projects-data.js`

Thêm entry mới vào **ĐẦU MẢNG** (sau dòng có chú thích):

```javascript
{
    id: 15,
    name: "Tên Hiển Thị Trên Website",
    year: "2024",
    folder: "15-nha-mai",
    thumbnail: "/assets/projects/15-nha-mai/00.Front-Page.JPG"
},
```

**Lưu ý quan trọng:**
- `id`: Số thứ tự project (theo thứ tự 14, 15, 16...)
- `folder`: Tên folder project (phải trùng với folder trong `/projects/`)
- `thumbnail`: Đường dẫn đến ảnh front-page

---

### Bước 4: Kiểm Tra

Mở trình duyệt và truy cập:
- `http://localhost:PORT/projects` - xem danh sách
- `http://localhost:PORT/projects/15-nha-mai` - xem project mới

---

## Cấu Trúc Thư Mục

```
web1/
├── assets/
│   ├── projects/
│   │   ├── 14-the-clay-resort/
│   │   ├── 15-nha-mai/          ← Folder ảnh mới
│   │   └── ...
│   └── js/
│       └── projects-data.js      ← File data (cần cập nhật)
├── projects/
│   ├── _template/                ← Template để copy
│   ├── index.html                ← Trang danh sách (tự động)
│   ├── the-clay-resort/
│   └── 15-nha-mai/               ← Folder project mới
│       └── index.html
└── ...
```

---

## Checklist Trước Khi Hoàn Thành

- [ ] Folder ảnh đã tạo trong `/assets/projects/`
- [ ] Ảnh front-page đặt tên `00.Front-Page.JPG`
- [ ] Folder project đã tạo trong `/projects/`
- [ ] File `index.html` đã chỉnh sửa đầy đủ thông tin
- [ ] File `projects-data.js` đã thêm entry mới
- [ ] Đã test trên trình duyệt

---

## Xử Lý Sự Cố

### Trang Projects không hiển thị ảnh mới?

Kiểm tra:
1. Folder name trong `projects-data.js` có trùng với folder thực tế không?
2. Đường dẫn thumbnail có đúng không?
3. File `projects-data.js` có lỗi syntax không (thừa/thiếu dấu phẩy, ngoặc)?

### Ảnh không hiển thị trong project page?

Kiểm tra:
1. Đường dẫn trong `data-src` và `src` có bắt đầu bằng `/` không?
2. Tên file ảnh có chính xác không (phân biệt hoa thường)?

### Lỗi JavaScript?

Mở DevTools (F12) → Console để xem thông báo lỗi.

---

## Liên Hệ

Nếu có thắc mắc, liên hệ: Tad.atelier
