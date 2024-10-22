# OpenFeign 笔记

## 微服务之间的调用方式

- HTTP

  在 SpringCloud 中, 默认使⽤ HTTP 来进⾏微服务的通信, 最常⽤的实现形式有两种：

  - RestTemplate
  - OpenFeign

- RPC（Remote Procedure Call，远程过程调⽤）

  RPC 协议是一种专门为服务间远程调用而设计的一种通用协议。 该协议基于其它已有的传输协议，规定通信方式为 C/S 架构，在代码开发过程中会屏蔽掉底层通信细节， 让开发者像调用本地方法一样，调用远程服务。RPC可以基于TCP、HTTP、WebStock等作为基础传输协议。RPC协议常见的实现有：

  - Dubbo
  - Thrift
  - gRPC

## 使用步骤

1. 添加 maven 依赖

   ```xml
   <!-- 添加OpenFeign依赖 -->
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-starter-openfeign</artifactId>
   </dependency>
   ```

2. 在启动类上添加注解 `@EnableFeignClients`

   Spring Boot 将会扫描指定的包路径下的 Feign 客户端接口，并自动创建代理对象。这些代理对象可以直接调用远程服务的 API，而无需手动编写 HTTP 请求代码。

3. 



## 参考网站

[腾讯云：必知必会 - 一文搞定理解RPC](https://cloud.tencent.com/developer/article/1506792)

[脚本之家：SpringCloud整合OpenFeign实现微服务间的通信](https://www.jb51.net/program/322568m1c.htm)