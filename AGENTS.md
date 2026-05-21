# Spring Boot Demo - AGENTS.md

> AI 代码助手开发规范文档 - 本文档定义了项目的所有开发规范和最佳实践

## 目录

- [项目概述](#项目概述)
- [技术栈](#技术栈)
- [项目结构](#项目结构)
- [模块完成情况](#模块完成情况)
- [代码规范](#代码规范)
- [数据库设计规范](#数据库设计规范)
- [日志规范](#日志规范)
- [Git 提交规范](#git-提交规范)
- [测试规范](#测试规范)
- [开发指南](#开发指南)
- [常用命令参考](#常用命令参考)
- [常见问题排查](#常见问题排查)
- [AI 助手指南](#ai-助手指南)

---

## 项目概述

`spring-boot-demo` 是一个用于深度学习并实战 Spring Boot 的多模块 Maven 项目。

- **项目规模**：66 个集成 demo
- **完成情况**：已完成 55 个，待完成 11 个
- **Spring Boot 版本**：2.1.0.RELEASE
- **Java 版本**：JDK 1.8+
- **Maven 版本**：3.5+
- **包名**：com.xkcoding
- **作者**：Yangkai.Shen
- **开源协议**：MIT

---

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

---

## 项目结构

```
spring-boot-demo/
├── demo-helloworld/                  # HelloWorld 示例
├── demo-properties/                  # 配置读取
├── demo-actuator/                    # 监控端点
├── demo-admin/                       # 可视化监控（包含 client 和 server）
├── demo-logback/                     # 日志配置
├── demo-log-aop/                     # AOP 请求日志
├── demo-exception-handler/            # 统一异常处理
├── demo-template-freemarker/          # Freemarker 模板引擎
├── demo-template-thymeleaf/          # Thymeleaf 模板引擎
├── demo-template-beetl/               # Beetl 模板引擎
├── demo-template-enjoy/              # Enjoy 模板引擎
├── demo-orm-jdbctemplate/            # JdbcTemplate ORM
├── demo-orm-jpa/                     # JPA ORM
├── demo-orm-mybatis/                 # MyBatis ORM
├── demo-orm-mybatis-mapper-page/     # MyBatis 通用Mapper和分页
├── demo-orm-mybatis-plus/            # MyBatis-Plus ORM
├── demo-orm-beetlsql/                # BeetlSQL ORM
├── demo-cache-redis/                 # Redis 缓存
├── demo-cache-ehcache/               # Ehcache 缓存
├── demo-email/                       # 邮件服务
├── demo-task/                        # 基础定时任务
├── demo-task-quartz/                 # Quartz 动态定时任务
├── demo-task-xxl-job/                # XXL-JOB 分布式任务
├── demo-swagger/                     # Swagger API文档
├── demo-swagger-beauty/              # Swagger 美化版
├── demo-rbac-security/               # Spring Security 权限管理
├── demo-session/                     # Session 共享
├── demo-social/                      # 第三方登录
├── demo-zookeeper/                   # Zookeeper 分布式锁
├── demo-mq-rabbitmq/                # RabbitMQ 消息队列
├── demo-mq-kafka/                   # Kafka 消息队列
├── demo-websocket/                   # WebSocket 服务
├── demo-websocket-socketio/          # Socket.IO 聊天室
├── demo-ureport2/                    # UReport2 中国式报表
├── demo-async/                       # 异步任务
├── demo-dubbo/                       # Dubbo 微服务
├── demo-elasticsearch/              # Elasticsearch
├── demo-mongodb/                     # MongoDB
├── demo-neo4j/                       # Neo4j 图数据库
├── demo-docker/                      # Docker 容器化
├── demo-multi-datasource-jpa/         # JPA 多数据源
├── demo-multi-datasource-mybatis/    # MyBatis 多数据源
├── demo-sharding-jdbc/               # 分库分表
├── demo-codegen/                     # 代码生成器
├── demo-graylog/                     # GrayLog 日志收集
├── demo-ldap/                        # LDAP 集成
├── demo-dynamic-datasource/          # 动态数据源
├── demo-ratelimit-guava/             # Guava 单机限流
├── demo-ratelimit-redis/             # Redis 分布式限流
├── demo-https/                       # HTTPS 配置
├── demo-flyway/                      # Flyway 数据库迁移
├── demo-pay/                         # 支付集成
└── pom.xml                          # 父 POM
```

---

## 模块完成情况

### 已完成模块（55/66）

#### 入门示例
- `demo-helloworld` - Spring Boot 基础示例
- `demo-properties` - 配置文件读取

#### 监控与日志
- `demo-actuator` - 端点监控
- `demo-admin` - 可视化监控
- `demo-logback` - 日志配置
- `demo-log-aop` - AOP 日志记录
- `demo-graylog` - 日志收集

#### 模板引擎
- `demo-template-freemarker` - Freemarker 模板
- `demo-template-thymeleaf` - Thymeleaf 模板
- `demo-template-beetl` - Beetl 模板
- `demo-template-enjoy` - Enjoy 模板

#### ORM 框架
- `demo-orm-jdbctemplate` - JdbcTemplate 操作
- `demo-orm-jpa` - Spring Data JPA
- `demo-orm-mybatis` - 原生 MyBatis
- `demo-orm-mybatis-mapper-page` - MyBatis 通用Mapper和分页
- `demo-orm-mybatis-plus` - MyBatis-Plus 增强
- `demo-orm-beetlsql` - BeetlSQL

#### 缓存
- `demo-cache-redis` - Redis 缓存
- `demo-cache-ehcache` - Ehcache 缓存

#### 消息队列
- `demo-mq-rabbitmq` - RabbitMQ 消息队列
- `demo-mq-kafka` - Kafka 消息队列

#### 定时任务
- `demo-task` - 基础定时任务
- `demo-task-quartz` - Quartz 动态管理
- `demo-task-xxl-job` - XXL-JOB 分布式调度

#### 安全
- `demo-rbac-security` - Spring Security 权限管理
- `demo-session` - Session 共享
- `demo-social` - 第三方登录（JustAuth）

#### 其他功能
- `demo-email` - 邮件服务
- `demo-upload` - 文件上传（七牛云）
- `demo-swagger` - Swagger API文档
- `demo-swagger-beauty` - Swagger 美化版
- `demo-zookeeper` - Zookeeper 分布式锁
- `demo-websocket` - WebSocket 服务端推送
- `demo-websocket-socketio` - Socket.IO 聊天室
- `demo-ureport2` - UReport2 中国式报表
- `demo-async` - 异步任务
- `demo-dubbo` - Dubbo 微服务
- `demo-elasticsearch` - ElasticSearch
- `demo-elasticsearch-rest-high-level-client` - ES 7.x 高级客户端
- `demo-mongodb` - MongoDB 文档数据库
- `demo-neo4j` - Neo4j 图数据库
- `demo-docker` - Docker 容器化
- `demo-multi-datasource-jpa` - JPA 多数据源
- `demo-multi-datasource-mybatis` - MyBatis 多数据源
- `demo-sharding-jdbc` - 分库分表
- `demo-codegen` - Velocity 代码生成器
- `demo-ldap` - LDAP 目录服务
- `demo-dynamic-datasource` - 动态数据源
- `demo-ratelimit-guava` - Guava 单机限流
- `demo-ratelimit-redis` - Redis 分布式限流
- `demo-https` - HTTPS 配置
- `demo-flyway` - Flyway 数据库迁移
- `demo-pay` - 支付集成

### 待完成模块（11/66）

| 模块名称 | 功能描述 | 依赖技术 | 难度 |
|---------|---------|---------|------|
| `demo-rbac-shiro` | Shiro 权限管理 | Shiro, Spring Security | ⭐⭐⭐ |
| `demo-oauth` | OAuth2 认证服务器 | OAuth2, Spring Security | ⭐⭐⭐⭐ |
| `demo-mq-rocketmq` | RocketMQ 消息队列 | RocketMQ | ⭐⭐⭐ |
| `demo-uflo` | 流程控制引擎 | uflo, Activiti | ⭐⭐⭐⭐ |
| `demo-urule` | 规则引擎 | urule, Drools | ⭐⭐⭐⭐ |
| `demo-activiti` | 流程引擎 | Activiti 7 | ⭐⭐⭐⭐ |
| `demo-tio` | 网络编程框架 | t-io | ⭐⭐⭐ |
| `demo-grpc` | gRPC 微服务 | gRPC, Protobuf | ⭐⭐⭐⭐ |
| `demo-sso` | 单点登录 | CAS, OAuth2 | ⭐⭐⭐⭐ |
| `demo-springbatch` | 批处理 | Spring Batch | ⭐⭐⭐ |
| `demo-security-justauth` | JustAuth + Security | JustAuth, Spring Security | ⭐⭐⭐ |

---

## 代码规范

### 包结构规范
每个 demo 模块遵循以下包结构：

```
com.xkcoding.{module}/
├── config/              # 配置类
├── controller/          # 控制器层
├── service/            # 服务层
│   └── impl/          # 服务实现
├── repository/        # 数据访问层（Spring Data）
├── mapper/            # MyBatis Mapper 接口
├── entity/            # 实体类
├── model/             # 数据模型
├── dto/               # 数据传输对象
├── vo/                # 视图对象
├── request/           # 请求对象
├── response/          # 响应对象
├── constant/          # 常量
├── enums/             # 枚举
├── exception/         # 异常定义
├── handler/           # 处理器
├── aspect/            # 切面
├── annotation/        # 自定义注解
├── util/              # 工具类
└── Application.java   # 启动类
```

### 命名规范

#### 类名：UpperCamelCase（帕斯卡命名）
- 实体类：`User.java`
- 控制器：`UserController.java`
- 服务接口：`UserService.java`
- 服务实现：`UserServiceImpl.java`
- Mapper 接口：`UserMapper.java`
- Mapper XML：`UserMapper.xml`
- 配置类：`RedisConfig.java`

#### 方法名：lowerCamelCase（驼峰命名）
- 查询方法：`getUserById()`, `findUserList()`
- 保存方法：`saveUser()`, `createUser()`
- 更新方法：`updateUser()`
- 删除方法：`deleteUser()`, `removeUser()`
- 批量操作：`batchSaveUsers()`, `batchDeleteUsers()`

#### 常量：UPPER_SNAKE_CASE（全大写下划线分隔）
```java
public static final int MAX_RETRY_COUNT = 3;
public static final String DEFAULT_PAGE_SIZE = "20";
private static final Logger log = LoggerFactory.getLogger(ClassName.class);
```

#### 变量命名
```java
// 普通变量
String userName;
Integer userId;
List<User> userList;
Map<String, Object> dataMap;

// 成员变量（带 m 前缀，可选）
private String mUserName;
private Integer mUserId;
```

### 配置文件规范

#### 主配置文件：application.yml
```yaml
spring:
  application:
    name: demo-xxx
  profiles:
    active: dev
```

#### 环境配置
- `application.yml` - 主配置
- `application-dev.yml` - 开发环境
- `application-test.yml` - 测试环境
- `application-prod.yml` - 生产环境

#### MyBatis 配置
- Mapper XML 位置：`src/main/resources/mappers/`
- 命名规范：`XxxMapper.xml`

### 注解使用规范
```java
@RestController          // REST 控制器
@RequestMapping("/api")  // 请求映射
@Service                 // 服务层组件
@Repository              // 数据访问层组件
@Component               // 通用组件
@Configuration           // 配置类
@Bean                    // 声明式创建 Bean
@Slf4j                  // 日志注解（Lombok）
@Data                    // Getter/Setter（Lombok）
```

### RESTful API 设计规范

#### URL 设计
```
GET    /users           # 查询用户列表
GET    /users/{id}      # 查询单个用户
POST   /users           # 创建用户
PUT    /users/{id}      # 更新用户
DELETE /users/{id}      # 删除用户
```

#### 请求参数规范
```java
// 路径参数
@PathVariable Long id

// 查询参数
@RequestParam String name

// 请求体
@RequestBody UserRequest request
```

#### 响应格式规范
```java
{
  "code": 200,
  "message": "success",
  "data": { ... }
}
```

### Lombok 使用规范
```java
@Data                  // Getter, Setter, toString, equals, hashCode
@NoArgsConstructor     // 无参构造器
@AllArgsConstructor    // 全参构造器
@Builder               // 构建者模式
@Slf4j                 // 日志对象（private static final Logger log）
```

---

## 数据库设计规范

### 表命名规范
- 使用小写字母和下划线
- 格式：`模块_表名`
- 示例：`orm_user`, `sys_user_role`, `log_login_record`

### 字段命名规范
- 使用小写字母和下划线
- 格式：`word_word`
- 示例：`user_name`, `create_time`, `last_login_time`

### 主键规范
```sql
-- 推荐使用自增主键
id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY

-- 或使用 UUID
id VARCHAR(32) NOT NULL PRIMARY KEY
```

### 常用字段规范
```sql
-- 创建时间
create_time DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间'

-- 更新时间
update_time DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间'

-- 逻辑删除
deleted TINYINT(1) NOT NULL DEFAULT 0 COMMENT '逻辑删除，0：未删除，1：已删除'

-- 状态
status TINYINT(2) NOT NULL DEFAULT 1 COMMENT '状态，0：禁用，1：启用'

-- 创建人
create_by VARCHAR(32) COMMENT '创建人'

-- 更新人
update_by VARCHAR(32) COMMENT '更新人'
```

### 字段类型选择
- 字符串：`VARCHAR`（可变得长字符串）或 `TEXT`（长文本）
- 数字：`INT`, `BIGINT`, `DECIMAL`
- 日期：`DATETIME` 或 `TIMESTAMP`
- 布尔：`TINYINT(1)` 或 `BOOLEAN`

### 索引规范
```sql
-- 普通索引
INDEX idx_user_name (user_name)

-- 唯一索引
UNIQUE INDEX uk_user_name (user_name)

-- 联合索引
INDEX idx_status_time (status, create_time)
```

### SQL 示例
```sql
CREATE TABLE `orm_user` (
  `id` INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT '主键',
  `name` VARCHAR(32) NOT NULL UNIQUE COMMENT '用户名',
  `password` VARCHAR(32) NOT NULL COMMENT '加密后的密码',
  `salt` VARCHAR(32) NOT NULL COMMENT '加密使用的盐',
  `email` VARCHAR(32) NOT NULL UNIQUE COMMENT '邮箱',
  `phone_number` VARCHAR(15) NOT NULL UNIQUE COMMENT '手机号码',
  `status` INT(2) NOT NULL DEFAULT 1 COMMENT '状态，0：禁用，1：启用',
  `create_time` DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `last_login_time` DATETIME DEFAULT NULL COMMENT '上次登录时间',
  `last_update_time` DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='用户表';
```

---

## 日志规范

### 日志级别使用
```java
log.debug("调试信息，用于开发环境");
log.info("一般信息，记录业务操作");
log.warn("警告信息，潜在问题");
log.error("错误信息，异常情况");
```

### 日志输出规范
```java
// ✅ 正确：使用占位符
log.info("查询用户【id】= {}", id);
log.info("保存用户【user】= {}", user);

// ❌ 错误：字符串拼接
log.info("查询用户【id】= " + id);
```

### 敏感信息处理
```java
// ✅ 正确：脱敏处理
log.info("用户手机号：{}", DesensitizeUtil.mobile(phone));

// ❌ 错误：直接打印敏感信息
log.info("用户手机号：{}", phone);
```

### 统一日志格式
```
时间 | 级别 | 线程 | 类名 | 消息
2024-01-01 10:00:00 | INFO | http-nio-8080-exec-1 | UserService | 查询用户成功
```

---

## Git 提交规范

### 提交信息格式
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type 类型
- `feat`: 新功能
- `fix`: Bug 修复
- `docs`: 文档更新
- `style`: 代码格式（不影响功能）
- `refactor`: 重构
- `perf`: 性能优化
- `test`: 测试
- `chore`: 构建或辅助工具

### 示例
```
feat(demo-orm-mybatis): 添加用户查询功能

- 添加 UserMapper 接口
- 添加 UserMapper.xml
- 添加单元测试

Closes #123
```

### 分支命名
- 功能分支：`feature/demo-xxx`
- 修复分支：`fix/bug-xxx`
- 发布分支：`release/v1.0.0`

---

## 测试规范

### 测试类命名
```java
// 单元测试
XxxServiceTest.java
XxxMapperTest.java

// 集成测试
XxxIntegrationTest.java
```

### 测试方法命名
```java
@Test
public void testSaveUser_Success() { }

@Test
public void testGetUserById_NotFound() { }

@Test(expected = BusinessException.class)
public void testSaveUser_ValidationError() { }
```

### 测试覆盖率
- 核心业务代码覆盖率 ≥ 70%
- 公共工具类覆盖率 ≥ 80%

---

## 开发指南

### 环境要求
- JDK 1.8+
- Maven 3.5+
- MySQL 5.7+（推荐 8.0）
- IntelliJ IDEA（推荐安装 Lombok 插件）

### 开发环境搭建
1. **克隆项目**
   ```bash
   git clone https://github.com/xkcoding/spring-boot-demo.git
   cd spring-boot-demo
   ```

2. **导入 Maven 项目**
   - 使用 IDEA 打开项目根目录
   - 在 Maven Projects 面板导入 `pom.xml`

3. **配置数据库**
   - 创建数据库：`CREATE DATABASE spring_boot_demo;`
   - 修改 `application.yml` 中的数据库配置

4. **运行模块**
   - 找到目标模块的 `Application.java`
   - 右键运行或使用 Debug 模式

### 注意事项
- 每个 demo 均有详细的 README 文档，运行前请先阅读
- 部分 demo 需要提前初始化数据库
- 数据库脚本通常位于：
  - `src/main/resources/db/`
  - `src/main/resources/sql/`
  - 根目录的 `sql/` 或 `db/` 文件夹

---

## 常用命令参考

### Maven 命令
```bash
# 清理并编译
mvn clean compile

# 打包（跳过测试）
mvn clean package -DskipTests

# 运行模块
mvn clean package -DskipTests
java -jar target/demo-xxx.jar

# 查看依赖树
mvn dependency:tree

# 跳过测试
mvn clean install -DskipTests
```

### 数据库命令
```sql
-- 导入 SQL 文件
source /path/to/schema.sql
source /path/to/data.sql

-- 查看表结构
DESC table_name;

-- 查看索引
SHOW INDEX FROM table_name;
```

### Docker 命令
```bash
# 构建镜像
docker build -t spring-boot-demo:latest .

# 运行容器
docker run -d -p 8080:8080 spring-boot-demo:latest

# 查看日志
docker logs -f container_id
```

---

## 常见问题排查

### 依赖问题
- **依赖冲突**：使用 `mvn dependency:tree` 查看依赖树，定位冲突
- **版本不兼容**：检查 Spring Boot 版本与依赖版本的兼容性

### 数据库问题
- **连接失败**：检查数据库 URL、用户名、密码
- **表不存在**：确认数据库初始化脚本已执行
- **字符集问题**：检查数据库和表的字符集配置

### 启动问题
- **端口占用**：`java.net.BindException: Address already in use`
  - 修改 `application.yml` 中的端口号
  - 或停止占用端口的进程
- **配置缺失**：检查必要的配置项是否完整

### 运行时问题
- **NPE 空指针**：使用日志追踪定位空值
- **事务失效**：检查是否在同一个类中调用方法
- **缓存问题**：确认缓存配置正确，清除缓存测试

### 日志查看
```bash
# 查看实时日志
tail -f logs/spring.log

# 查看错误日志
grep -i error logs/spring.log

# 查看最近 100 行日志
tail -n 100 logs/spring.log
```

---

## AI 助手指南

### 代码分析
1. 查看 `pom.xml` 了解依赖配置
2. 查看 `README.md` 了解模块功能
3. 查看 `application.yml` 了解配置方式
4. 分析现有代码结构，遵循相同的模式

### 代码生成
1. 参考现有模块的代码结构
2. 遵循包结构规范
3. 使用统一的命名风格
4. 保持代码风格一致性
5. 添加必要的注释和文档

### 问题排查
1. 检查 Spring Boot 版本兼容性
2. 检查数据库连接配置
3. 检查依赖版本冲突
4. 查看日志输出定位问题
5. 使用断点调试定位问题

### 代码审查要点
1. **代码风格**：是否符合项目规范
2. **命名规范**：变量、方法、类名是否规范
3. **异常处理**：是否正确处理异常
4. **安全检查**：是否有安全隐患
5. **性能考虑**：是否有性能问题

### 性能优化建议
1. 使用懒加载减少初始化时间
2. 使用缓存减少数据库查询
3. 使用索引优化查询性能
4. 使用批量操作减少数据库交互
5. 使用异步处理提高响应速度

### 安全性检查清单
1. **SQL 注入**：使用参数化查询
2. **XSS**：对输出进行转义
3. **CSRF**：使用 Token 验证
4. **敏感信息**：加密存储敏感数据
5. **权限控制**：验证用户权限

### 最佳实践
1. 使用 Lombok 减少样板代码
2. 使用 `@Slf4j` 注解简化日志
3. 使用统一响应格式（`Result`）
4. 使用全局异常处理器
5. 使用事务注解管理事务
6. 使用参数校验注解（`@Valid`）
7. 使用 Swagger 生成 API 文档

---

> 📝 **文档更新记录**
> - 2024年 - 初始版本
> - 增强内容：数据库规范、日志规范、Git 规范、测试规范
> - 补充未完成模块列表和详细说明
> - 添加常用命令参考和常见问题排查
> - 增强 AI 助手指南
