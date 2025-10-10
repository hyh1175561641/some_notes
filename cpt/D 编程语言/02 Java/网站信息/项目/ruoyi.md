
https://www.ruoyi.vip/
https://gitee.com/y_project/RuoYi
https://gitee.com/y_project/RuoYi-Vue
https://gitee.com/y_project/RuoYi-Cloud
https://gitee.com/y_project/RuoYi-App





# 分析项目的流程和顺序

每个类上面写上这个类有啥功能
每个方法下面写了这个方法的功能和流程
复杂语句写上这个语句执行了什么功能



# 若依依赖及配置

后端
Spring Boot
Apache Shiro

前端
Thymeleaf

数据库
MyBatis
Druid

工具
Quartz
Fastjson



# 模块

ruoyi 父模块
ruoyi-admin 页面模块
ruoyi-common 通用工具
ruoyi-framework 框架核心
ruoyi-generator 代码生成器
ruoyi-quartz 定时任务
ruoyi-system 系统模块





# 数据库


系统管理
  用户管理
sys_user 用户信息表
  角色管理
sys_role 角色信息表
  菜单管理
sys_menu 菜单权限表
  部门管理
sys_dept 部门表
  岗位管理
sys_post 岗位信息表

  字典管理
sys_dict_data 字典数据表
sys_dict_type 字典类型表
  参数设置
sys_config 参数配置表
  通知公告
sys_notice 通知公告表
  日志管理
sys_oper_log 操作日志记录
sys_logininfor 系统访问记录
系统监控
  在线用户
sys_user_online 在线用户记录

系统: 用户 角色 菜单 
现实: 用户 部门 岗位

系统
sys_user_role 用户和角色关联表 uid rid
sys_role_menu 角色和菜单关联表 rid mid

现实
sys_user_post 用户与岗位关联表 uid pid
sys_role_dept 角色和部门关联表 uid did




定时器
sys_job 定时任务调度表
sys_job_log 定时任务调度日志表

quartz数据库
QRTZ_BLOB_TRIGGERS Blob类型的触发器表
QRTZ_CALENDARS 日历信息表
QRTZ_CRON_TRIGGERS Cron类型的触发器表
QRTZ_FIRED_TRIGGERS 已触发的触发器表
QRTZ_JOB_DETAILS 任务详细信息表
QRTZ_LOCKS 存储的悲观锁信息表
QRTZ_PAUSED_TRIGGER_GRPS 暂停的触发器表
QRTZ_SCHEDULER_STATE 调度器状态表
QRTZ_SIMPLE_TRIGGERS 简单触发器的信息表
QRTZ_SIMPROP_TRIGGERS 同步机制的行锁表
QRTZ_TRIGGERS 触发器详细信息表

代码生成器
gen_table 代码生成业务表
gen_table_column 代码生成业务表字段

# 前端显示


logo和侧边导航栏是一体的,如果侧边导航栏收缩,logo也要跟着一起收缩,要考虑到变化时该怎么办.

个人中心显示个人信息以及修改基本资料,弹框修改密码.



菜单导航
首页
系统管理
  用户管理
  角色管理
  菜单管理
  部门管理
  岗位管理
  字典管理
  参数设置
  通知公告
  日志管理
系统监控
  在线用户
  定时任务
  数据监控
  服务监控
  缓存监控
系统工具
  表单构建  
  代码生成  代码生成器
  系统接口  Swagger
若依官网    外链接
实例演示




# 后端接口




# 登录模块




# 系统模块
ruoyi-system 系统模块
## 系统配置







# 上传下载



/common/download GET 下载请求
/common/download/resource GET 本地资源下载
/common/upload POST 上传一个
/common/uploads POST 上传多个




# 生成器模块


# 定时任务模块
























