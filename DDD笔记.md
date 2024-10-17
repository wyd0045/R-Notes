# DDD 笔记

以 [产品代码都给你看了，可别再说不会DDD](https://docs.mryqr.com/ddd-introduction/) 为主线，仅做适当的补充。

## 1. DDD 入门

- SaaS

  即软件即服务（Software as a Service），是用户能够通过互联网连接使用的基于云的应用程序。它不需要用户将软件产品安装在自己的电脑或服务器上，而是通过 Web 浏览器连接到该应用。

- DDD 是面向对象进阶。

## 2. DDD 概念大白话

- 成员已创建事件类 MemberCreatedEvent

  ```java
  @Getter
  @TypeAlias("MEMBER_CREATED_EVENT")
  @NoArgsConstructor(access = PRIVATE)
  public class MemberCreatedEvent extends DomainEvent {
      private String memberId;
  
      public MemberCreatedEvent(String memberId, User user) {
          super(MEMBER_CREATED, user); // 调用超类的构造方法
          this.memberId = memberId;
      }
  
  }
  ```

​		`super()` 方法是在调用超类的构造方法。

​		Java 中构造函数的继承：

​		子类的构造过程中必须调用父类的构造方法 子类可在自己的构造方法中使用super（）来调用父类的构造方法 使用this来调用本类的另外的构造方法 
如果调用super必须写在子类构造方法的第一行 
3.如果子类的构造方法中没有显示的调用父类的构造方法，则系统默认的调用父类的无参的构造方法。 
4.如果子类的构造方法中既没有显示调用父类的构造方法，而父类中又没有无参的构造方法，则编译出错。 