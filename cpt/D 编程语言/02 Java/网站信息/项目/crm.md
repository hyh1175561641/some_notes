


# 数据库



# 数据层

```java
// BaseMapper.java

selectByPrimaryKey 根据id查询详情
selectByParams 多条件查询
insertSelective 添加记录返回行数
insertHasKey 添加记录返回主键
insertBatch 批量添加
updateByPrimaryKeySelective 更新单条数据
updateBatch 批量更新
deleteByPrimaryKey 主键删除
deleteBatch 批量删除

CusDevPlanMapper.java
ModuleMapper.java
PermissionMapper.java
RoleMapper.java
SaleChanceMapper.java
UserMapper.java
UserRoleMapper.java

```









# 业务层


```java

// BaseService
insertSelective 添加记录返回行数
insertHasKey 添加记录返回主键
insertBatch 批量添加
selectByPrimaryKey 查询详情
selectByParams 多条件查询
updateByPrimaryKeySelective 更新单条记录
updateBatch 批量更新
deleteByPrimaryKey 删除单条记录
deleteBatch 批量删除
queryByParamsForTable 分页查询

// CusDevPlanService
findCusDevPlanByItem 条件查询

// ModuleService
findAllModules 查询所有的资源信息
findModules 

// PermissionService

// RoleService

// SaleChanceService

// UserModel

// UserRoleService

// UserService



```








# 接口层



```java


// BaseController
// IndexController



// CusDevPlanController
// ModuleController
// PermissionController
// RoleController
// SaleChanceController
// UserController
// UserRoleController


```






# 前端


首页logo


头部功能



导航栏项目

营销管理: 营销机会管理,客户开发计划
服务管理: 服务创建,服务分配,服务处理,服务反馈,服务归档
统计报表: 客户贡献分析,客户构成分析,客户服务分析,客户流失分析
系统设置: 字典管理,用户管理,角色管理,菜单管理










