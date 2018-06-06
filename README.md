# vue-learn

学习vue, 记录笔记

代码放在：[vue-learn](https://github.com/solate/vue-learn)


## Hello World

1. 创建vue 实例
2. el 表示 vue 管理的区域
3. data 表示管理区域内的数据
4. {{内容}} 进行绑定


## TODOList

### v-for

循环遍历 data中 list 的数据

### v-on

绑定事件, 放在methods 内

todoList 中在按钮中绑定提交事件

```
简写: v-on:click => @click
```


### v-model

数据的双向绑定

输入框数据发生变化, 则data中数据也发送变化. data 中定义变量发送变化则页面数据也跟着变

### v-bind

向组件传入绑定值，

props 组件接受那些值

```
简写: v-bind:index => :index
```

### v-if

条件判断语句

### v-text

将值输出成文本

### v-html

将值输出成html


## MVVM 模式

### 传统MVP 设计模式

主要面向DOM进行操作

View <=> Presenter <=> Model

View : 视图
Presenter : 控制器, 大量的DOM操作

### MVVM

View <=> ViewModel <=> Model

ViewModel : DOM Listeners , Data Bindings.  Vue 内置的, 我们并不需要关注

主要面向数据进行操作


## 前端组件化

可以将页面进行切分, 组件就是界面中的一小块。

父组件使用v-bind 向子组件传值，子组件使用 this.$emit 向父组件触发事件，父组件监听这个时间, 并接受事件的参数


## Vue 实例

全局变量： app.$data.xx

以$开头的都是这个实例的**实例属性**和**实例方法**

app.$destroy() //将这个实例销毁，销毁后再修改值,页面不会发送变化

### 生命周期钩子

生命周期函数就是vue实例在某个时间点自动执行的函数

1. init : 初始化事件和生命周期相关部分
2. beforeCreate()
3. init : 处理外部注入和 双向绑定等
4. created() //初始化完成
5. has el : 是否有元素绑定，没有执行 vm.$mount(el)
6. has template : 是否有模版, 有模版就执行模版，没有就把el的内容当成模版
7. beforeMount() //模版和数据即将挂载的一瞬间, 未渲染页面
8. vm.$el replace el 模版和数据进行挂载
9. mounted() //已渲染页面
10. mount 挂载
11. 当 data 中数据有变化 (app.$data.seen = false)
12. beforeUpdate() //渲染之前
13. DOM 重新开始渲染
14. updated()  //渲染之后
15. 当 vm.$destroy() 被调用,下面开始执行 (app.$destroy())
16. beforeDestroy() //销毁之前
17. 销毁
18. destroyed() //销毁之后

### 模版语法

1. 插值表达式 : {{data}}
2. v-text
3. v-html


## 参考