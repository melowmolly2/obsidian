
## Mô hình MVC — Lý thuyết

---

### 1. Tại sao cần MVC?

Ứng dụng lớn → khó **bảo trì**, **tái sử dụng**, **làm việc nhóm**. MVC giải quyết bằng "chia để trị".

---

### 2. MVC là gì?

**MVC = Model – View – Controller** — mẫu kiến trúc tách ứng dụng thành 3 tầng độc lập.

```
┌─────────┐   cập nhật    ┌──────────┐
│  Model  │ ←──────────── │Controller│
│(dữ liệu)│   ──────────→ │  (xử lý) │
└─────────┘               └──────────┘
                                │ cập nhật
                                ▼
                          ┌──────────┐
                          │   View   │
                          │(giao diện)│
                          └──────────┘
                                │ tương tác
                                └──────────→ người dùng
```

---

### 3. Ba thành phần

| Thành phần     | Vai trò                                                         |
| -------------- | --------------------------------------------------------------- |
| **Model**      | Lớp dữ liệu: đối tượng, logic lưu trữ (DB, file, serialization) |
| **View**       | Giao diện người dùng (FXML, JavaFX controls, CSS)               |
| **Controller** | Trung gian: nhận sự kiện từ View → gọi Model → cập nhật View    |

---

### 4. Lợi ích

- **Tách biệt trách nhiệm** — mỗi tầng chỉ lo việc của mình
- **Dễ bảo trì & mở rộng** — sửa View không ảnh hưởng Model
- **Song song phát triển** — team A làm View, team B làm Model
- **Tái sử dụng** — Model dùng lại cho nhiều View khác nhau

---

### 5. MVC trong JavaFX (theo tài liệu)

| Tầng | Công nghệ |
|---|---|
| **View** | FXML + Scene Builder + CSS |
| **Controller** | Java class xử lý Event (click, keypress, drag…) |
| **Model** | Java objects + Serialization + JDBC/SQLite |

---

### 6. Luồng hoạt động điển hình

```
Người dùng click button
       ↓
  Controller.handleClick()
       ↓               ↓
  Model.getData()   View.update()
       ↓
  (DB / File / Memory)
```

---

### 7. Serialization (thuộc Model)

Chuyển đối tượng Java → byte stream để **lưu file / truyền mạng**.

```java
public class Account implements Serializable {
    private static final long serialVersionUID = 1L;
    private transient String password; // không serialize
}
```

- `implements Serializable` — bắt buộc
- `serialVersionUID` — đảm bảo tương thích phiên bản
- `transient` — trường bị bỏ qua khi serialize

---

### 8. Kết nối DB (JDBC + SQLite — thuộc Model)

```sql
CREATE TABLE users (
    id    INTEGER PRIMARY KEY AUTOINCREMENT,
    name  VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE
);
```

JDBC là API chuẩn Java kết nối mọi DBMS (MySQL, SQLite, PostgreSQL…) theo cùng một cách.

---

**Tóm lại:** MVC = tách code thành 3 tầng rõ ràng → dự án lớn vẫn manageable.