# 概述

为了满足统一性和规范性，体现语义化的原则，我对前端的接口适配层提出了一种约束方式，基本上是符合`RESTful API`的原则的。

# 微服务架构

首先，为了对齐后端微服务架构，在前端将`API`调用分为三个模块。

```
├─base  负责调用basecenterweb服务
├─eqp  负责调用eqpcenterweb服务
└─user  负责调用ucenterweb服务
```

每个模块下都定义了统一的微服务命名空间，例如`/src/api/base/index.js`：

```javascript
export const namespace = 'basecenterweb';
```

# 特性案例

每个功能特性都有独立的`js`模块，以角色管理相关接口为例，路径是`/src/api/user/role.js`

```javascript
import api from '../api'
import { rejectNull } from "../../utils/helper";
import { namespace } from "./index"

// 特性命名空间
const feature = 'role'

// 添加
export const addRole = params => api.post(`/${namespace}/${feature}/add`, rejectNull(params));

// 删除
export const deleteRole = params => api.deletes(`/${namespace}/${feature}/delete`, params);

// 更新
export const updateRole = params => api.put(`/${namespace}/${feature}/update`, rejectNull(params));

// 条件查询
export const findRoles = params => api.get(`/${namespace}/${feature}/find`, params);

// 查询所有记录
export const getAllRoles = () => findRoles();

// 获取详情
export const getRoleDetail = params => api.get(`/${namespace}/${feature}/detail`, params);

// 分页
export const getRolePage = params => api.get(`/${namespace}/${feature}/page`, rejectNull(params));

// 搜索
export const searchRole = params => params.wd ? api.get(`/${namespace}/${feature}/search`, rejectNull(params)) : getRolePage(params);

```

- 每一条接口都根据`RESTful`风格，调用增（`api.post`）删（`api.deletes`）改（`api.put`）查（`api.get`）的底层方法。

- 调用的`url`由三部分组成，格式：`/微服务命名空间/特性命名空间/方法`

- 接口适配层函数命名规范：
  - 新增：`addXXX`
  - 删除：`deleteXXX`
  - 更新：`updateXXX`
  - 根据ID查询记录：`getXXXDetail`
  - 条件查询一条记录：`findOneXXX`
  - 条件查询：`findXXXs`
  - 查询所有记录：`getAllXXXs`
  - 分页查询：`getXXXPage`
  - 搜索：`searchXXX`



**注：请按照以上规范执行，让接口维护变得简单。**

<div id="gitalk-container"></div>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
<script>
var gitalk = new Gitalk({
    clientID: "abe61bb2112d4926d0b9",
    clientSecret: "760737a207de2813a6586e1d2c14dd187ddeea64",
    repo: "FE-guide",
    owner: "cumt-robin",
    admin: ["cumt-robin"],
    id: decodeURIComponent(location.pathname)
});
gitalk.render("gitalk-container");
</script>