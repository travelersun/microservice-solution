# microservice-solution

**微服务开发平台解决方案**


本项目的有些组件由几个著名的开源项目改造而来，基础中心的部分数据模型参考了Oracle E-Business Suite 的数据模型设计


## 组成本项目的主要组件

- [service-eraker](https://github.com/travelersun/service-eraker "service-eraker")
spring cloud eureka 注册中心 https://github.com/travelersun/service-eraker

- [gateway](https://github.com/travelersun/gateway "gateway")
spring cloud gateway 微服务网关 https://github.com/travelersun/gateway
集成Spring session 分布式会话管理和 Spring Cloud Security Oauth2 验证和授权,代理外部对uaa服务请求
支持session 和 oauth2 jwt 

- [uaa](https://github.com/travelersun/tianzhu-identity-uaa "uaa")
Spring Cloud Security Oauth2 授权服务中心https://github.com/travelersun/tianzhu-identity-uaa
改造自[https://github.com/cloudfoundry/uaa](https://github.com/cloudfoundry/uaa "https://github.com/cloudfoundry/uaa")项目，改造成基于spring boot/spring cloud的架构
User Account and Authentication (UAA) Server
Oauth2.0 uaa server,OAuth2 provider
jwt OpenId Connect LDAP
SSO service
微服务授权中心，互联网账号ID
基于spring boot/spring cloud
配合spring session可实现应用无状态化
授权码验证：网关gateway和uaa各有一个验证的session，保持集群内session同步使用Spring session redis ,
web 应用推荐此模式
密码验证直接请求uaa分发token，后续请求带上token, app 掉用推荐此方式
客户端密码：直接使用验证客户端凭证请求jwt token，用于内部或第三方API 掉用


- [idcenter](https://github.com/travelersun/idcenter "idcenter")
分布式序列中心https://github.com/travelersun/idcenter 
改造自[https://github.com/zhongxunking/idcenter.git](https://github.com/zhongxunking/idcenter.git "https://github.com/zhongxunking/idcenter.git")项目，改造成基于spring boot/spring cloud的架构,权限验证通过网关gateway Spring Cloud Security Oauth2 控制
idcenter（分布式ID中心）：高效的分布式id生成器，每个客户端tps都可达到150万，服务端毫无压力。具备完整的登录、权限校验。使用http协议进行通信，可支持多语言。部署简单、页面操作简洁、运维成本低。后台逻辑简单（代码量不超过4千行），让你能够hold得住。

- [xxl-job](https://github.com/travelersun/xxl-job "xxl-job")
分布式调度中心https://github.com/travelersun/xxl-job
XXL-JOB是一个轻量级分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。
基于spring boot/spring cloud.权限验证通过网关gateway Spring Cloud Security Oauth2 控制。

- [vue-element-admin](https://github.com/travelersun/vue-element-admin "vue-element-admin")
微服务前端项目https://github.com/travelersun/vue-element-admin
vue-element-admin 是一个后台前端解决方案，它基于 vue 和 element-ui实现。它使用了最新的前端技术栈，内置了 i18n 国际化解决方案，动态路由，权限验证，提炼了典型的业务模型，提供了丰富的功能组件，它可以帮助你快速搭建企业级中后台产品原型。

- [foundation](https://github.com/travelersun/foundation "foundation")
微服务基础中心https://github.com/travelersun/foundation
基础中心的部分数据模型参考了Oracle E-Business Suite 的数据模型设计，
集成Spring Cloud Security Oauth2 ,Mybatis plus，query-filtering
前端由vue-element-admin项目完成，提供以下服务：
	1. 功能管理
	1. 菜单管理
	1. 应用管理
	1. 用户管理
	1. 权限与权限组
	1. Oauth2 客户端管理
	1. 职责管理
	1. 数据字典
	1. 值集
	1. 快速代码
	1. 地址管理
	1. 组织管理
	1. 组织层次结构
	1. 配置文件
	1. 系统配置文件选项
	1. 用户配置文件选项
	1. 安全性配置文件

工具类项目：
- [common-excel-parser](https://github.com/travelersun/common-excel-parser "common-excel-parser")
https://github.com/travelersun/common-excel-parser
Java 对象与excel映射的读写工具,可方便灵活操作excel表格。后续考虑集成Oracle BI Publisher java类库,方便json或xml数据生成报表
- [query-filtering](https://github.com/travelersun/query-filtering "query-filtering")
https://github.com/travelersun/query-filtering
Json filter 语法 构建最终sql语句的表达式构建工具,结合mybatis可实现强大的查询功能


遗留项目：
- [tianzhu-core](https://github.com/travelersun/tianzhu-core "tianzhu-core")
https://github.com/travelersun/tianzhu-core
早期单体java web通用后端管理系统基础开发框架，提供基础通用功能和组件。
基于主流的（Spring + Spring MVC + Hibernate/MyBatis）web架构
引入JPA、Spring-Data-JPA提升持久层架构规范性和开发效率
基于流行JQuery/Bootstrap等UI框架和插件整合，良好的浏览器兼容性和移动设备访问支持
基于Maven的项目和组件依赖管理模式，便捷高效的与持续集成开发集成

## 功能截图









## RoadMap
- 分布式事务中心 集成https://github.com/keets2012/Lottor
- 分布式锁  基于redis,zookeeper,数据库,consul,etcd (待调研) ?
- 配置中心 集成https://github.com/ctripcorp/apollo
- Spring cloud gateway 改造 动态路由 结合oauth2动态权限拦截配置 限流 分为入口网关与内部对外网关
- 应用管理Spring boot admin
- 熔断监控turbine hystrix dashboard
- 消息队列 Spring cloud bus
- 分布式链路追踪zipkin
- 日志系统 E/FLK
- docker compose 本地开发一键打包部署
- k8s 生产环境docker镜像部署
