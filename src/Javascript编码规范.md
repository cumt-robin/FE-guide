# 概述

本文根据生产实践和一些行业内的规范，总结了适合前端团队的`javascript`编码风格，为团队成员提供编码风格标准和参考依据，规则不是固定的，最终以实际项目中`lint`规则为准！

# 文件夹及文件命名

统一使用`kebab-case`（短横线）命名法来命名文件夹及文件，见[前端项目目录结构及文件命名规范](https://cumt-robin.github.io/FE-guide/项目目录结构规范.html)。

# 命名规范

- 命名应具备语义化的基本原则，禁止使用无具体含义的命名。

```javascript
// good
let age = 18;
let sex = '男';

// bad
let var1 = 18;
let s = '男';
```

- 禁止采用保留关键字进行命名，可参考[ES5注解 Reserved Words](http://es5.github.io/#x7.6.1)，如果不确定是不是关键字，则采用单词组合的方式增强命名。

```javascript
// good
let defaultValue = 1;

// bad
let default = 1;
```

## 常量

全部采用**大写**，单词间用下划线`_`分隔。系统中常量应该尽量统一维护在某个固定文件中，如`/src/utils/const.js`，当然也可视业务而定进行适当分离。

```javascript
// good
export const BSJ_CUSTOMER_KEY = 'fa1ceced-70ec-4717-8a09-6174cffd2b5f'

// bad
export const BSJCUSTOMERKEY = 'fa1ceced-70ec-4717-8a09-6174cffd2b5f'
```

## 变量

- 采用小驼峰（`Lower Camel Case`）写法。

```javascript
// good
let userName = 'Tusi'

// bad
let UserName = 'Tusi'
```

- 对于引用类型（`Array`或`Object`），请使用`const`定义，而不要使用`var`或`let`，防止变量被重新赋值而导致意料之外的`bug`。

```javascript
// good
const options = {
  startTime: '2018',
  endTime: '2019'
}

// bad
let options = {
  startTime: '2018',
  endTime: '2019'
}
```

## 函数命名

- 普通函数采用小驼峰（`Lower Camel Case`）写法，并采用动宾结构进行命名，如：

```javascript
// good
function getUserInfo() {}
function addUser() {}

// bad
function userinfo() {}
function add() {}
```

- 构造函数采用大驼峰（`Upper Camel Case`）写法，也称之为`Pascal Case`。

```javascript
// good
function User() {}
let userInstance = new User();

// bad
function user() {}
let userInstance = new user();
```

## 类命名

采用大驼峰（`Upper Camel Case`）写法。

# 代码风格

## 缩进

- 配置时，统一采用4空格缩进风格，禁止使用制表符`tab`缩进。如若遇见缩进设置有误的文件，可参考[VSCode缩进方式转换](https://coollu.yuque.com/trlc33/oabv03/rqtu35)。

![1568628900886](http://qncdn.wbjiang.cn/%E7%A6%81%E6%AD%A2%E4%BD%BF%E7%94%A8tab%E7%BC%A9%E8%BF%9B.png)

- 操作时，仍使用`tab`键缩进，根据配置，已默认执行了`tab`转`space`

## 空格

**【强制】**操作符前后保留一个空格，包括赋值运算符，算术运算符，比较运算符，逻辑运算符，条件运算符（三元运算符）等。

```javascript
// "space-infix-ops": 2
// good
let result = 1 + 2;

// bad
let result = 1+2;
```

**【强制】**禁止出现多余的空格。

```javascript
// 'no-multi-spaces': 2
// good
let result = 1 + 2;

// bad
let result = 1 +  2;
```

**【强制】**函数圆括号之前不加空格，圆括号之后加一个空格。

```javascript
// "space-before-function-paren": [2, "nerver"]
// "space-before-blocks": [2, 'always']
// good
function login(params) {
  // ...
}

// bad
function login(params){

}
```

**【强制】**关键字前后各一个空格，例如`if`, `switch`, `for`等常用关键字。

```javascript
// 'keyword-spacing': [2, { before: true, after: true }]
// good
if (bool) {
    //...
} else {
    //...
}

// bad
if(bool) {
    //...
} else{
    //...
}
if (bool) {
    //...
}else {
    //...
}
```

**【强制】**花括号开始后和结束前有空格

```javascript
// 'block-spacing': [2, 'always']
// good
function getBool() { return true; }

// bad
function getBool() {return true;}
```

**【强制】**逗号，分号前无空格，后有空格

```javascript
// "semi-spacing": [2, {"before": false, "after": true}]
// good
[1, 2]
var name; var sex;

// bad
[1 , 2]
[1,2]
[1 ,2]
var name;var sex;
```

**【强制】**箭头函数的箭头之前和之后有空格

```javascript
// 'arrow-spacing': [2, { before: true, after: true }]
// good
promiseTask.then(res => {
    // ...
})

// bad
promiseTask.then(res=> {
    // ...
})
promiseTask.then(res =>{
    // ...
})
```

**【强制】**在对象字面量、解构赋值 和`import/export`的花括号中使用一致的空格。若对象最后一个元素是对象或数组，则结束花括号前不需要空格。

```javascript
// 'object-curly-spacing': [2, 'always', { objectsInObjects: false, "arraysInObjects": false }]
// good
let obj = { name: 'Tusi', sex: '男' }
let { name, sex } = { name: 'Tusi', sex: '男' }
let newObj = { name: 'Tusi', sex: '男', moreInfo: { salary: 1 }}
import { merge } from "utils"

// bad
let obj = {name: 'Tusi', sex: '男' }
let { name, sex} = { name: 'Tusi', sex: '男' }
let newObj = { name: 'Tusi', sex: '男', moreInfo: { salary: 1} }
import { merge} from "utils"
```

**【强制】**数组内部除逗号后有空格外，禁止出现其他空格

```javascript
// 'array-bracket-spacing': [2, 'never']
// good
let nameArr = ['Tusi', '张三', '李四']

// bad
let nameArr = [ 'Tusi', '张三', '李四' ]
```

**【强制】**冒号前无空格，冒号后有空格，适用于`case`，对象键值对等。

```javascript
// "switch-colon-spacing": [2, {"after": true, "before": false}]
// 'key-spacing': [2, { beforeColon: false, afterColon: true, mode: 'strict' }]
// good
switch (age) {
    case 18: break;
    default: break;
}
let obj = { name: 'Tusi', sex: '男' }

// bad
switch (age) {
    case 18 : break;
    default :break;
}
let obj = { name:'Tusi', sex :'男' }
```

## 花括号风格

**【强制】**控制语句或声明语句中，开始花括号应处于第一行，内容另起一行，结束花括号另起一行。

```javascript
// 'brace-style': [2, '1tbs', { allowSingleLine: true }]
// good
function login() {
  if (bool) {
    // do something
  } else {
    // do something
  }
}

// bad
function login()
{
  if (bool)
  {
    // do something
  }
  else
  {
    // do something
  }
}
```

## 注释

**【建议】**使用合理的注释来解释代码，提高可读性，如单行注释，多行注释，[jsdoc注释](http://www.dba.cn/book/jsdoc/)。

# 最佳实践

## 禁止扩展原生对象

`no-extend-native`

**【强制】**除了团队内部明确的`shim`外，其他情况禁止扩展原生对象。

## 禁止使用eval, with

`no-eval`, `no-implied-eval`, `no-with`

**【强制】**`eval`是不安全的。`with`性能并不具备优势，并且有语义不明的风险。

## 禁止出现alert, confirm, prompt

`no-alert`

**【强制】**禁止出现`alert, confirm, prompt`，应使用自定义的`UI`组件来完成上述交互。

## 只遍历自身属性

**【强制】**在使用 `for in` 遍历对象时，使用`hasOwnProperty`判断是否为自身属性，防止遍历原型属性。

```javascript
// "guard-for-in": 2
// good
for (key in obj) {
  if (obj.hasOwnProperty(key)) {
    doSomething(key);
  }
}

// bad
for (key in obj) {
  doSomething(key);
}
```

## 推荐使用三等于

**【建议】**使用类型安全的 `===` 和 `!==` 操作符代替 `==` 和 `!=` 操作符，除非你明确你的逻辑没有问题！

```javascript
// 'eqeqeq': [2, 'allow-null']
// good
let isTrue = bool === true

// bad
let isTrue = maybeBool == true
```

## 禁止使用魔术数字

`no-magic-numbers`

**【建议】**魔术数字是指代码中多次出现的没有明确含义的数字，它最好由命名常量取代，否则可能不易理解。


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