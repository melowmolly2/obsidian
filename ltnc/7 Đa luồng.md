I'll read the uploaded PDF content right away.

# Lý thuyết tuần 7 — Đa luồng (Concurrency & Multithreaded Programming)

---

## 1. Vì sao cần Concurrency?

- Chạy nhiều chương trình / nhiều phần của cùng một chương trình **song song**.
- Tăng **throughput** & **tính tương tác** của ứng dụng.
- **Định luật Amdahl** — giới hạn lý thuyết về tăng tốc:

$$
\text{Speedup} = \frac{1}{B + \frac{1-B}{N}}
$$

Trong đó **B** = tỉ lệ code *không* song song được, **N** = số tiến trình/luồng.

---

## 2. Các đơn vị của Concurrency

| Loại | Đơn vị | Mô tả |
|---|---|---|
| Multi-processing | CPU | Nhiều CPU chạy đồng thời |
| Multi-tasking | Process | OS chuyển đổi giữa các tiến trình trên 1 CPU |
| Multi-threading | Thread | Nhiều luồng trong cùng 1 tiến trình |

---

## 3. Process vs Thread

- **Process**: chương trình đang chạy, **độc lập** & **tách biệt**.
- **Thread**: đường thực thi trong process, có **call stack riêng**, nhưng **dùng chung heap/data** của process.
- Java mặc định chạy 1 process → có thể tạo nhiều thread bên trong.

---

## 4. Tạo và khởi chạy Thread trong Java

Ba cách:

```java
// 1. Extends Thread
class MyThread extends Thread {
    public void run() { /* ... */ }
}

// 2. Runnable (anonymous class)
Thread t = new Thread(new Runnable() {
    public void run() { /* ... */ }
});

// 3. Runnable (lambda) — ưu tiên dùng
Thread t = new Thread(() -> { /* ... */ });
t.start();
```

**Nên dùng Runnable** vì Java không cho đa kế thừa (không extends được thêm class khác nếu đã extends Thread).

---

## 5. Vòng đời của Thread

```
NEW → RUNNABLE → (BLOCKED / WAITING / TIMED_WAITING) → TERMINATED
```

- `Thread.sleep(ms)` — tạm dừng luồng hiện tại.
- `thread.join()` — chờ luồng khác hoàn thành.

---

## 6. Executor Framework

Tách **submission** khỏi **execution policy** → dễ thay đổi sau.

```java
ExecutorService executor = Executors.newFixedThreadPool(4);
executor.submit(() -> System.out.println("Task chạy trong pool"));
executor.shutdown();
```

- **Executor**: `execute(Runnable)`
- **ExecutorService**: thêm `submit()`, quản lý lifecycle
- **ScheduledExecutorService**: thêm lập lịch thực thi

Nếu số task > thread đang rảnh → task xếp vào **Blocking Queue** chờ. Nếu queue đầy → **rejected**.

---

## 7. Callable & Future

`Runnable` không trả kết quả. Dùng **Callable** khi cần giá trị trả về hoặc throw checked exception:

```java
Callable<String> callable = () -> {
    Thread.sleep(2000);
    return "Kết quả";
};

Future<String> future = executor.submit(callable);
String result = future.get(); // Blocking — chờ kết quả
```

Các method quan trọng của `Future`:

| Method | Ý nghĩa |
|---|---|
| `get()` | Lấy kết quả (blocking) |
| `cancel(mayInterrupt)` | Huỷ task |
| `isCancelled()` | Đã bị huỷ? |
| `isDone()` | Hoàn thành? |

- `invokeAll(list)` — submit nhiều Callable, chờ **tất cả** xong.
- `invokeAny(list)` — trả kết quả của Callable **nhanh nhất**.

---

## 8. Vấn đề của Concurrency

| Loại | Vấn đề | Ví dụ |
|---|---|---|
| Access problem | **Race condition** — nhiều thread ghi đồng thời | `count` bị sai (985 thay vì 1000) |
| Visibility problem | **Memory Consistency Error** — thread A không thấy thay đổi của thread B | Deadlock |

---

## 9. Synchronization

**Hai nguyên tắc:**
1. Chỉ **1 thread** đọc/ghi shared variable tại một thời điểm (**atomicity**).
2. Thay đổi của thread này **hiển thị** với thread khác (**happens-before**).

```java
// Synchronized method
public synchronized void increment() { count++; }

// Synchronized block
synchronized(this) { count++; }
```

- **`volatile`** keyword: ngăn compiler tối ưu/sắp xếp lại lệnh quanh biến → đảm bảo visibility.

---

## 10. Locks

### ReentrantLock
- Tương đương `synchronized`, nhưng linh hoạt hơn.
- Thread nắm lock có thể **acquire lại** (reentrant) mà không bị block.
- `tryLock()` — thử lấy lock, **không block** nếu thất bại.

```java
ReentrantLock lock = new ReentrantLock();
lock.lock();
try { /* critical section */ }
finally { lock.unlock(); }
```

### ReadWriteLock
- **Read lock**: nhiều thread giữ đồng thời được (nếu không có write lock).
- **Write lock**: độc quyền.
- Hiệu năng tốt hơn khi **reads >> writes**.

---

## 11. Virtual Thread (Java 21+)

| | Platform Thread (kernel thread) | Virtual Thread |
|---|---|---|
| Quản lý bởi | OS | JVM |
| Tạo mới | System call (tốn kém) | Không cần system call |
| Context switch | OS-level (nặng) | JVM-level (nhẹ) |
| Memory | Lớn | Nhỏ |

```java
// API giống hệt platform thread!
Thread vt = Thread.ofVirtual().start(() -> System.out.println("Virtual!"));
```

Virtual thread chạy trên **carrier thread** bên dưới, JVM điều phối → scale được số lượng lớn mà chi phí thấp.

---

**Tóm tắt nhanh:**
> Thread → Runnable/Callable → ExecutorService → Future → Synchronized/Lock → Virtual Thread