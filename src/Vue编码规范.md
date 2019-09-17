# 概述

本文根据生产实践和一些行业内的规范，总结了适合前端团队的`vue`编码风格，为团队成员提供编码风格标准和参考依据，规则不是固定的，最终以实际项目中`lint`规则为准！

# 目录结构

1. 按照项目实际运作情况，总结出[前端项目目录结构及文件命名规范](https://cumt-robin.github.io/FE-guide/项目目录结构规范.html)。
2. `vue`源代码统一放置于`/src`目录下，结构如下：

```
├─App.vue
├─main.js
│
├─api API封装和适配
│  ├─api.js
│  │
│  ├─base
│  │
│  ├─eqp
│  │
│  └─user
│
├─assets 图片字体等资源
│  ├─fonts
│  │
│  └─image
│
├─authority 处理动态路由权限
│  ├─generate-routes.js
│  ├─route-map.js
│
├─components 自定义组件
│  ├─index.js
│  
├─directives 自定义指令
│  ├─dialog-drag.js
│  ├─index.js
│
├─icons SVG图标
│  ├─index.js
│  │
│  └─svg
│     ├─history.svg
│
├─mock 接口模拟
│  ├─bsj.js
│  ├─index.js
│  │
│  ├─eqp
│  │  └─truck
│  │     ├─index.js
│  │
│  └─user
│     └─menu
│        ├─index.js
│
├─router 路由
│  ├─404.js
│  ├─base-url.js
│  ├─common.js
│  ├─index.js
│  │
│  └─modules
│     └─test
│        ├─index.js
│
├─store 状态管理
│  ├─index.js
│  │
│  └─modules
│     ├─user.js
│
├─styles 样式
│  ├─index.scss
│  │
│  ├─global 全局样式
│  │  ├─common.scss 公共样式
│  │  ├─element-ui.scss ElementUI定制样式
│  │  ├─element-variables.scss 重设ElementUI默认的scss变量
│  │  ├─iconfont.scss 字体图标
│  │  ├─index.scss 引入同目录下的其他scss
│  │  ├─layouts.scss 布局样式
│  │  ├─mixins.scss 维护mixin
│  │  ├─reset.scss 重设浏览器自带样式，保证各浏览器基本风格一致
│  │  ├─variables.scss 维护scss变量
│  │
│  └─scoped 局部样式
│     ├─login.scss
│
├─utils 工具集
│  ├─helper.js
│
└─views 页面
    ├─404
    │  ├─index.vue
    │
```

3. `views`目录下是项目的所有页面级`vue`文件，基本的原则是按照路由层级，结合功能特性，分模块书写。截取了一部分为例说明。

```
├─404 一级路由
│  ├─index.vue
│
├─backend 一级路由
│  ├─index.vue
│  │
│  ├─cloud-platform 二级路由
│  │  ├─index.vue
│  │  │
│  │  ├─department 三级路由
│  │  │
│  │  ├─device 这单纯是一个目录，只是为了对齐业务设计，将云盒，云环，控制器等类似功能放在同一个目录归类
│  │  │  ├─cloud-box 三级路由
│  │  │  │
│  │  │  └─controller 三级路由
│  │  │
│  ├─datacenter 二级路由
│  │
├─login 一级路由
│  ├─index.vue
│
```

# 文件夹及文件命名

统一使用`kebab-case`（短横线）命名法来命名文件夹及文件，见[前端项目目录结构及文件命名规范](https://cumt-robin.github.io/FE-guide/项目目录结构规范.html)。

# 命名规范

## 组件命名

**【强制】**如上文所述，`vue`组件文件命名采用`kebab-case`（短横线）命名法，如`icon-font.vue`。

**【强制】**给组件设置`name`属性时，应采用大驼峰写法，如`name: 'IconFont'`，对应规则`vue/name-property-casing`

**【强制】**使用组件时，应遵循以下规则：

1. 导入组件

```javascript
// 导入的变量名应为大驼峰写法
import EditUser from "./edit-user.vue";
```

2. 声明组件

```javascript
components: {
  EditUser
}
```

3. 模板中使用

```html
<!-- 采用kebab-case（短横线）写法使用组件标签 -->
<edit-user />
```

## template

参照[HTML编码规范](https://cumt-robin.github.io/FE-guide/HTML编码规范.html)，并结合以下规则。

## script

参照[Javascript编码规范](https://cumt-robin.github.io/FE-guide/Javascript编码规范.html)即可。

## style

参照[CSS编码规范](https://cumt-robin.github.io/FE-guide/CSS编码规范.html)即可。

# 代码风格

## 缩进

以4空格缩进为准，参照[Javascript编码规范](https://cumt-robin.github.io/FE-guide/Javascript编码规范.html)即可。

## 组件书写规范

1. `vue`组件一般分为三部分，`template`, `script`, `style`，各部分之间应有空行分隔。
2. `vue`组件代码书写顺序如下：

```javascript
// "vue/order-in-components"
export default {
    // 组件依赖声明
    components: {},
    // 外部输入属性
    props: {},
    // 实例数据
    data() {
        return {}
    },
    // 计算属性
    computed: {},
    // 侦听属性
    watch: {},
    // 生命周期，按顺序写
    beforeCreate() {},
    created() {},
    beforeMount() {},
    mounted() {},,
    beforeUpdate() {},
    updated() {},
    beforeDestroy() {},
    destroyed() {},
    // 实例方法
    methods: {},
    // 实例指令
    directives: {},
    // 实例过滤器
    filters: {}
}
```

## template

// TODO

## script

参照[Javascript编码规范](https://cumt-robin.github.io/FE-guide/Javascript编码规范.html)即可。

## style

// TODO

# 最佳实践

## template

### 标签自闭合

**【建议】**当组件标签内未包含内容时，应采用自闭合写法。

```html
// good
<child-component user-name="Tusi" />

// bad
<child-component user-name="Tusi"></child-component>
```

### v-if与v-for

**【强制】**禁止在同一标签上使用`v-if`与`v-for`

### prop写法

**【建议】**组件声明`prop`时，采用小驼峰写法；绑定时，应采用`kebab-case`（短横线）命名法。

```
// vue/prop-name-casing
// good
// 声明
props: {
    userName: {
        type: String
    }
}
// 绑定
<child-component user-name="Tusi" />
```

### prop与event绑定

**【建议】**采用简写形式绑定，`:`绑定属性，`@`绑定事件，对应规则`vue/v-bind-style`, `vue/v-on-style`

### 多属性绑定

**【建议】**当组件的属性或事件绑定大于3个时，应分行书写，一行一个。

```html
// "vue/max-attributes-per-line": [2, { "singleline": 3 }]
// good
<child-component
  user-name="Tusi"
  sex="男"
  age="18"
  nation="汉族"
/>

// bad
<child-component user-name="Tusi" sex="男" age="18" nation="汉族" />
```

### 属性绑定编写顺序

- DEFINITION：`is`
- LIST_RENDERING：`v-for`
- CONDITIONALS：`v-if, v-else-if, v-else, v-show, v-cloak`
- RENDER_MODIFIERS：`v-once, v-pre`
- GLOBAL：`id`
- UNIQUE：`ref, key, v-slot, slot`
- TWO_WAY_BINDING：`v-model`
- OTHER_DIRECTIVES：`v-custom-directive`
- OTHER_ATTR：`custom-prop` 
- EVENTS：`@eventName="eventHandler"` 
- CONTENT：`v-text, v-html` 

### this

**【强制】**不要在`template`中使用`this`访问`vue`实例属性或方法，因为默认已经绑定了`this`。对应规则`vue/this-in-template`

### 事件处理器

**【强制】**如果`@`绑定的事件处理器不带参数，则禁止在方法名后加括号。对应规则`vue/v-on-function-call`

## script

### prop类型

**【强制】**必须指定`prop`的类型，使用对应类型的构造函数而非字符串

```javascript
// vue/require-prop-types
// good
props: {
    value: {
        type: String
    }
}

// bad
props: {
    value: {
        type: 'String'
    }
}
```

### prop默认值

**【建议】**给`prop`指定默认值`default`

**【强制】**`Array`和`Object`类型的`prop`，在指定默认值时，应使用函数返回默认值，而非字面量。

```javascript
// good
props: {
    options: {
        type: Object,
        default: function() {
            return {}
        }
    }
}

// bad
props: {
    value: {
        type: 'String',
        default: {}
    }
}
```

### 重复属性名

**【强制】**禁止在`data`, `props`, `computed`, `methods`等出现重复的属性名

```javascript
// bad
props: {
    propName: String
},
data: {
    propName: null
},
methods: {
    propName () {}
}
```

### 保留关键字

**【强制】**禁止在给`vue`实例定义属性或方法时出现`vue`保留的一些关键字，如`$el`, `$parent`, `$refs`, `$nextTick`等。

### 计算属性

**【强制】**禁止在计算属性计算方法中，改变其依赖值。

```javascript
// bad
computed: {
    fullName () {
        this.firstName = 'Tusi' // 错误地改变了依赖值
        return `${this.firstName} ${this.lastName}`
    }
}
```

## style

// TODO


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