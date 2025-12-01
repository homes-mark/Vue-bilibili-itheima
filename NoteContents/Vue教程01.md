```html
<!-- 引入axios -->
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>

<!-- 引入vue的开发版本包 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
```

# Vue 是什么？
Vue 是一个<font style="color:#DF2A3F;">用于构建用户界面</font>的<font style="color:#DF2A3F;">渐进式框架。</font>

构建用户界面：基于 数据 动态 渲染页面

渐进式：循序渐进（学一点，用一点）

框架：一套完整的项目解决方案（效率嘎嘎高）

官网：[https://cn.vuejs.org/](https://cn.vuejs.org/)

Vue2：[https://v2.cn.vuejs.org/](https://v2.cn.vuejs.org/)



Vue 的两种使用方式：

1、Vue 核心包开发

场景：局部 模块改造

2、Vue 核心包 & Vue 插件 工程化开发

场景：整站开发



![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761209492673-026775e9-0c2b-4661-ad37-9a1b8d13e608.png)



# 创建一个 Vue 实例
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761209774611-69462773-a2d8-4fdf-89dc-ba2aa3b2ade9.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- 创建Vue实例，初始化渲染
     1、准备容器（Vue管理的范围）
     2、引包 （开发版本包 / 生产版本包）
     3、创建实例
     4、添加配置项 => 完成渲染 -->
    <div id="app">
        <!-- 这里会编写一些用于渲染的代码逻辑 -->
        <h1>{{ msg }}</h1>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        // 一旦引入 Vuejs 核心包，在全局环境，就有了Vue构造函数
        const app = new Vue({
            // 通过 el 配置选择器，指定 Vue 实例要管理的范围
            el: '#app',
            // 通过 data 提供数据
            data: {
                msg: 'Hello Vue World!'
            }
        })
    </script>

</body>
</html>
```

# 模板
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="app">
        
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        
    </script>

</body>
</html>
```

# 插值语法
Vue 的模板语法

1、 作用：利用表达式进行插值，渲染到页面中

表达式：可以被求值的代码，js 引擎会将其计算出一个结果

2、语法： {{ 表达式 }}

3、注意点：

+ 使用的数据，必须在 data 中存在
+ 支持的是表达式，而不是语句
+ 不能在标签属性中使用 {{}} 语法

```html
<body>
    <div id="app">
        <h1>{{ nickname }}</h1>
        <h2>{{ friend.name }}</h2>
        <p>{{ friend.desc }}</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <script>
        const app = new Vue({
            el: '#app',
            data: {
                nickname: 'Mark',
                age: 25,
                friend: {
                    name: 'person',
                    desc: '啊啊啊啊啊啊'
                }
            }
        })
    </script>
</body>
```

# 核心特性：响应式
响应式：数据改变，视图自动更新

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761215575591-6535f583-3c4d-4c07-9328-53831514656b.png)

使用 Vue 开发，可以专注于业务核心逻辑即可



如何访问或修改数据

data 中的数据，最终会被添加到实例上

1、访问数据： 实例.属性名

2、修改数据：实例.属性名 = 值

# 安装开发者工具
**Vue Devtools**

1、谷歌应用商店  （下面这个版本会出现下图中的 Vue 栏）

[https://chromewebstore.google.com/detail/vuejs-devtools/iaajmlceplecbljialhhkmedjlpdblhp](https://chromewebstore.google.com/detail/vuejs-devtools/iaajmlceplecbljialhhkmedjlpdblhp)

2、极简插件



安装完之后，打开 Vue 运行的页面，**调试工具中 Vue 栏**，即可查看修改数据，进行调试

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761215767840-2e0d3e4f-53c7-410e-9c82-f9f094f055cc.png)

# Vue 指令
Vue 会根据不同的【<font style="color:#DF2A3F;">指令</font>】，针对标签实现不同的【<font style="color:#DF2A3F;">功能</font>】

指令：带有 <font style="color:#DF2A3F;">v-前缀</font>  的特殊 <font style="color:#DF2A3F;">标签属性</font>



## v-html 
作用：动态设置元素的 innerHTML

语法：v-html = '表达式'

```html
<body>
    <div id="app">
        <div v-html="msg"></div>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                msg: `
                <a href="https://www.baidu.com/">这是一个链接</a>
                `
            }
        })
    </script>

</body>
```

## v-show & v-if
<font style="color:rgb(190, 140, 4);">v-show</font>

1、作用：控制元素显示隐藏

2、语法：v-show="表达式"  表达式为 true 显示

3、 底层原理：切换 css 的 dispay 属性来控制显示隐藏 

4、场景：频繁切换显示隐藏的场景（购物车）

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761216838152-cb8f1553-5a00-4709-b0fd-a6714e707a4f.png)



<font style="color:rgb(190, 140, 4);">v-if</font>

1、作用：

2、语法：

3、 底层原理：根据判断条件控制元素的**创建和移除**

4、场景：要么显示，要么隐藏，不频繁切换的场景

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761216853641-9955aea5-abd1-4636-bbd0-1fa8ed183618.png)

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box {
            height: 100px;
            width: 200px;
            margin-bottom: 5px;
            text-align: center;
            border: 2px solid black;
            box-shadow: 2px 2px 2px #ccc;
        }
    </style>
</head>
<body>
    <div id="app">
        <div v-show="flag" class="box">我是v-show控制的盒子</div>
        <div v-if="flag" class="box">我是v-if控制的盒子</div>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                flag: false
            }
        })
    </script>

</body>
```

## v-else & v-else-if
1、作用：辅助 v-if 进行判断渲染

2、语法：v-else	 v-else-if="表达式"

3、注意：需要紧挨着  v-if 使用

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761217828550-afbb4c70-05eb-4f73-b1a9-9b1056be12ba.png)

```html
<body>
    <div id="app">
        <p v-if="gender === 1">性别：♂ 男</p>
        <p v-else>性别: ♀ 女</p>
        <hr>
        <p v-if="score >= 90">成绩评定A：奖励电脑一台</p>
        <p v-else-if="score >= 80">成绩评定B：奖励周末一日游</p>
        <p v-else-if="score >= 60">成绩评定C：奖励零食</p>
        <p v-else>成绩评定D：惩罚一周不能玩手机</p>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                gender: 2,
                score: 90
            }
        })
    </script>

</body>
```

## v-on
1、作用：注册事件 = 添加监听 + 提供处理逻辑

2、语法：

+ `v-on`：事件名 = "内联语句"
+ `v-on`：事件名 = "methods 中的函数名"

3、简写：`v-on:click = @click`

```html
<body>
    <div id="app">
        <button @click="count--">-</button>
        <span>{{ count }}</span>
        <button @click="count++">+</button>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                count: 100
            }
        })
    </script>

</body>
```

```html
<body>
    <div id="app">
        <button @click="fn">切换显示隐藏</button>
        <h1 v-show="isShow">黑马程序员</h1>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                isShow: true
            },
            methods: {
                fn() {
                    // 让提供的所有 methods 中的方法，this都指向当前实例
                    this.isShow = !this.isShow
                }
            }
        })
    </script>

</body>
```

4、调用传参

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761219826629-ab1f6522-c4f8-405f-af72-f780cce329e4.png)

```html
<body>
    <div id="app">
        <div class="box">
            <h3>自动售货机</h3>
            <button @click="buy(5)">可乐5元</button>
            <button @click="buy(10)">咖啡10元</button>
            <h3>余额为: {{ money }}</h3>
        </div>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                money: 100
            },
            methods: {
                buy(price) {
                    this.money -= price
                }
            }
        })
    </script>

</body>
```

## v-bind
1、作用：动态的设置 html 的标签属性  src  url  title

2、语法：v-bind:属性名="表达式"

3、缩写：v-bind:src ---> :src

```html
<body>
    <div id="app">
        <img v-bind:src="imgUrl" v-bind:title="imgTitle">
        <!-- 缩写 -->
        <img :src="imgUrl" :title="imgTitle">
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                imgUrl: './images/微信图片_20251004162904_1460_46.jpg',
                imgTitle: '这是微信图片'
            }
        })
    </script>

</body>
```

![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761226566520-f712cee8-397a-452a-b8d3-df80900f7fbc.png)

```html
<body>
    <div id="app">
        <button v-show="index > 0" @click="index--">上一页</button>
        <div>
            <!-- 缩写 -->
            <img :src="list[index]">
        </div>
        <button v-show="index < list.length - 1" @click="index++">下一页</button>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                index: 0,
                list: [
                    './images/微信图片_20251004162904_1460_46.jpg',
                    './images/微信图片_20251004162904_1461_46.jpg',
                    './images/微信图片_20251004162906_1463_46.jpg'
                ]     
            }
        })
    </script>

</body>
```



为了便于样式控制，Vue 扩展了 v-bind 的语法，可以针对 class 类名和 style 行内样式进行控制

### v-bind 操作 class
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761305215565-5a5ecda9-21c0-471d-a842-105a5b3b9b61.png)

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box {
            width: 200px;
            height: 200px;
            border: 3px solid #000;
            font-size: 30px;
            margin-top: 10px;
        }
        .pink {
            background-color: pink;
        }
        .big {
            width: 300px;
            height: 300px;
        }
    </style>
</head>
<body>
    <div id="app">
        <div class="box" :class="{pink: true, big: true}">黑马程序员</div>
        <div class="box" :class="['pink', 'big']">黑马程序员</div>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {

            },
            methods: {

            }
        })
    </script>

</body>
```

### 案例-京东秒杀
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761305852843-9657c586-0840-4df6-8644-aa4ccd3d8eaf.png)

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        ul {
            display: flex;
            padding: 0 10px;
            border-bottom: 2px solid #e01222;
        }
        li {
            width: 100px;
            height: 50px;
            line-height: 50px;
            text-align: center;
            list-style: none;
        }
        li a {
            display: block;
            text-decoration: none;
            color: #333;
            font-weight: bold;
        }
        li a.active {
            background-color: #e01222;
            color: #fff;
        }
    </style>
</head>
<body>
    <div id="app">
        <ul>
            <li v-for="(item, index) in list" :key="item.id" @click="activeIndex = index">
                <a :class="{active: activeIndex === index}" href="#">{{ item.name }}</a>
            </li>
        </ul>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                activeIndex: 0,
                list: [
                    {id: 1, name: '京东秒杀'},
                    {id: 2, name: '每日特价'},
                    {id: 3, name: '品类秒杀'}
                ]
            }
        })
    </script>

</body>
```

### v-bind 操作 style
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761307368310-43782599-9e48-48cc-a493-85cb898dd497.png)

```html
<style>
    .box {
        width: 200px;
        height: 200px;
        background-color: pink;
    }
</style>

<body>
    <div id="app">
        <div class="box" :style="{width: '400px', height: '400px'}"></div>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {},
            methods: {}
        })
    </script>

</body>
```

### 案例-进度条
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .progress {
            height: 25px;
            width: 400px;
            border-radius: 15px;
            background-color: #272425;
            border: 3px solid #272425;
            box-sizing: border-box;
            margin-bottom: 30px;
        }
        .inner {
            width: 50%;
            height: 20px;
            border-radius: 10px;
            background-color: #409eff;
            text-align: right;
            position: relative;
            box-sizing: border-box;
            transition: all 1s;
        }
        .inner span {
            position: absolute;
            right: -20px;
            bottom: -25px;
        }
    </style>
</head>
<body>
    <div id="app">
        <!-- 外层盒子 -->
        <div class="progress">
            <!-- 内层盒子 -->
            <div class="inner" :style="{width: percent + '%'}">
                <span>{{ percent }}%</span>
            </div>
        </div>
        <button @click="percent = 25">设置25%</button>
        <button @click="percent = 50">设置50%</button>
        <button @click="percent = 75">设置75%</button>
        <button @click="percent = 100">设置100%</button>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                percent: 30
            }
        })
    </script>

</body>
```

## v-for
1、作用：基于数据循环，多次渲染整个元素  ---> 数组、对象、数字......

2、语法：`v-for = "(item, index) in 数组"` 

index 下标， item 每一项

```html
<body>
    <div id="app">
        <ul>
            <li v-for="(item, index) in list">
                {{ item }} - {{ index }}
            </li>
        </ul>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                list: ['苹果', '香蕉', '橘子', '葡萄', '西瓜']
            }
        })
    </script>

</body>
```

案例：

```html
<body>
    <div id="app">
        <h1>我的书架</h1>
        <ul>
            <li v-for="(item, index) in booksList" :key="item.id">
                <!-- <span>{{ item.id }}</span> -->
                <span>{{ item.name }}</span>
                <span>{{ item.author }}</span>
                <button @click="del(item.id)">删除</button>
            </li>
        </ul>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                booksList: [
                    { id: 1, name: '《JavaScript高级程序设计》', author: 'Nicholas C. Zakas'},
                    { id: 2, name: '《JavaScript权威指南》', author: 'David Flanagan'},
                    { id: 3, name: '《你不知道的JavaScript（上、中、下卷）》', author: 'Kyle Simpson'},
                    { id: 4, name: '《JavaScript设计模式与开发实践》', author: 'Addy Osmani'}
                ]
            },
            methods: {
                del(id) {
                    // 通过id进行删除数组中的对应项 -> filter 不会改变原数组
                    // 只会根据条件，保留满足条件的对应项，得到一个新数组
                    this.booksList= this.booksList.filter(item => item.id !== id)
                }
            }
        })
    </script>

</body>
```



案例中，v-for 里面的 key

作用：**给列表项添加的唯一标识，便于 Vue 进行列表项的正确排序复用**

如果不加 key，v-for 的默认行为会尝试 <font style="color:rgb(190, 140, 4);">原地修改元素（就地复用）</font>

**注意点**：

1、key 只能是字符串 或 数字类型

2、有唯一性

3、推荐使用 id 作为 key，不推荐 index

## v-model
1、作用：给**表单元素**使用，**双向数据绑定** ----> 可以快速**获取或设置**表单元素内容

+ 数据变化  ---> 视图自动更新
+ 视图变化  ---> 数据自动更新

2、语法：`v-model='变量'`

```html
<body>
    <div id="app">
        账户： <input type="text" v-model="username"> <br>
        密码： <input type="password" v-model="password"> <br>
        <button @click="login">登录</button>
        <button @click="reset">重置</button>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                username: '',
                password: ''
            },
            methods: {
                login () {
                    console.log(this.username, this.password)
                },
                reset () {
                    this.username = ''
                    this.password = ''
                }
            }
        })
    </script>

</body>
```



### v-mode 应用于其他表单元素
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761370540558-34860a4f-e6db-4640-a5ea-805b7463a3f9.png)

```html
<style>
  textarea {
    display: block;
    width: 240px;
    height: 100px;
    margin: 10px 0;
  }
</style>

<body>
 
  <div id="app">
    <h3>小黑学习网</h3>
 
    姓名：
      <input type="text" v-model="name"> 
      <br><br>
 
    是否单身：
      <input type="checkbox" v-model="isSingle"> 
      <br><br>
 
    <!-- 
      前置理解：
        1. name:  给单选框加上 name 属性 可以分组 → 同一组互相会互斥
        2. value: 给单选框加上 value 属性，用于提交给后台的数据
      结合 Vue 使用 → v-model
    -->
    性别: 
      <input type="radio" name="gender" v-model="gender" value="1">男
      <input type="radio" name="gender" v-model="gender" value="2">女
      <br><br>
 
    <!-- 
      前置理解：
        1. option 需要设置 value 值，提交给后台
        2. select 的 value 值，关联了选中的 option 的 value 值
      结合 Vue 使用 → v-model
    -->
    所在城市:
      <select v-model="cityId">
        <option value="101">北京</option>
        <option value="102">上海</option>
        <option value="103">成都</option>
        <option value="104">南京</option>
      </select>
      <br><br>

    自我描述：
      <textarea v-model="desc"></textarea> 
 
    <button>立即注册</button>
  </div>

  <script src="./vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        name: '',
        isSingle: false,
        gender: '1',
        cityId: '102',
        desc: ''
      }
    })
  </script>
</body>
```

# 综合案例-小黑记事本
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761290710201-1af6d9ff-52b6-49c5-a36a-50ca31892cce.png)

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>记事本</title>
    <link rel="stylesheet" href="./css/index.css" />
</head>
<body>
    <!-- 主体区域 -->
    <section id="app">
        <!-- 输入框 -->
        <header class="header">
            <h1>小黑记事本</h1>
            <input v-model="todoName" placeholder="请输入任务" class="new-todo">
            <button @click="add" class="add">添加任务</button>
        </header>
        <!-- 列表区域 -->
        <section class="main">
            <ul class="todo-list">
                <li class="todo" v-for="(item, index) in list" :key="item.id">
                    <div class="view">
                        <span class="index">{{ index + 1 }}.</span> <label>{{ item.name }}</label>
                        <button @click="del(item.id)" class="destroy"></button>
                    </div>
                </li>
            </ul>
        </section>
        <!-- 统计和清空  如果没任务了，底部应该隐藏-->
        <footer class="footer" v-show="list.length > 0">
            <!-- 统计 -->
            <span class="todo-count">合 计: <strong> {{ list.length }} </strong></span>
            <!-- 清空 -->
            <button class="clear-completed" @click="clear">清空任务</button>
        </footer>
    </section>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        // 添加功能
        // 1. 通过 v-model 绑定输入框，实时获取表单元素的内容
        // 2. 点击按钮，进行新增，往数组最前面加入数据 unshift
        const app = new Vue({
            el: '#app',
            data: {
                todoName: '',
                list: [
                    {id: 1, name: '跑步'},
                    {id: 2, name: '游泳'},
                    {id: 3, name: '羽毛球'},
                ],
            },
            methods: {
                del (id) {
                    this.list = this.list.filter(item => item.id != id)
                },
                add () {
                    if (this.todoName.trim() === '') {
                        alert('请输入任务名称')
                        return
                    }

                    this.list.unshift({
                        id: +new Date(),
                        name: this.todoName
                    })

                    this.todoName = ''
                },
                clear () {
                    this.list = []
                }
            }
        })
    </script>

</body>
```

```css
html,
body {
  margin: 0;
  padding: 0;
}
body {
  background: #fff;
}
button {
  margin: 0;
  padding: 0;
  border: 0;
  background: none;
  font-size: 100%;
  vertical-align: baseline;
  font-family: inherit;
  font-weight: inherit;
  color: inherit;
  -webkit-appearance: none;
  appearance: none;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font: 14px 'Helvetica Neue', Helvetica, Arial, sans-serif;
  line-height: 1.4em;
  background: #f5f5f5;
  color: #4d4d4d;
  min-width: 230px;
  max-width: 550px;
  margin: 0 auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-weight: 300;
}

:focus {
  outline: 0;
}

.hidden {
  display: none;
}

#app {
  background: #fff;
  margin: 180px 0 40px 0;
  padding: 15px;
  position: relative;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
#app .header input {
  border: 2px solid rgba(175, 47, 47, 0.8);
  border-radius: 10px;
}
#app .add {
  position: absolute;
  right: 15px;
  top: 15px;
  height: 68px;
  width: 140px;
  text-align: center;
  background-color: rgba(175, 47, 47, 0.8);
  color: #fff;
  cursor: pointer;
  font-size: 18px;
  border-radius: 0 10px 10px 0;
}

#app input::-webkit-input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

#app input::-moz-placeholder {
  font-style: italic;
  font-weight: 300;
  color: #e6e6e6;
}

#app input::input-placeholder {
  font-style: italic;
  font-weight: 300;
  color: gray;
}

#app h1 {
  position: absolute;
  top: -120px;
  width: 100%;
  left: 50%;
  transform: translateX(-50%);
  font-size: 60px;
  font-weight: 100;
  text-align: center;
  color: rgba(175, 47, 47, 0.8);
  -webkit-text-rendering: optimizeLegibility;
  -moz-text-rendering: optimizeLegibility;
  text-rendering: optimizeLegibility;
}

.new-todo,
.edit {
  position: relative;
  margin: 0;
  width: 100%;
  font-size: 24px;
  font-family: inherit;
  font-weight: inherit;
  line-height: 1.4em;
  border: 0;
  color: inherit;
  padding: 6px;
  box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.new-todo {
  padding: 16px;
  border: none;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
}

.main {
  position: relative;
  z-index: 2;
}

.todo-list {
  margin: 0;
  padding: 0;
  list-style: none;
  overflow: hidden;
}

.todo-list li {
  position: relative;
  font-size: 24px;
  height: 60px;
  box-sizing: border-box;
  border-bottom: 1px solid #e6e6e6;
}

.todo-list li:last-child {
  border-bottom: none;
}

.todo-list .view .index {
  position: absolute;
  color: gray;
  left: 10px;
  top: 20px;
  font-size: 22px;
}

.todo-list li .toggle {
  text-align: center;
  width: 40px;
  /* auto, since non-WebKit browsers doesn't support input styling */
  height: auto;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto 0;
  border: none; /* Mobile Safari */
  -webkit-appearance: none;
  appearance: none;
}

.todo-list li .toggle {
  opacity: 0;
}

.todo-list li .toggle + label {
  /*
		Firefox requires `#` to be escaped - https://bugzilla.mozilla.org/show_bug.cgi?id=922433
		IE and Edge requires *everything* to be escaped to render, so we do that instead of just the `#` - https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/7157459/
	*/
  background-image: url('data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%22-10%20-18%20100%20135%22%3E%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2250%22%20fill%3D%22none%22%20stroke%3D%22%23ededed%22%20stroke-width%3D%223%22/%3E%3C/svg%3E');
  background-repeat: no-repeat;
  background-position: center left;
}

.todo-list li .toggle:checked + label {
  background-image: url('data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%22-10%20-18%20100%20135%22%3E%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2250%22%20fill%3D%22none%22%20stroke%3D%22%23bddad5%22%20stroke-width%3D%223%22/%3E%3Cpath%20fill%3D%22%235dc2af%22%20d%3D%22M72%2025L42%2071%2027%2056l-4%204%2020%2020%2034-52z%22/%3E%3C/svg%3E');
}

.todo-list li label {
  word-break: break-all;
  padding: 15px 15px 15px 60px;
  display: block;
  line-height: 1.2;
  transition: color 0.4s;
}

.todo-list li.completed label {
  color: #d9d9d9;
  text-decoration: line-through;
}

.todo-list li .destroy {
  display: none;
  position: absolute;
  top: 0;
  right: 10px;
  bottom: 0;
  width: 40px;
  height: 40px;
  margin: auto 0;
  font-size: 30px;
  color: #cc9a9a;
  margin-bottom: 11px;
  transition: color 0.2s ease-out;
}

.todo-list li .destroy:hover {
  color: #af5b5e;
}

.todo-list li .destroy:after {
  content: '×';
}

.todo-list li:hover .destroy {
  display: block;
}

.todo-list li .edit {
  display: none;
}

.todo-list li.editing:last-child {
  margin-bottom: -1px;
}

.footer {
  color: #777;
  padding: 10px 15px;
  height: 20px;
  text-align: center;
  border-top: 1px solid #e6e6e6;
}

.footer:before {
  content: '';
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  height: 50px;
  overflow: hidden;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 8px 0 -3px #f6f6f6,
    0 9px 1px -3px rgba(0, 0, 0, 0.2), 0 16px 0 -6px #f6f6f6,
    0 17px 2px -6px rgba(0, 0, 0, 0.2);
}

.todo-count {
  float: left;
  text-align: left;
}

.todo-count strong {
  font-weight: 300;
}

.filters {
  margin: 0;
  padding: 0;
  list-style: none;
  position: absolute;
  right: 0;
  left: 0;
}

.filters li {
  display: inline;
}

.filters li a {
  color: inherit;
  margin: 3px;
  padding: 3px 7px;
  text-decoration: none;
  border: 1px solid transparent;
  border-radius: 3px;
}

.filters li a:hover {
  border-color: rgba(175, 47, 47, 0.1);
}

.filters li a.selected {
  border-color: rgba(175, 47, 47, 0.2);
}

.clear-completed,
html .clear-completed:active {
  float: right;
  position: relative;
  line-height: 20px;
  text-decoration: none;
  cursor: pointer;
}

.clear-completed:hover {
  text-decoration: underline;
}

.info {
  margin: 50px auto 0;
  color: #bfbfbf;
  font-size: 15px;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5);
  text-align: center;
}

.info p {
  line-height: 1;
}

.info a {
  color: inherit;
  text-decoration: none;
  font-weight: 400;
}

.info a:hover {
  text-decoration: underline;
}

/*
	Hack to remove background from Mobile Safari.
	Can't use it globally since it destroys checkboxes in Firefox
*/
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  .toggle-all,
  .todo-list li .toggle {
    background: none;
  }

  .todo-list li .toggle {
    height: 40px;
  }
}

@media (max-width: 430px) {
  .footer {
    height: 50px;
  }

  .filters {
    bottom: 10px;
  }
}

```

# 指令修饰符
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761294915253-76a0f888-591f-4808-af71-471ad45f3959.png)

在小黑记事本案例上，对输入框进行 `@keyup.enter="add"`进行回车确认添加任务

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .father {
            width: 200px;
            height: 100px;
            background-color: pink;
        }

        .son {
            width: 100px;
            height: 50px;
            background-color: skyblue;
        }
    </style>
</head>
<body>
    <div id="app">
        <h3>v-model修饰符  .trim .number</h3>
        <!-- .trim  去掉输入框的左右两边的空格 -->
        姓名： <input type="text" v-model.trim="name">  <br>
        <!-- .number  将输入的字符串转为数字 -->
        年纪： <input type="text" v-model.number="age">
        <hr>

        <h3>@事件名.stop   ->    阻止冒泡</h3>
        <div class="father" @click="fatherFn">
            <!-- @click.stop  阻止冒泡 -->
            <div class="son" @click.stop="sonFn">子组件</div>
        </div>
        <hr>

        <h3>@事件名.prevent   ->   阻止默认行为</h3>
        <a href="https://www.baidu.com" @click.prevent>阻止默认行为</a>
    </div>

    <!-- 引入的是开发版本包  包含完整的注释和警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                name: '',
                age: ''
            },
            methods: {
                fatherFn() {
                    console.log('父组件')
                },
                sonFn() {
                    console.log('子组件')
                }

            }
        })
    </script>

</body>
```

# 计算属性
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761372074671-38c006e0-7867-4215-b91b-e037e0933af0.png)

```html
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    table {
      border: 1px solid #000;
      text-align: center;
      width: 240px;
    }
    th,td {
      border: 1px solid #000;
    }
    h3 {
      position: relative;
    }
  </style>
</head>
<body>
 
  <div id="app">
    <h3>小黑的礼物清单</h3>
    <table>
      <tr>
        <th>名字</th>
        <th>数量</th>
      </tr>
      <tr v-for="(item, index) in list" :key="item.id">
        <td>{{ item.name }}</td>
        <td>{{ item.num }}个</td>
      </tr>
    </table>
 
    <!-- 目标：统计求和，求得礼物总数 -->
    <p>礼物总数：{{ totalCount }} 个</p>
  </div>
  <script src="./vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        // 现有的数据
        list: [
          { id: 1, name: '篮球', num: 1 },
          { id: 2, name: '玩具', num: 2 },
          { id: 3, name: '铅笔', num: 5 },
        ]
      },
      computed: {
        totalCount() {
            // 基于现有的数据，编写求值逻辑
            // 计算属性函数内部，可以直接通过 this 访问 app实例
            // 对this.list数组里面的num进行求和  reduce
            let total = this.list.reduce((sum, item) => sum + item.num, 0)
            return total
        }
      }
    })
  </script>
</body>
```

代码中使用了 js 中数组的 `reduce()`方法，对 list 中每个对象进行遍历

初始值为第二个参数 0

对于每个元素 item，将它的 num 属性值累加到 sum 中

## computed 计算属性 VS methods 方法
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761376136339-ab6e159a-4ed5-4b81-abb6-8c9de7525ae8.png)

建立多个使用计算属性的组件，然后在计算属性中加入一个 console.log()，会发现只执行了一次；

如果是用的是 methods 的话，会运行多次

## 计算属性的完整写法
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761376427342-4237aadc-5948-418a-bffa-ce26c0a39cea.png)

```html
<body>
 
  <div id="app">
    姓：<input type="text" v-model="firstName"><br>
    名：<input type="text" v-model="lastName"><br>
    <p>姓名：{{ fullName }}</p>
    <button @click="changeName">修改姓名</button>
  </div>
  <script src="./vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        firstName: '张',
        lastName: '三'
      },
      computed: {
        fullName: {
            get() {
                return this.firstName + this.lastName
            },
            set(value) {
                this.firstName = value.slice(0, 1)
                this.lastName = value.slice(1)
            }
        }
      },
      methods: {
        changeName() {
            this.fullName = '陈平安'
        }
      }
    })
  </script>
</body>
```

# 综合案例-成绩案例
```html
<body>
    <div id="app" class="score-case">
      <div class="table">
        <table>
          <thead>
            <tr>
              <th>编号</th>
              <th>科目</th>
              <th>成绩</th>
              <th>操作</th>
            </tr>
          </thead>
          <tbody v-if="list.length > 0 ">
            <tr v-for="(item, index) in list" :key="item.id">
              <td>{{ index + 1 }}</td>
              <td>{{ item.subject }}</td>
              <td :class="{red: item.score < 60}">{{ item.score }}</td>
              <td><a href="#" @click.prevent="del(item.id)">删除</a></td>
            </tr>
          </tbody>
          <tbody v-else>
            <tr>
              <td colspan="5">
                <span class="none">暂无数据</span>
              </td>
            </tr>
          </tbody>
 
          <tfoot>
            <tr>
              <td colspan="5">
                <span>总分：{{ totalScore }}</span>
                <span style="margin-left: 50px">平均分：{{ averageScore }}</span>
              </td>
            </tr>
          </tfoot>
        </table>
      </div>
      <div class="form">
        <div class="form-item">
          <div class="label">科目：</div>
          <div class="input">
            <input
              type="text"
              placeholder="请输入科目"
              v-model="subject"
            />
          </div>
        </div>
        <div class="form-item">
          <div class="label">分数：</div>
          <div class="input">
            <input
              type="text"
              placeholder="请输入分数"
              v-model="score"
            />
          </div>
        </div>
        <div class="form-item">
          <div class="label"></div>
          <div class="input">
            <button class="submit" @click="add">添加</button>
          </div>
        </div>
      </div>
    </div>

    <script src="./vue.js"></script>
 
    <script>
      const app = new Vue({
        el: '#app',
        data: {
          list: [
            { id: 1, subject: '语文', score: 20 },
            { id: 7, subject: '数学', score: 99 },
            { id: 12, subject: '英语', score: 70 },
          ],
          subject: '',
          score: ''
        },
        methods: {
            add () {
                this.list.unshift({
                    id: +new Date(),
                    subject: this.subject,
                    score: +this.score
                })
                this.subject = ''
                this.score = ''
            },
            del (id) {
                this.list = this.list.filter(item => item.id !== id)
            }
        },
        computed: {
            totalScore () {
                return this.list.reduce((sum, item) => sum + item.score, 0)
            },
            averageScore () {
                if (this.list.length === 0) return 0
                return (this.totalScore / this.list.length).toFixed(2)
            }
        }
      })
    </script>
  </body>
```

```css
.score-case {
  width: 1000px;
  margin: 50px auto;
  display: flex;
}
.score-case .table {
  flex: 4;
}
.score-case .table table {
  width: 100%;
  border-spacing: 0;
  border-top: 1px solid #ccc;
  border-left: 1px solid #ccc;
}
.score-case .table table th {
  background: #f5f5f5;
}
.score-case .table table tr:hover td {
  background: #f5f5f5;
}
.score-case .table table td,
.score-case .table table th {
  border-bottom: 1px solid #ccc;
  border-right: 1px solid #ccc;
  text-align: center;
  padding: 10px;
}
.score-case .table table td.red,
.score-case .table table th.red {
  color: red;
}
.score-case .table .none {
  height: 100px;
  line-height: 100px;
  color: #999;
}
.score-case .form {
  flex: 1;
  padding: 20px;
}
.score-case .form .form-item {
  display: flex;
  margin-bottom: 20px;
  align-items: center;
}
.score-case .form .form-item .label {
  width: 60px;
  text-align: right;
  font-size: 14px;
}
.score-case .form .form-item .input {
  flex: 1;
}
.score-case .form .form-item input,
.score-case .form .form-item select {
  appearance: none;
  outline: none;
  border: 1px solid #ccc;
  width: 200px;
  height: 40px;
  box-sizing: border-box;
  padding: 10px;
  color: #666;
}
.score-case .form .form-item input::placeholder {
  color: #666;
}
.score-case .form .form-item .cancel,
.score-case .form .form-item .submit {
  appearance: none;
  outline: none;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 10px;
  margin-right: 10px;
  font-size: 12px;
  background: #ccc;
}
.score-case .form .form-item .submit {
  border-color: #069;
  background: #069;
  color: #fff;
}
```

# watch 侦听器（监视器）
![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761379658210-a2f488d5-489c-45c1-9946-3b7a177be6b3.png)

```html
 <body>
    <div id="app">
      <!-- 条件选择框 -->
      <div class="query">
        <span>翻译成的语言：</span>
        <select>
          <option value="italy">意大利</option>
          <option value="english">英语</option>
          <option value="german">德语</option>
        </select>
      </div>
 
      <!-- 翻译框 -->
      <div class="box">
        <div class="input-wrap">
          <textarea v-model="obj.words"></textarea>
          <span><i>⌨️</i>文档翻译</span>
        </div>
        <div class="output-wrap">
          <div class="transbox">{{ result }}</div>
        </div>
      </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/axios@1.6.8/dist/axios.min.js"></script>
    <script>
      // 接口地址：https://applet-base-api-t.itheima.net/api/translate
      // 请求方式：get
      // 请求参数：
      // （1）words：需要被翻译的文本（必传）
      // （2）lang： 需要被翻译成的语言（可选）默认值-意大利
      // -----------------------------------------------
       
      const app = new Vue({
        el: '#app',
        data: {
        //   words: ''
            obj: {
                words: ''
            },
            result: '',  // 翻译结果
            timer: null  // 定时器标识
        },
        // 具体讲解：(1) watch语法 (2) 具体业务实现
        watch: {
            // words (newValue) {
            //     console.log("对象改变了", newValue)
            // }

            // async 'obj.words' (newValue) {
            //     const res = await axios({
            //         url: 'https://applet-base-api-t.itheima.net/api/translate',
            //         params: {
            //             words: newValue
            //         }
            //     })
            //     this.result = res.data.data
            //     // console.log(res.data.data)
            // }

            // 防抖: 延迟执行 ---> 干啥事先等一等，延迟一会，一段时间没有再次触发，再执行
            'obj.words' (newValue) {
                clearTimeout(this.timer)
                this.timer = setTimeout(async () => {
                    const res = await axios({
                        url: 'https://applet-base-api-t.itheima.net/api/translate',
                        params: {
                            words: newValue
                        }
                    })
                    this.result = res.data.data
                }, 300)
                
            }
        }
      })
    </script>
  </body>
```

```html
<body>
    <div id="app">
      <!-- 条件选择框 -->
      <div class="query">
        <span>翻译成的语言：</span>
        <select v-model="obj.lang">
          <option value="italy">意大利</option>
          <option value="english">英语</option>
          <option value="german">德语</option>
        </select>
      </div>
 
      <!-- 翻译框 -->
      <div class="box">
        <div class="input-wrap">
          <textarea v-model="obj.words"></textarea>
          <span><i>⌨️</i>文档翻译</span>
        </div>
        <div class="output-wrap">
          <div class="transbox">{{ result }}</div>
        </div>
      </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/axios@1.6.8/dist/axios.min.js"></script>
    <script>
      // 接口地址：https://applet-base-api-t.itheima.net/api/translate
      // 请求方式：get
      // 请求参数：
      // （1）words：需要被翻译的文本（必传）
      // （2）lang： 需要被翻译成的语言（可选）默认值-意大利
      // -----------------------------------------------
       
      const app = new Vue({
        el: '#app',
        data: {
            obj: {
                words: '小黑',
                lang: 'english'
            },
            result: '',  // 翻译结果
            timer: null  // 定时器标识
        },
        // 具体讲解：(1) watch语法 (2) 具体业务实现
        watch: {
            obj: {
                deep: true,  // 深度监听
                immediate: true, // 立即执行
                handler (newValue) {
                    clearTimeout(this.timer)
                    this.timer = setTimeout(async () => {
                        // 发起请求
                        const res = await axios.get('https://applet-base-api-t.itheima.net/api/translate', {
                            params: newValue
                        })
                        this.result = res.data.data
                    }, 300)
                }
            }
        }
      })
    </script>
  </body>
```

```css
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-size: 18px;
      }
      #app {
        padding: 10px 20px;
      }
      .query {
        margin: 10px 0;
      }
      .box {
        display: flex;
      }
      textarea {
        width: 300px;
        height: 160px;
        font-size: 18px;
        border: 1px solid #dedede;
        outline: none;
        resize: none;
        padding: 10px;
      }
      textarea:hover {
        border: 1px solid #1589f5;
      }
      .transbox {
        width: 300px;
        height: 160px;
        background-color: #f0f0f0;
        padding: 10px;
        border: none;
      }
      .tip-box {
        width: 300px;
        height: 25px;
        line-height: 25px;
        display: flex;
      }
      .tip-box span {
        flex: 1;
        text-align: center;
      }
      .query span {
        font-size: 18px;
      }
 
      .input-wrap {
        position: relative;
      }
      .input-wrap span {
        position: absolute;
        right: 15px;
        bottom: 15px;
        font-size: 12px;
      }
      .input-wrap i {
        font-size: 20px;
        font-style: normal;
      }
    </style>
```

# 综合案例-水果购物车![](https://cdn.nlark.com/yuque/0/2025/png/35081558/1761382691129-66686172-7827-4d3a-9599-1cfd1966e59a.png)
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="./css/inputnumber.css" />
    <link rel="stylesheet" href="./css/index.css" />
    <title>购物车</title>
  </head>
  <body>
    <div class="app-container" id="app">
      <!-- 顶部banner -->
      <div class="banner-box"><img src="http://autumnfish.cn/static/fruit.jpg" alt="" /></div>
      <!-- 面包屑 -->
      <div class="breadcrumb">
        <span>🏠</span>
        /
        <span>购物车</span>
      </div>
      <!-- 购物车主体 -->
      <div class="main" v-if="fruitList.length > 0">
        <div class="table">
          <!-- 头部 -->
          <div class="thead">
            <div class="tr">
              <div class="th">选中</div>
              <div class="th th-pic">图片</div>
              <div class="th">单价</div>
              <div class="th num-th">个数</div>
              <div class="th">小计</div>
              <div class="th">操作</div>
            </div>
          </div>
          <!-- 身体 -->
          <div class="tbody">
            <div v-for="(item, index) in fruitList" :key="item.id" class="tr" :class="{active: item.isChecked}">
              <div class="td"><input type="checkbox" v-model="item.isChecked" /></div>
              <div class="td"><img :src="item.icon" alt="" /></div>
              <div class="td">{{ item.price }}</div>
              <div class="td">
                <div class="my-input-number">
                  <button :disabled="item.num <= 1" class="decrease" @click="sub(item.id)"> - </button>
                  <span class="my-input__inner">{{ item.num }}</span>
                  <button class="increase" @click="add(item.id)"> + </button>
                </div>
              </div>
              <div class="td">{{ item.price * item.num }}</div>
              <div class="td"><button @click="del(item.id)">删除</button></div>
            </div>
 
          </div>
        </div>
        <!-- 底部 -->
        <div class="bottom">
          <!-- 全选 -->
          <label class="check-all">
            <input type="checkbox" v-model="isAll" />
            全选
          </label>
          <div class="right-box">
            <!-- 所有商品总价 -->
            <span class="price-box">总价  :  ¥ <span class="price">{{ totalPrice }}</span></span>
            <!-- 结算按钮 -->
            <button class="pay">结算( {{ totalCount}} )</button>
          </div>
        </div>
      </div>
      <!-- 空车 -->
      <div class="empty" v-else>🛒空空如也</div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <script>
    const defaultArr = [
            {
              id: 1,
              icon: './images/火龙果.png',
              isChecked: true,
              num: 2,
              price: 6,
            },
            {
              id: 2,
              icon: './images/荔枝.png',
              isChecked: false,
              num: 7,
              price: 20,
            },
            {
              id: 3,
              icon: './images/榴莲.png',
              isChecked: false,
              num: 3,
              price: 40,
            },
            {
              id: 4,
              icon: './images/鸭梨.png',
              isChecked: true,
              num: 10,
              price: 3,
            },
            {
              id: 5,
              icon: './images/樱桃.png',
              isChecked: false,
              num: 20,
              price: 34,
            },
          ]
    const app = new Vue({
        el: '#app',
        data: {
          // 水果列表
          fruitList: JSON.parse(localStorage.getItem('list')) || defaultArr
        },
        methods: {
            del(id) {
                this.fruitList = this.fruitList.filter(item => item.id !== id)
            },
            add(id) {
                // 根据id找到数组中的对应项 --- > find
                const fruit = this.fruitList.find(item => item.id === id)
                // 操作num的值
                fruit.num++
            },
            sub(id) {
                const fruit = this.fruitList.find(item => item.id === id)
                fruit.num--
            }
        },
        computed: {
            isAll: {
                get() {
                    // 必须所有的小选框全选了，大选框才选中 ---> every
                    return this.fruitList.every(item => item.isChecked)
                },
                set(value) {
                    // 根据大选框的选中状态，设置所有小选框的状态
                    this.fruitList.forEach(item => item.isChecked = value)
                }
            },
            totalCount () {
                return this.fruitList.reduce((sum, item) => {
                    if (item.isChecked) {
                        return sum + item.num
                    } else {
                        return sum
                    }
                }, 0)
            },
            totalPrice () {
                return this.fruitList.reduce((sum, item) => {
                    if (item.isChecked) {
                        return sum + item.num * item.price
                    } else {
                        return sum
                    }
                }, 0)
            }
        },
        watch: {
            fruitList: {
                deep: true,
                handler(newValue) {
                    // 需要将变化后的newValue保存到localStorage中，也就是本地，不过要转为json
                    localStorage.setItem('list', JSON.stringify(newValue))
                }
            }
        }
      })
    </script>
  </body>
</html>
```

