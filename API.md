# Fund Manager
###### 第一次制定于 *2019-07-19*

###### 编码： UTF-8
###### 日期： yyyy-MM-dd HH:mm:ss

## API 文档说明:
###### 公共请求消息头:
|    消息头    | 是否必选 |              说明              |
|:------------:|:--------:|:------------------------------:|
| Content-Type |  非必选  | application/json;charset=utf-8 |


###### Error 返回格式:
| 参数名  |  类型   |   说明   |
|:-------:|:-------:|:--------:|
|  flag   | Boolean | 是否成功 |
|  code   | String  |  错误码  |
| message | String  | 错误描述 |
|  data   | String  |   数据   |

###### code为错误码，所有错误码取值来源 XXX 公共错误码和 XXX 专有错误码.
```
Error 示例
{
  "flag" : "false"
  "code" : "AccessDenied",
  "message" : "Access Denied."
  "data" : ""
}
```
## 错误码说明:
##### 公共错误码:
| 错误码 | 错误描述 | HTTP状态码 | 中文注释 | 英文解释 |
|:------:|:--------:|:----------:|:--------:|:--------:|
| 00000  |  00000   |   00000    |  00000   |  00000   |

##### 专用错误码:
| 错误码 | 错误描述 | HTTP状态码 | 中文注释 | 英文解释 |
|:------:|:--------:|:----------:|:--------:|:--------:|
| 00000  |  00000   |   00000    |  00000   |  00000   |

## 接口说明：
###### 所有接口:
|     类型      |           子类型           |        说明        |        权限         | 请求类型 |                 参数名称                  |     参数类型     |
|:-------------:|:--------------------------:|:------------------:|:-------------------:|:--------:|:-----------------------------------------:|:----------------:|
| fund/actuator |         httptrace          |    HTTP请求跟踪    |   httptrace:view    |   GET    |                                           |                  |
|      log      |            list            |    操作日志列表    |      log:view       |   GET    |                                           |                  |
|      log      |            {id}            |      删除日志      |     log:delete      |  DELETE  |                    ids                    |      String      |
|      log      |           excel            |    导出Excel表     |     log:export      |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|   loginLog    |            list            |    登录日志列表    |    loginlog:view    |   GET    |                                           |                  |
|   loginLog    |            {id}            |    删除日志成功    |   loginlog:delete   |  DELETE  |                    ids                    |      String      |
|   loginLog    |           excel            |    导出Excel表     |   loginlog:export   |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|    session    |            list            |    在线用户列表    |     online:view     |   GET    |                                           |                  |
|    session    |            {id}            |      踢出用户      |    user:kickout     |  DELETE  |                    id                     |      String      |
|               |                            |                    |                     |          |                                           |                  |
|     dept      |        select/tree         |     获取部门树     |                     |   GET    |                                           |                  |
|     dept      |            tree            |     获取部门树     |                     |   GET    |                                           |                  |
|     dept      |                            |      新增部门      |      dept:add       |   POST   |                   dept                    |       Dept       |
|     dept      |         {deptIds}          |      删除部门      |     dept:delete     |  DELETE  |                  deptIds                  |      String      |
|     dept      |           update           |      修改部门      |     dept:update     |   PUT    |                   dept                    |       Dept       |
|     dept      |           excel            |    导出Excel表     |     dept:export     |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|               |           login            |        登录        |                     |   POST   | username/password/verifyCode/{rememberMe} | String/{boolean} |
|               |          register          |        注册        |                     |   POST   |             username/password             |      String      |
|     index     |         {username}         |      用户主页      |                     |   GET    |                 username                  |      String      |
|     image     |          captcha           |       验证码       |                     |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|     menu      |         {username}         |      个人菜单      |                     |   GET    |                 username                  |      String      |
|     menu      |            tree            |     个人菜单树     |                     |   GET    |                                           |                  |
|     menu      |                            |      新增菜单      |      menu:add       |   POST   |                   menu                    |       Menu       |
|     menu      |         {menuIds}          |      删除菜单      |     menu:delete     |  DELETE  |                  menuIds                  |      String      |
|     menu      |           update           |      修改菜单      |     menu:update     |   PUT    |                   menu                    |       Menu       |
|     menu      |           excel            |    导出Excel表     |     menu:export     |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|     role      |            list            |      角色列表      |      role:view      |   GET    |                                           |                  |
|     role      |                            |      新增角色      |      role:add       |   POST   |                   role                    |       Role       |
|     role      |         {roleIds}          |      删除角色      |     role:delete     |  DELETE  |                  roleIds                  |      String      |
|     role      |           update           |      修改角色      |     role:update     |   PUT    |                   role                    |       Role       |
|     role      |           excel            |    导出Excel表     |     role:export     |   GET    |                                           |                  |
|               |                            |                    |                     |          |                                           |                  |
|     user      |         {username}         |    获取用户信息    |                     |   GET    |                 username                  |      String      |
|     user      |      check/{username}      | 通过用户名查找用户 |                     |   GET    |              username/userId              |      String      |
|     user      |            list            |      用户列表      |      user:view      |   GET    |                                           |                  |
|     user      |                            |      新增用户      |      user:add       |   POST   |                   user                    |       User       |
|     user      |         {userIds}          |      删除用户      |     user:delete     |  DELETE  |                  userIds                  |      String      |
|     user      |           update           |      修改用户      |     user:update     |   PUT    |                   user                    |       User       |
|     user      | password/reset/{usernames} |   重置(默认)密码   | user:password:reset |   POST   |                 usernames                 |      String      |
|     user      |      password/update       |      修改密码      |                     |   POST   |          oldPassword/newPassword          |      String      |
|     user      |       avatar/{image}       |      修改头像      |                     |   GET    |                   image                   |      String      |
|     user      |        theme/update        |    修改主题背景    |                     |   POST   |                theme/isTab                |      String      |
|     user      |       profile/update       |    修改个人信息    |                     |   POST   |                   user                    |       User       |
|     user      |           excel            |    导出Excel表     |     user:export     |   GET    |                                           |                  |

###### 参数实体类型说明
###### Dept:
|  类型  |  参数名称  |    说明    |
|:------:|:----------:|:----------:|
|  Long  |   deptId   |   部门ID   |
|  Long  |  parentId  | 上级部门ID |
| String |  deptname  |  部门名称  |
|  Long  |  orderNum  |    排序    |
|  Date  | createTime |  创建时间  |
|  Date  | modifyTime |  删除时间  |

###### Menu:
|  类型  |  参数名称  |     说明     |
|:------:|:----------:|:------------:|
|  Long  |   menuId   |    菜单ID    |
|  Long  |  parentId  |  上级菜单ID  |
| String |  menuName  | 菜单按钮名称 |
| String |    url     |   菜单URL    |
| String |   perms    |   权限标识   |
| String |    icon    |     图标     |
| String |    type    | 0按钮,1菜单  |
|  Long  |  orderNum  |     排序     |
|  Date  | createTime |   创建时间   |
|  Date  | modifyTime |   删除时间   |

###### Role
|         类型          |  参数名称  |           说明            |
|:---------------------:|:----------:|:-------------------------:|
|         Long          |   roleId   |          角色ID           |
|        String         |  rolename  |         角色名称          |
|        String         |   remark   |         角色描述          |
|         Date          | createTime |         创建时间          |
|         Date          | modifyTime |         删除时间          |
| String(transient修饰) |  menuIds   | 角色对应的菜单（按钮） id |

###### User
|  类型  |   参数名称    |           说明           |
|:------:|:-------------:|:------------------------:|
|  Long  |    userId     |         用户 ID          |
| String |   username    |         用户名称         |
| String |   password    |  用户密码 默认 1234qwer  |
|  Long  |    deptId     |          部门ID          |
| String |     email     |           邮箱           |
| String |    mobile     |          手机号          |
| String |    status     |     状态 1有效 0无效     |
|  Date  |  createTime   |         创建时间         |
|  Date  |  modifyTime   |         删除时间         |
|  Date  | lastLoginTime |       最近登录时间       |
| String |     ssex      |    性别 0男 1女 2保密    |
| String |    avatar     |  头像 默认  default.jpg  |
| String |     theme     | 主题 black黑色 white白色 |
| String |     isTab     | 是否开启Tab 0开启，1关闭 |
| String |  description  |           描述           |
| String |   deptname    |         部门名称         |
| String |    roleId     |          角色ID          |
| String |   rolename    |         角色名称         |



###### 具体说明：
| 请求方法 | 参数名称 | 参数类型 | 是否必须 | 描述 |
|:--------:|:--------:|:--------:|:--------:|:----:|
|          |          |          |          |      |
