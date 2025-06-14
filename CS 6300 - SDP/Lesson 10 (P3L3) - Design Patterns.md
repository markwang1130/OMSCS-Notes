# Lesson 10

It can be difficult to decide on a design that will best fit our software system. Therefore, in this lesson we will look into _design patterns_ which can help to provide reusability to our software system.

### 🎯 What Is a Design Pattern?

A **design pattern** is a **reusable solution** to a **common problem** that occurs in software design.  
It is not a piece of code, but a **conceptual template** that can be applied to similar design challenges across different systems.

---

#### 🔍 Key Characteristics

| Concept             | Explanation                                                                 |
| ------------------- | --------------------------------------------------------------------------- |
| **Not code**        | It's not a concrete class or method, but a general approach or structure.   |
| **Reusable**        | Can be applied to many problems in different systems.                       |
| **Abstract**        | Describes relationships and responsibilities, not specific implementations. |
| **Well-documented** | Patterns are well-known and named (e.g., Singleton, Observer).              |


> 📌 Patterns help us think at a higher level of design, beyond the level of syntax and language.

---

#### 💬 Analogy: Chairs and Patterns （类比：椅子和设计模式）

Imagine designing different chairs—office chair, dining chair, gaming chair.  
They all follow a **general chair design**: four legs, a seat, and a backrest.

This **"chair pattern"** is like a **design pattern** in software:
- Not a specific chair, but a reusable **design idea**.
- Can be **implemented in different styles** for different needs.

> 🔁 类比：设计模式就像“椅子的设计图”，是解决某类设计问题的通用方案，不是代码本身。

---

#### 🧠 Why Use Design Patterns?

- ✅ Provide **standard vocabulary** for communicating designs (e.g., “Use a Strategy pattern here”).
- ✅ Promote **best practices** based on proven solutions.
- ✅ Improve **modularity** and **decoupling** in your code.
- ✅ Make systems **easier to understand, maintain, and evolve**.

> 🎓 In short, patterns make your design **clearer, cleaner, and more professional**.


## History Of Design Patterns

The history of design patterns could be summarized as:

- 1977: Christopher Alexander introduces the idea of patterns as successful solutions to problems
- 1987: Ward Cunningham and Ken Beck leverage Alexander's idea in the context of an OO language
- 1987: Eric Gamm's dissertation on importance of patterns and how to capture them
- 1992: Jim Coplien's book, _Advanced C++ Programming Styles and Idioms_
- 1994: Gang of Four (Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides) and their book, _Design Patterns: Elements of Reusable Object-Oriented Software_

## Patterns Catalogue

There are five main categories of design patterns we may be concerned with:

1. **Fundamental**
2. **Creational**
3. **Structural**
4. **Behavioral**
5. **Concurrency**

### 🎯 Categories of Design Patterns

Design patterns offer reusable solutions to common design problems. They can be grouped into five major categories:

---

#### 🧩 Fundamental Patterns
- Cover basic principles and idioms like delegation, layering, or composition.
- Influence architecture and class design.
- Examples: Delegation, Composition, Interface Segregation, Dependency Injection.
- 🔁 类比：编程基本功，是设计的地基。

---

#### 🏗️ Creational Patterns
- Deal with object creation, abstracting the instantiation logic.
- Goal: Flexibility and decoupling of client code.
- Examples: Singleton, Factory Method, Abstract Factory, Builder, Prototype.
- 🔁 类比：房屋建造风格。

---

#### 🧱 Structural Patterns
- Focus on class and object composition.
- Help create flexible, reusable software structures.
- Examples: Adapter, Composite, Decorator, Facade, Proxy, Bridge.
- 🔁 类比：模块拼装方式。

---

#### 🔄 Behavioral Patterns
- Focus on communication and responsibilities among objects.
- Help manage complex workflows and control flow.
- Examples: Observer, Strategy, Command, State, Mediator, Template Method.
- 🔁 类比：团队合作流程。

---

#### ⚙️ Concurrency Patterns
- Help manage multi-threaded programming.
- Address resource sharing, synchronization, and task parallelism.
- Examples: Thread Pool, Producer-Consumer, Future/Promise, Read-Write Lock.
- 🔁 类比：流水线并发调度。


We will cover some patterns from each category. For more information on patterns in each category see the [Wiki page on software design patterns](https://en.wikipedia.org/wiki/Software_design_pattern).

## Pattern Format

The format of a design pattern is as follows:

- Name
- Intent
- Applicability
- Structure
- Sample code

There are more formats which include fields such as motivation, consequences, implementation, and related patterns. However, for the purpose of this class we will mainly focus on the five attributes above for each design pattern.

## Factory Method Pattern

Below are properties of the factory method pattern:

### Intent
Allows for creating objects without specifying their class by invoking a factory method (i.e., a method whose main goal is to create class instances)
> Factory Method Pattern定义了一个创建对象的接口，**但由子类决定要实例化哪一个类**，从而将对象创建与使用解耦。  
> 换句话说，你可以写一个方法专门用来“创建对象”，**但这个方法本身并不指定返回哪种具体类型的对象**，**而是交由子类决定返回哪个类的实例。**

> 在程序中，我们常常需要创建对象。  
> 最简单的方式就是直接使用 `new` 关键字：

```java
Car car = new SportsCar(); // 直接写死了具体类
```
> 但这样一来，你的代码**紧耦合于具体的类**，如果以后要用`FamilyCar`替换`SportsCar`，你就必须修改代码。  
> 使用Factory Method Pattern，可以这样做：

```java
Car car = factory.createCar(); // 不知道具体是哪个Car，由工厂来决定
```
> 这个`factory.createCar()`是一个**Factory Method**，它的实现可以在运行时由子类动态决定返回哪种具体的`Car`对象。


### Applicability
- Class can't anticipate the type of objects it must create
  > 类不能预先知道它必须创建的对象的类型  
  > 👉 比如日志系统，日志可能输出到文件、数据库或控制台，但创建时无法确定
- Class wants its subclasses to specify the type of objects it creates
  > 类希望将创建对象的职责交给子类  
  > 👉 父类提供创建接口，但真正的对象由子类决定
- Class needs control over the creation of its objects
  > 类希望对对象创建过程进行控制或扩展  
  > 👉 如果以后要做缓存、限流、统计等功能，集中控制创建过程是很有用的
### Structure
An example of factory method may include:
- **Creator (抽象创建者)**: provides interface for factory method
  > 声明工厂方法
- **ConcreteCreator (具体创建者)**: provides method for creating actual object
  > 实现工厂方法，返回具体产品实例
- **Product (产品接口)**: object created by the factory method
  > 抽象定义要创建的对象
- **ConcreteProduct (具体产品)**: 
  > 实现产品接口的具体类

### Sample code
```java
public classs ImageReaderFactory {
    public static ImageReader createImageReader(InputSteam is) {
        int imageType = getImageType(is);
        switch (imageType) {
            case ImageReaderFactory.GIF:
                return new GifReader(is);
            case ImageReaderFactory.JPEG:
                return new JpegReader(is);
            // ...
        }
    }
}
```
or provided by ChatGPT
```java
// Product
interface Car {
    void drive();
}

// Concrete Product
class SportsCar implements Car {
    public void drive() {
        System.out.println("Drive fast!");
    }
}
class FamilyCar implements Car {
    public void drive() {
        System.out.println("Drive slow!")
    }
}

// Creator
abstract class CarFactory {
    abstract Car createCar(); // Factory Method
}

// Concrete Creator
class SportsCarFactory extends CarFactory {
    Car createCar() {
        return new SportsCar();
    }
}
class FamilyCarFactory extends CarFactory {
    Car createCar() {
        return new FamilyCar();
    }
}

// when calling
CarFactory factory = new SportsCarFactory();
Car car = factory.createCar();
car.drive(); // 输出: Drive fast!
```

## Strategy Pattern

Below are properties of the strategy pattern:

### Intent
Allows for switching between different algorithms for accomplishing a task

> 定义一组算法，将每个算法封装起来，使它们可以互相替换，使得算法的变化不会影响使用算法的客户端代码。

也就是说，你可以把“怎么做事情”的逻辑封装成不同的类（策略），然后在运行时自由切换这些类的实现，而不需要修改核心的业务逻辑代码。

### Applicability
- Different variants of an algorithm
  > 有多个算法（策略）可供选择，且它们只是实现不同
- Many related classes differ only in their behavior
  > 多个类仅在行为上不同，可以提取出共用接口

需要在运行时选择算法，或频繁切换算法

### Structure
An example of strategy pattern may include:
- **Context**: interface to outside world
- **Algorithm (strategy)**: common interface for the different algorithms
- **Concrete strategy**: actual implementation of the algorithm

| 术语                   | 中文解释 | 说明                                                          |
| -------------------- | ---- | ----------------------------------------------------------- |
| **Context**          | 上下文  | 这个类对外暴露使用接口，内部依赖一个 `Strategy` 来完成具体任务。你可以理解成“客户端”或“控制流程的人”。 |
| **Strategy**         | 策略接口 | 这是一个抽象接口或父类，定义了所有算法共有的方法签名。比如“出行方式”的抽象接口。                   |
| **ConcreteStrategy** | 具体策略 | 实现了 `Strategy` 接口的类，表示某个具体的算法实现，比如“开车”或“坐公交”。               |

Context 中通常会有一个 `setStrategy()` 方法来动态设置当前要使用哪种策略，然后通过统一的接口调用 `strategy.execute()`

#### 💬 类比

上下班的“出行方式”就是一个策略：
- **Context** = 你（旅行者）
- **Strategy** = 出行方式接口
- **ConcreteStrategy** = 开车、坐公交、骑车等

通过更换策略，你可以灵活选择不同的出行方式而无需改变其它逻辑。

> ✅ 本质：把具体行为抽象为策略类，Context 中只依赖策略接口，**方便扩展和替换**。

#### 🚗 Strategy Pattern — Commute Example in Java
```java
// Strategy interface
public interface CommuteStrategy {
    void commute();
}

// Concrete Strategies
public class DriveStrategy implements CommuteStrategy {
    public void commute() {
        System.out.println("Driving to work.");
    }
}

public class BusStrategy implements CommuteStrategy {
    public void commute() {
        System.out.println("Taking the bus to work.");
    }
}

public class BikeStrategy implements CommuteStrategy {
    public void commute() {
        System.out.println("Riding a bike to work.");
    }
}

// Context
public class Commuter {
    private CommuteStrategy strategy;

    public void setStrategy(CommuteStrategy strategy) {
        this.strategy = strategy;
    }

    public void goToWork() {
        strategy.commute();
    }
}

// Usage example
Commuter me = new Commuter();
me.setStrategy(new DriveStrategy());
me.goToWork(); // Output: Driving to work.

me.setStrategy(new BikeStrategy());
me.goToWork(); // Output: Riding a bike to work.
```
这个例子中的 `Commuter` 是 `Context`，它依赖于 `CommuteStrategy` 接口，但并不关心使用的是哪种具体策略（Drive、Bus、Bike）。策略可以在运行时灵活替换，非常符合 Strategy Pattern 的设计思想。

See lecture for sample code example.

## Other Common Patterns

Other patterns include:

- **Visitor**: a way of separating an algorithm from an object structure on which it operates
- **Decorator**: a wrapper that adds functionality to a class (stackable)
- **Iterator**: access elements of a collection without knowing underlying representation
- **Observer**: notify dependents when object changes
- **Proxy**: surrogate controls access to an object

### 🧩 常见设计模式速查表（含中文解释）

---

#### **Visitor**
**Intent**: Separate an algorithm from the object structure it operates on.  
**Scenario**: You have a document with elements (text, image, table), and you want to add export or spell-checking logic.

> **中文解释**：将操作与数据结构本身分离，比如你有一个文档，里面有文字、图片、表格，你可以定义不同的访问者来处理不同功能（如导出、校对等），而不用改这些元素类的代码。

---

#### **Decorator**
**Intent**: Add behavior to objects dynamically without altering their class.  
**Scenario**: Wrap a `Coffee` object to add `Milk`, `Sugar`, or `WhippedCream`.

> **中文解释**：通过包装类给对象动态添加功能，比如给咖啡添加牛奶、糖、奶油等，每种配料都是一层装饰，不改动原始类。

---

#### **Iterator**
**Intent**: Traverse elements of a collection without exposing the underlying structure.  
**Scenario**: Iterate through a `List` of users without knowing if it's an array, tree, or linked list.

> **中文解释**：提供统一的方式来遍历集合元素，而不暴露其内部实现结构，比如你只关心“遍历用户”，不需要知道它是数组、链表还是其他结构。

---

#### **Observer**
**Intent**: Automatically notify dependents when an object’s state changes.  
**Scenario**: A `WeatherStation` updates the temperature, and multiple `Display` panels get notified to update themselves.

> **中文解释**：当一个对象状态变化时，自动通知所有依赖它的对象，比如气象站更新温度时，多个显示器一起刷新。

---

#### **Proxy**
**Intent**: Control access to another object (e.g., lazy loading, security, logging).  
**Scenario**: Use a `RemoteImageProxy` to delay loading a large image until it’s actually displayed.

> **中文解释**：代理对象控制对真实对象的访问，比如延迟加载大图，只有调用显示方法时才真正加载图像。



## Choosing A Pattern

There are several guidelines to choosing a design pattern:

1. Understand your design context
2. Examine the patterns catalog
3. Identify and study related patterns
4. Apply suitable pattern

However, there are pitfalls when selecting design patterns which may include (but are not limited to):

- Selecting wrong patterns
- Abusing patterns

We should always be careful to not rely too heavily on design patterns and ensure that whichever design pattern we select fits our problem.

## Negative Design Patterns

In addition to design patterns, there are also negative design patterns, i.e., how not to design manage, etc. These are also called _anti-patterns_ and _bad smells_ as discussed in Christoper Alexander's book: [A Pattern Language](https://en.wikipedia.org/wiki/A_Pattern_Language)

## Section Quizzes

### Choosing A Pattern Quiz

_Answer following questions_:

1. _Imagine that you have to write a class that can have one instance only. Which of the design pattern that we've discussed is most appropriate_? Factory
2. _Imagine that you have to write a class that can have one instance only. Using one of the design patterns that we discussed in this lesson, write the code of a class with only one method (except for possible constructors) that satisfy this requirement_. The code should be as follows:

```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}

    public static Singleton factory() {
        if (instance == null) {
           instance = new Singleton();
        }
        return instance;
    }
}
```
