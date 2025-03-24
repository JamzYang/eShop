
## 各模块详细说明

### API 服务层
- **Basket.API**: 购物车微服务，处理购物车的增删改查
  - `Extensions/`: 扩展方法和中间件配置
  - `Grpc/`: gRPC 服务实现
  - `IntegrationEvents/`: 集成事件定义和处理
  - `Model/`: 购物车相关的数据模型
  - `Proto/`: Protocol Buffers 定义文件
  - `Repositories/`: 购物车数据访问层实现

- **Catalog.API**: 商品目录服务，管理商品信息、分类、价格等
  - `Apis/`: API 端点实现
  - `Infrastructure/`: 基础设施代码
  - `IntegrationEvents/`: 商品相关的集成事件
  - `Model/`: 商品目录数据模型
  - `Services/`: 业务服务实现
  - `Setup/`: 服务初始化和配置

- **Identity.API**: 基于 IdentityServer 的身份认证服务
  - `Configuration/`: IdentityServer 配置
  - `Data/`: 身份认证相关的数据访问
  - `Models/`: 身份认证数据模型
  - `Services/`: 认证相关服务
  - `Views/`: 登录和账户管理界面

- **Mobile.Bff.Shopping**: 移动端专用的 BFF 服务
  - `Extensions/`: 服务扩展方法
  - `Properties/`: 项目属性配置

- **Ordering.API**: 订单管理 API 服务
  - `Apis/`: API 端点实现
  - `Application/`: 应用层服务
  - `Infrastructure/`: 基础设施实现

- **Webhooks.API**: Webhook 服务，处理异步通知

### 领域层
- **Ordering.API**: 订单管理 API 服务
  - `Apis/`: API 端点实现
    - `OrderServices.cs`: 订单服务实现
    - `OrdersApi.cs`: 订单 API 端点定义
  - `Application/`: 应用层服务
    - `Behaviors/`: 行为管道实现（日志、事务、验证）
    - `Commands/`: CQRS 命令实现（创建、取消、发货等）
    - `DomainEventHandlers/`: 领域事件处理器
    - `IntegrationEvents/`: 集成事件定义和处理
    - `Models/`: 应用层数据模型
    - `Queries/`: CQRS 查询实现
    - `Validations/`: 命令验证器
  - `Extensions/`: 扩展方法
  - `Infrastructure/`: API 层基础设施

- **Ordering.Domain**: 订单领域层
  - `AggregatesModel/`: 聚合根模型
    - `BuyerAggregate/`: 买家聚合根
      - `Buyer.cs`: 买家实体
      - `CardType.cs`: 支付卡类型
      - `PaymentMethod.cs`: 支付方式
      - `IBuyerRepository.cs`: 买家仓储接口
    - `OrderAggregate/`: 订单聚合根
      - `Order.cs`: 订单实体
      - `OrderItem.cs`: 订单项
      - `OrderStatus.cs`: 订单状态
      - `Address.cs`: 地址值对象
      - `IOrderRepository.cs`: 订单仓储接口
  - `Events/`: 领域事件定义
  - `Exceptions/`: 领域异常
  - `SeedWork/`: DDD 基础构建块

- **Ordering.Infrastructure**: 基础设施层
  - `EntityConfigurations/`: 实体配置
    - 定义实体与数据库表的映射关系
    - 配置实体间的关系和约束
  - `Idempotency/`: 幂等性处理
    - `ClientRequest.cs`: 客户端请求记录
    - `RequestManager.cs`: 请求管理器
  - `Migrations/`: 数据库迁移脚本
  - `Repositories/`: 仓储实现
    - `BuyerRepository.cs`: 买家仓储实现
    - `OrderRepository.cs`: 订单仓储实现
  - `OrderingContext.cs`: EF Core 数据库上下文

### 客户端应用
- **ClientApp**: 主要客户端应用程序
  - `Animations/`: 自定义动画效果
  - `Controls/`: 自定义UI控件
  - `Effects/`: 视觉效果实现
  - `Models/`: 数据模型定义
  - `Services/`: 业务服务实现
  - `ViewModels/`: MVVM模式的视图模型
  - `Views/`: 用户界面实现

- **HybridApp**: 混合开发应用
  - `Components/`: 混合应用组件
  - `Services/`: 混合应用服务
  - `wwwroot/`: Web资源文件

- **WebApp**: Web 应用程序
  - `Components/`: Web组件实现
  - `Extensions/`: 扩展方法
  - `Services/`: Web应用服务

- **WebAppComponents**: 可复用的 Web 组件库
  - `Catalog/`: 商品目录相关组件
  - `Item/`: 商品项组件
  - `Services/`: 组件服务

### 事件总线
- **EventBus**: 事件总线的抽象层，定义接口和基类
  - `Abstractions/`: 事件总线接口定义
  - `Events/`: 基础事件类型
  - `Extensions/`: 事件总线扩展方法

- **EventBusRabbitMQ**: 基于 RabbitMQ 的消息队列实现
  - `EventBusOptions.cs`: RabbitMQ配置选项
  - `RabbitMQEventBus.cs`: RabbitMQ事件总线实现
  - `RabbitMQTelemetry.cs`: 遥测功能实现

- **IntegrationEventLogEF**: 使用 Entity Framework 实现的事件日志
  - `Services/`: 事件日志服务
  - `Utilities/`: 工具类
  - `EventStateEnum.cs`: 事件状态枚举
  - `IntegrationEventLogEntry.cs`: 事件日志实体

### 处理器服务
- **OrderProcessor**: 处理订单相关的异步任务
  - `Events/`: 订单事件定义
  - `Extensions/`: 扩展方法
  - `Services/`: 订单处理服务

- **PaymentProcessor**: 处理支付相关的业务逻辑
  - `IntegrationEvents/`: 支付相关事件
  - `PaymentOptions.cs`: 支付配置选项

### Webhook 相关
- **WebhookClient**: Webhook 客户端实现
  - `Components/`: Webhook UI组件
  - `Endpoints/`: 客户端端点
  - `Extensions/`: 扩展方法

- **Webhooks.API**: Webhook 服务端实现

### 基础设施
- **eShop.AppHost**: 应用程序宿主，管理服务配置和启动

- **eShop.ServiceDefaults**: 服务默认配置

- **Shared**: 共享的工具类和扩展方法
  - `ActivityExtensions.cs`: 活动追踪扩展
  - `MigrateDbContextExtensions.cs`: 数据库迁移扩展

## 架构特点

1. **微服务架构**：
   - 服务独立部署
   - 服务间通过事件总线通信
   - 每个服务有自己的数据存储

2. **领域驱动设计**：
   - 清晰的领域边界
   - 聚合根模式
   - 领域事件

3. **事件驱动架构**：
   - 异步消息通信
   - 事件溯源
   - 集成事件日志

4. **BFF 模式**：
   - 移动端专用 API 层
   - 优化客户端通信

5. **多客户端支持**：
   - Web 应用
   - 移动应用
   - 混合应用