# 📚 Lý thuyết Tuần 9 — Tích hợp và Triển khai (UET.CS2043)

---

## 1. Vấn đề "Works on My Machine"

Nguyên nhân code chạy tốt trên máy mình nhưng lỗi ở chỗ khác:

- **Môi trường khác nhau**: JDK 8 vs JDK 17, Windows vs Linux
- **Hard-coded paths**: `C:\Users\Tuan\Documents\data.txt`
- **Thiếu thư viện**: Quên copy `.jar`
- **Xung đột phiên bản**: dùng v1.0, máy khác có v2.0

**Giải pháp**: Automation — Maven, Checkstyle, SLF4J/Logback, GitHub Actions

---

## 2. Apache Maven

### Maven là gì?
- Công cụ quản lý dự án Java, dựa trên **Project Object Model (POM)**
- Chức năng: quản lý dependencies, biên dịch, đóng gói, test, tạo tài liệu, quản lý phiên bản

### Cấu trúc `pom.xml`
```xml
<project>
  <groupId>com.example</groupId>      <!-- Tên tổ chức -->
  <artifactId>my-app</artifactId>     <!-- Tên dự án -->
  <version>1.0-SNAPSHOT</version>
  <properties>
    <maven.compiler.source>17</maven.compiler.source>
  </properties>
</project>
```

### Quản lý thư viện (Dependencies)
- Chỉ khai báo trong `<dependencies>`, Maven tự tải từ **Maven Central**
- Thứ tự tìm thư viện: **Local** (`~/.m2`) → **Central** → **Remote/Private** (Nexus, Artifactory)

### Maven Build Lifecycle
| Lệnh | Tác dụng |
|---|---|
| `mvn clean` | Xóa thư mục `target` |
| `mvn compile` | Biên dịch `src/main/java` |
| `mvn test` | Biên dịch + chạy test, xuất báo cáo |
| `mvn package` | Test → đóng gói thành JAR/WAR |
| `mvn install` | Đóng gói → đưa vào Local Repository |

> ⚠️ Chạy phase sau = tự động kích hoạt tất cả phase trước. Nếu `mvn package` mà test fail → **dừng ngay, không tạo `.jar`**

### Maven Plugins phổ biến
- `maven-compiler-plugin` — biên dịch Java
- `maven-surefire-plugin` — chạy Unit Test
- `maven-jar-plugin` — tạo JAR
- `maven-checkstyle-plugin` — kiểm tra code standard

---

## 3. Logging — SLF4J & Logback

### Tại sao cần Logging?
- **Debugging**: tìm nguyên nhân lỗi
- **Auditing**: ai làm gì, lúc mấy giờ
- **Monitoring**: theo dõi sức khỏe hệ thống
- **Forensics**: điều tra sự cố sau khi xảy ra

### `System.out.println` vs Logger
| | `System.out.println` | Logging Framework |
|---|---|---|
| Bật/tắt | Không thể tắt | Tắt theo level |
| Đầu ra | Chỉ Console | File, DB, Console |
| I/O | Blocking (chậm) | Async (nhanh hơn) |
| Context | Không có | Timestamp, Class, Thread |

### Log Levels (tăng dần mức nghiêm trọng)
```
TRACE < DEBUG < INFO < WARN < ERROR
```
- **TRACE**: chi tiết nhỏ nhất (vào/ra hàm, giá trị biến)
- **DEBUG**: gỡ lỗi khi phát triển
- **INFO**: vận hành bình thường (start app, login success)
- **WARN**: cảnh báo, hệ thống vẫn chạy nhưng có rủi ro
- **ERROR**: lỗi chức năng, Exception cần xử lý

> **Quy tắc**: cấu hình `level=INFO` thì `TRACE` và `DEBUG` bị ẩn

### Kiến trúc SLF4J & Logback
- **SLF4J** = interface (API), developer chỉ code với SLF4J
- **Logback / Log4j2** = implementation thực sự ghi log

### Parameterized Logging (quan trọng!)
```java
// ❌ Sai — tốn chi phí cộng chuỗi dù log bị tắt
logger.debug("Giá trị: " + obj.toString() + " user: " + user.getName());

// ✅ Đúng — chỉ thực hiện khi debug được bật
logger.debug("Giá trị: {} user: {}", obj, user.getName());
```

### Cấu hình Logback (`logback.xml`)
```xml
<configuration>
  <appender name="FILE" class="ch.qos.logback.core.FileAppender">
    <file>app.log</file>
    <encoder>
      <pattern>%d{HH:mm:ss} [%thread] %-5level %logger{36} - %msg%n</pattern>
    </encoder>
  </appender>
  <root level="info">
    <appender-ref ref="FILE" />
  </root>
</configuration>
```

---

## 4. Static Code Analysis — Checkstyle

### Phân tích tĩnh là gì?
Kiểm tra mã nguồn **tự động mà không cần chạy** chương trình. Mục tiêu:
- Tìm lỗi tiềm ẩn (NullPointer, Resource Leak)
- Kiểm tra coding standard (Checkstyle)
- Đo độ phức tạp (Cyclomatic Complexity)
- Tìm code trùng lặp

### Checkstyle bắt lỗi gì?
- Tên biến/hàm sai quy tắc (không đúng camelCase)
- Thiếu Javadoc cho public API
- Dòng code quá dài (> 120 ký tự)
- Import không dùng đến
- Nhiều câu lệnh trên 1 dòng

Bộ quy tắc phổ biến: **Sun Checks**, **Google Checks**

### Cyclomatic Complexity
- Đo số **đường đi độc lập** qua code (số lượng `if/else`, `for`, `switch`)
- Complexity > 10 → cần **refactor**, tách hàm nhỏ hơn

### Tích hợp vào Maven
```xml
<plugin>
  <artifactId>maven-checkstyle-plugin</artifactId>
  <version>3.2.0</version>
  <configuration>
    <configLocation>google_checks.xml</configLocation>
    <failOnViolation>true</failOnViolation>
  </configuration>
  <executions>
    <execution>
      <phase>validate</phase>
      <goals><goal>check</goal></goals>
    </execution>
  </executions>
</plugin>
```

### Công cụ khác (Optional)
- **SpotBugs**: tìm lỗi logic (so sánh String bằng `==`, quên đóng Stream)
- **PMD**: tìm code thừa, code chết
- **SonarQube**: dashboard tổng hợp tất cả chỉ số chất lượng

---

## 5. CI/CD — GitHub Actions

### CI/CD là gì?
| | Continuous Integration (CI) | Continuous Delivery (CD) |
|---|---|---|
| Mục tiêu | Phát hiện lỗi sớm — **Fail Fast** | Phát hành phần mềm nhanh |
| Khi nào | Mỗi lần push/merge code | Sau khi CI pass |
| Làm gì | Auto Build + Test | Auto đóng gói + Deploy lên Staging/Production |

### Kiến trúc GitHub Actions
- **Workflow**: quy trình tự động (file `.yml`)
- **Event**: sự kiện kích hoạt (push, pull_request, schedule...)
- **Job**: tập hợp các step, chạy trên 1 Runner
- **Step**: từng hành động nhỏ (checkout, cài Java, chạy Maven)
- **Runner**: máy ảo thực thi (ubuntu-latest, windows-latest...)

### File YAML cơ bản
```yaml
name: Java CI
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
          cache: 'maven'        # Cache deps để build nhanh hơn
      - run: mvn package
```

### Các tính năng nâng cao
- **Cache dependencies**: thêm `cache: 'maven'` → GitHub tự lưu `~/.m2`
- **Matrix Build**: test trên nhiều OS cùng lúc
  ```yaml
  strategy:
    matrix:
      os: [ubuntu-latest, windows-latest, macos-latest]
  ```
- **Artifacts**: lưu file `.jar` sau build (Runner bị hủy sau khi xong)
  ```yaml
  - uses: actions/upload-artifact@v3
    with:
      name: my-app-jar
      path: target/*.jar
  ```
- **Workflow Badge**: gắn lên `README.md` để hiển thị trạng thái build
- **Branch Protection**: yêu cầu CI xanh mới cho merge vào `main`

---

## 📝 Tổng kết so sánh: Dự án lớp vs Doanh nghiệp

| Tiêu chí | Lớp học | Doanh nghiệp |
|---|---|---|
| Thư viện | Copy `.jar` thủ công | Khai báo `pom.xml`, Maven tự tải |
| Build | Bấm "Run" trong IDE | `mvn package` — độc lập IDE |
| Debug | `System.out.println` | Logging system (File, Levels) |
| Deploy | Copy qua USB/Zalo | CI/CD Pipeline, Docker |