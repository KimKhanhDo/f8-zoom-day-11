```css
@media (max-width: 1399.98px) {
    .container {
        max-width: 1140px;
    }
}
```

-   `max-width` của `.container` (1140px) luôn nhỏ hơn `max-width` trong media query (1399.98px), giúp tạo khoảng trống hai bên màn hình.
-   Trong `.container`, ta dùng `margin-left: auto;` và `margin-right: auto;` để canh giữa phần tử.

---

## 🧱 ROW & COLUMN

-   `.row` là con của `.container` nhưng **không bắt buộc** phải là con **trực tiếp**.
-   `.col-*` **bắt buộc là con trực tiếp** của `.row`.

---

### ✅ So sánh tư duy `col-*` vs `row-cols-*`

| Tên class    | Tư duy                              | Ví dụ        | Giải thích                                    |
| ------------ | ----------------------------------- | ------------ | --------------------------------------------- |
| `col-*`      | Số **cột cơ sở** (trên tổng 12 cột) | `col-6`      | Chiếm 6/12 cột → hiển thị 2 cột trên 1 hàng   |
| `row-cols-*` | Số **cột hiển thị** trong hàng      | `row-cols-3` | Chia đều 3 cột trong hàng → mỗi cột = `col-4` |

---

### 📀 Quy tắc kiểm soát độ rộng cột

```css
/*
  Đảm bảo độ rộng cột được kiểm soát bằng CSS thay vì flexbox tự động:

  flex: 0 0 auto;
  → flex-grow: 0   → không cho giãn
  → flex-shrink: 0 → không co lại
  → flex-basis: auto → dùng width cụ thể được chỉ định
*/

.row > [class*='col-'],
.row[class*='row-cols-'] > * {
    flex: 0 0 auto;
}
```

---

## 📝 Ghi chú sử dụng

### Khi cần **col khác nhau**:

Dùng `col-*` để chỉ định rõ kích thước từng cột:

```html
<div class="row">
    <div class="col col-3"></div>
    <div class="col col-5"></div>
    <div class="col col-4"></div>
</div>
```

### Khi các cột **đều nhau**:

Dùng `row-cols-*` để code sạch hơn và dễ hiểu:

```html
<!-- Nhìn là biết có 3 cột đều nhau -->
<div class="row row-cols-3">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
</div>
```

So với cách dài dòng hơn:

```html
<!-- Cách này cũng đúng nhưng kém clean hơn -->
<div class="row">
    <div class="col col-4"></div>
    <div class="col col-4"></div>
    <div class="col col-4"></div>
</div>
```

---

> 🔍 **Chú ý**:
>
> -   Tên class `col-*` → thể hiện **số cột cơ sở** (trong 12 cột).
> -   Tên class `row-cols-*` → thể hiện **số cột hiển thị** trong một hàng.
