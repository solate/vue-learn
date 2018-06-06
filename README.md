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

全局变量： app.$data.xx



## 参考