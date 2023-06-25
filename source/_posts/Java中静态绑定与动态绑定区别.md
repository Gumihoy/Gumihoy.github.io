---
title: Java中静态绑定与动态绑定区别
date: 2010-10-01 08:00:00
# img: /source/images/xxx.jpg
top: false
hide: false
cover: false
# coverImg: /images/1.jpg
# password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: true
mathjax: false
# summary:
categories:
    - Java
tags:
    - Java
    - 静态绑定
    - 动态绑定
---

**`绑定`**: 将方法调用连接到方法体称为绑定

**`绑定`** 有两种类型：
- **静态绑定** ：在编译时映射方法。也叫`早期绑定`
- **动态绑定**：在运行时被解析。也叫`后期绑定`

### 静态绑定

编译器可以`在编译时解析的绑定`称为`静态绑定`或`早期绑定`。所有`private`、`static`和`final`方法的绑定都是`在编译时完成`的

#### 案例

`方法重载`是`静态绑定`的最好例子

```java

public class Main {

    public void print(Man man) {
        System.out.println("男人");
    }

    public void print(Women wm) {
        System.out.println("女人");
    }

    public static void main(String[] args) {
        Humanity m = new Man();
        Humanity wm = new Women();
        print(m);
        print(wm);
    }
}

public interface Humanity{}

public class Man implements Humanity {
}

public class Women implements Humanity {
}
```

### 动态绑定

程序`执行期间`解析方法调用`绑定`时，对象的类型是在程序执行过程中确定的，这样的过程在 `Java` 中称为`动态绑定`或`后期绑定`

#### 案例

`动态绑定`的最佳示例是`方法重写`，其中父类和派生类具有相同的方法。因此，对象的类型决定了要执行的方法

```java
public class Main {
    public static void main(String[] args) {
        Humanity m = new Man();
        Humanity wm = new Women();
        m.print();
        wm.print();
    }
}

public interface Humanity{
    void print();
}

public class Man implements Humanity {
    public void print() {
        System.out.println("男人");
    }
}

public class Women implements Humanity {
    public void print() {
        System.out.println("女人");
    }
}
```

### 静态绑定和动态绑定的区别
|序列号	| 静态绑定	| 动态绑定 |
|:----:|:-----|:-------|
|  1.	|	一种{% post_link Java中多态性：重写和重载 多态性 %}，它收集信息以在`编译时调用方法`。	|	一种{% post_link Java中多态性：重写和重载 多态性 %}，它收集信息以在`运行时调用方法`
|  2. 	|	绑定`发生在编译时`	| 	绑定`发生在运行时`
|  3. 	|	使用类型信息进行绑定	|	使用对象解析绑定
|  4. 	|	它也称为`早期绑定`，因为绑定`发生在编译期间`	|	它也称为`后期绑定`，因为`绑定发生在运行时`
|  5.	|	执行速度`很快`(相对于动态绑定)	|	执行速度`很慢`(相对于静态绑定)
|  6. 	|	方法重载是静态绑定的最好例子。	|	方法重写是动态绑定的最佳示例
|  7. 	|	`private`、`static`和`final`的方法静态绑定，因为`不能重写`它们。	|	其他非`private`、`static`和`final`方法的方法动态绑定，因为这些`方法可以重写`