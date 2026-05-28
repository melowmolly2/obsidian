## Bài 1 - Trắc nghiệm (minh họa) - 5 điểm
### Đoạn code 1:
```Java
class Employee {  
    protected String name;  
    private double salary;  
  
    Employee(String name, double salary) {  
        this.name = name;  
        this.salary = salary;  
    }  
  
    public static String policy() {  
        return "standard";  
    }  
  
    public double income() {  
        return salary;  
    }  
  
    public String role() {  
        return "Employee";  
    }  
}  
  
class Manager extends Employee {  
    private double bonus;  
  
    Manager(String name, double salary, double bonus) {  
        super(name, salary);  
        this.bonus = bonus;  
    }  
  
    public static String policy() {  
        return "management";  
    }  
  
    @Override  
    public double income() {  
        return super.income() + bonus;  
    }  
  
    @Override  
    public String role() {  
        return "Manager";  
    }  
}  
  
public class Main {  
    public static void main(String[] args) {  
        Employee e = new Manager("Lan", 1000, 300);  
        System.out.println(e.role());  
        System.out.println(e.income());  
        System.out.println(e.policy());  
        System.out.println(((Manager) e).policy());  
    }  
}
```
### Câu hỏi cho đoạn code 1
1. Output của chương trình là gì?
	```
	Manager
	1300
	standard
	management
	```
2. Vì sao lời gọi `e.role()` cho kết quả khác với `e.policy()`? 
	Vì `e.role()` là phương thức thông thường, áp dụng cơ chế **liên kết động (dynamic binding)**, nên tại thời điểm thực thi (runtime) nó gọi phương thức của đối tượng thực tế là `Manager`. Trong khi đó, `e.policy()` là phương thức tĩnh (`static`), áp dụng cơ chế **liên kết tĩnh (static binding)**, trình biên dịch 