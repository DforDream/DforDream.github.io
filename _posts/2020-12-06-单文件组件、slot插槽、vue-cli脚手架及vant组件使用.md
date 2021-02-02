# 单文件组件、slot插槽、vue-cli脚手架及vant组件使用

## 单文件组件

- 一个组件即为一个.vue文件
- 浏览器不能解析.vue文件，所以要先将.vue文件转换为js文件在执行
- 通过vue-cli脚手架可以实现vue的单文件组件



## slot插槽

- 单文件组件是可以复用的，而写死组件内容与组件复用相违背，而slot插槽可以完美解决该问题
- 父组件内import 引入组件，components声明组件，父组件在引入的子组件标签内写入该页面需要的子组件内容，子组件内通过slot插槽接收，形成组件的复用功能
- 具名插槽父组件slot=“haha”声明 ，子组件内name=“haha”接收，可以将接收到的内容放在固定的位置
- 通过this.$parent和this.$children查看该组件的父组件和子组件
- 如果slot插槽内放入组件，则该组件会成为拥有slot插槽组件的子组件，可以通过this.$parent和this.$children查看

## vue-cli脚手架

- 安装vue-cli脚手架

- ```bash
  npm install -g @vue/cli
  ```

- 查看 vue-cli版本

- ```bash
  vue --version / -V
  ```

- 创建项目

- ```bash
  vue create myapp
  ```

- 项目选择配置自行选择

## vant-ui（移动端）

- npm安装vant依赖

- ```bash
  npm i vant -S
  ```

- 引入方式推荐自动按需 引入组件

- 先安装自动按需引入的依赖

- ```bash
  npm i babel-plugin-import -D
  ```

- 在babel.config.js文件中 加入如下配置

- ```js
  module.exports = {
    plugins: [
      ['import', {
        libraryName: 'vant',
        libraryDirectory: 'es',
        style: true
      }, 'vant']
    ]
  };
  ```

- 接着在需要引入的组件内

- ```js
  import Vue from 'vue'
  import { Button,Swipe } from 'vant';
  Vue.use(Button).use(Swipe)
  ```

- 现在可以在该组件内使用引入的Vant组件了