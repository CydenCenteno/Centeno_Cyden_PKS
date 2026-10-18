# Fundamentals of Programming — Java Reference

## Program Skeleton

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, world");
    }
}
```

File name must match public class name: `Main.java`.

## Input

```java
import java.util.Scanner;

public class InputDemo {
    public static void main(String[] args) {
        try (Scanner in = new Scanner(System.in)) {
            System.out.print("Enter age: ");
            int age = in.nextInt();
            System.out.println("Age: " + age);
        }
    }
}
```

## Loops & Conditions

```java
for (int i = 1; i <= 5; i++) {
    if (i % 2 == 0) {
        System.out.println(i + " even");
    } else {
        System.out.println(i + " odd");
    }
}
```

## Methods

```java
public static int add(int a, int b) {
    return a + b;
}
```

## Class with Encapsulation

```java
public class Student {
    private final String name;
    private int grade;

    public Student(String name, int grade) {
        this.name = name;
        setGrade(grade);
    }

    public String getName() { return name; }
    public int getGrade() { return grade; }

    public void setGrade(int grade) {
        if (grade < 0 || grade > 100) {
            throw new IllegalArgumentException("Grade must be 0-100");
        }
        this.grade = grade;
    }
}
```

## Inheritance & Polymorphism

```java
abstract class Shape {
    abstract double area();
}

class Circle extends Shape {
    private final double r;
    Circle(double r) { this.r = r; }
    @Override double area() { return Math.PI * r * r; }
}

class Rect extends Shape {
    private final double w, h;
    Rect(double w, double h) { this.w = w; this.h = h; }
    @Override double area() { return w * h; }
}
```

`Shape s = new Circle(2); s.area();` → Circle's version runs.

## Collections

```java
import java.util.*;

List<String> names = new ArrayList<>();
names.add("Ana");
Map<String, Integer> scores = new HashMap<>();
scores.put("Ana", 95);
Set<Integer> unique = new HashSet<>(List.of(1, 2, 2, 3));  // {1,2,3}
```

## Exceptions

```java
try {
    int n = Integer.parseInt(text);
} catch (NumberFormatException e) {
    System.err.println("Not a number: " + text);
} finally {
    System.out.println("Always runs");
}
```

## Common Gotchas

- Compare strings with `.equals()`, not `==`.
- `int / int` truncates — cast one operand to `double`.
- `NullPointerException` — check null before use.
- Arrays are fixed size; `array.length` (no parentheses), `list.size()`, `string.length()`.
- Checked exceptions must be caught or declared with `throws`.

## Interface vs Abstract Class

- **Interface** — contract; class can implement many.
- **Abstract class** — shared state + partial implementation; single inheritance.
