# Spring Boot Demo - AGENTS.md

## 项目概述

`spring-boot-demo` 是一个用于深度学习并实战 Spring Boot 的多模块 Maven 项目，目前包含 **66** 个集成 demo，已完成 **55** 个。

- **Spring Boot 版本**：2.1.0.RELEASE
- **Java 版本**：JDK 1.8+
- **Maven 版本**：3.5+
- **包名**：com.xkcoding

## 技术栈

### 核心框架
- Spring Boot 2.1.0.RELEASE
- Spring Framework
- Spring Data 系列

### 数据库与 ORM
- MySQL 8.0.21
- JdbcTemplate
- Spring Data JPA
- MyBatis / MyBatis-Plus
- BeetlSQL
- Hibernate

### 缓存
- Redis
- Ehcache

### 消息队列
- RabbitMQ
- Kafka
- RocketMQ（待完成）

### 定时任务
- Spring Task
- Quartz
- XXL-JOB

### 安全
- Spring Security
- Shiro（待完成）
- OAuth2（待完成）

### 其他中间件
- Zookeeper（分布式锁）
- MongoDB（文档数据库）
- Neo4j（图数据库）
- Elasticsearch（搜索引擎）
- LDAP（目录服务）
- Docker（容器化）

### 工具库
- Hutool 5.4.5
- Guava 29.0-jre
- UserAgentUtils 1.20

## 项目结构

```
spring-boot-demo/
├── demo-helloworld/              # HelloWorld 示例
├── demo-properties/              # 配置读取
├── demo-actuator/                # 监控端点
├── demo-admin/                   # 可视化监控（包含 client 和 server）
├── demo-logback/                  # 日志配置
├── demo-log-aop/                  # AOP 请求日志
├── demo-exception-handler/        # 统一异常处理
├── demo-template-*/               # 模板引擎（Freemarker/Thymeleaf/Beetl/Enjoy）
├── demo-orm-*/                    # ORM 框架集成
├── demo-cache-*/                  # 缓存集成
├── demo-email/                    # 邮件服务
├── demo-task*/                    # 定时任务
├── demo-swagger*/                 # API 文档
├── demo-rbac-*/                   # 权限管理
├── demo-session/                  # Session 共享
├── demo-social/                   # 第三方登录
├── demo-zookeeper/                # Zookeeper 分布式锁
├── demo-mq-*/                     # 消息队列
├── demo-websocket*/               # WebSocket
├── demo-elasticsearch*/           # Elasticsearch
├── demo-dubbo/                    # Dubbo 微服务
├── demo-mongodb/                  # MongoDB
├── demo-neo4j/                    # Neo4j 图数据库
├── demo-docker/                   # Docker 容器化
├── demo-multi-datasource-*/       # 多数据源
├── demo-sharding-jdbc/            # 分库分表
├── demo-codegen/                  # 代码生成器
├── demo-graylog/                  # 日志收集
├── demo-ldap/                    # LDAP 集成
├── demo-dynamic-datasource/        # 动态数据源
├── demo-ratelimit-*/              # 限流
├── demo-https/                    # HTTPS 配置
├── demo-flyway/                   # 数据库迁移
├── demo-pay/                      # 支付集成
└── pom.xml                        # 父 POM
```

## 代码规范

### 包结构规范
每个 demo 模块遵循以下包结构：

```
com.xkcoding.{module}/
├── config/          # 配置类
├── controller/       # 控制器层
├── service/         # 服务层
│   └── impl/        # 服务实现
├── repository/      # 数据访问层（Spring Data）
├── mapper/         # MyBatis Mapper
├── entity/         # 实体类
├── model/          # 数据模型
├── dto/            # 数据传输对象
├── vo/             # 视图对象
├── constant/       # 常量
├── enums/          # 枚举
├── exception/      # 异常
├── handler/        # 处理器
├── aspect/         # 切面
├── annotation/      # 自定义注解
├── util/           # 工具类
└── Application.java # 启动类
```

### 命名规范
- **类名**：UpperCamelCase 风格
  - 实体类：`User.java`
  - 控制器：`UserController.java`
  - 服务接口：`UserService.java`
  - 服务实现：`UserServiceImpl.java`
  - Mapper：`UserMapper.java`

- **方法名**：lowerCamelCase 风格
  - 查询方法：`getUserById()`
  - 保存方法：`saveUser()`
  - 更新方法：`updateUser()`
  - 删除方法：`deleteUser()`

- **常量**：UPPER_SNAKE_CASE 风格
  - `MAX_RETRY_COUNT`
  - `DEFAULT_PAGE_SIZE`

### 配置文件
- **application.yml**：主配置文件
- **application-dev.yml**：开发环境配置
- **application-prod.yml**：生产环境配置

### 注解使用
- `@RestController` 或 `@Controller` + `@ResponseBody`
- `@Service` 用于服务层
- `@Repository` 用于数据访问层
- `@Component` 用于通用组件
- `@Configuration` 用于配置类
- `@Bean` 用于声明式创建 Bean

### RESTful API 设计
- `GET /users` - 查询用户列表
- `GET /users/{id}` - 查询单个用户
- `POST /users` - 创建用户
- `PUT /users/{id}` - 更新用户
- `DELETE /users/{id}` - 删除用户

## 开发指南

### 环境要求
- JDK 1.8+
- Maven 3.5+
- MySQL 5.7+
- IntelliJ IDEA（推荐安装 Lombok 插件）

### 运行方式
1. 克隆项目：`git clone https://github.com/xkcoding/spring-boot-demo.git`
2. 使用 IDEA 打开项目
3. 在 Maven Projects 面板导入根目录的 `pom.xml`
4. 找到各模块的 `Application` 类运行

### 注意事项
- 每个 demo 均有详细的 README 文档，运行前请先阅读
- 部分 demo 需要提前初始化数据库
- 数据库脚本通常位于各模块的 `sql/` 或 `db/` 目录下

## 模块分类

### 入门示例
- `demo-helloworld` - Spring Boot 基础示例
- `demo-properties` - 配置文件读取

### 监控与日志
- `demo-actuator` - 端点监控
- `demo-admin` - 可视化监控
- `demo-logback` - 日志配置
- `demo-log-aop` - AOP 日志记录
- `demo-graylog` - 日志收集

### 模板引擎
- `demo-template-freemarker`
- `demo-template-thymeleaf`
- `demo-template-beetl`
- `demo-template-enjoy`

### ORM 框架
- `demo-orm-jdbctemplate`
- `demo-orm-jpa`
- `demo-orm-mybatis`
- `demo-orm-mybatis-mapper-page`
- `demo-orm-mybatis-plus`
- `demo-orm-beetlsql`

### 缓存
- `demo-cache-redis`
- `demo-cache-ehcache`

### 消息队列
- `demo-mq-rabbitmq`
- `demo-mq-kafka`
- `demo-mq-rocketmq`（待完成）

### 定时任务
- `demo-task` - 基础定时任务
- `demo-task-quartz` - Quartz 动态管理
- `demo-task-xxl-job` - 分布式任务调度

### 安全
- `demo-rbac-security` - Spring Security 权限管理
- `demo-rbac-shiro`（待完成）
- `demo-session` - Session 共享
- `demo-oauth`（待完成）

### 其他
- `demo-email` - 邮件服务
- `demo-upload` - 文件上传
- `demo-swagger*` - API 文档
- `demo-social` - 第三方登录
- `demo-zookeeper` - 分布式锁
- `demo-websocket*` - WebSocket
- `demo-dubbo` - 微服务
- `demo-elasticsearch*` - 搜索引擎
- `demo-mongodb` - 文档数据库
- `demo-neo4j` - 图数据库
- `demo-docker` - 容器化
- `demo-multi-datasource-*` - 多数据源
- `demo-sharding-jdbc` - 分库分表
- `demo-codegen` - 代码生成
- `demo-ldap` - LDAP 集成
- `demo-dynamic-datasource` - 动态数据源
- `demo-ratelimit-*` - 限流
- `demo-https` - HTTPS 配置
- `demo-flyway` - 数据库迁移

## AI 助手指南

### 代码分析
- 查看 `pom.xml` 了解依赖配置
- 查看 `README.md` 了解模块功能
- 查看 `application.yml` 了解配置方式

### 代码生成
- 参考现有模块的代码结构
- 遵循包结构规范
- 使用统一的命名风格

### 问题排查
- 检查 Spring Boot 版本兼容性
- 检查数据库连接配置
- 检查依赖版本冲突
- 查看日志输出定位问题

### 最佳实践
- 使用 Lombok 减少样板代码
- 使用 `@Slf4j` 注解简化日志
- 使用 `Result` 或统一响应格式
- 使用全局异常处理器统一处理异常
