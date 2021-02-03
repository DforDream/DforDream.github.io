# 封装组件案例、slot、keep-alive及新增生命周期函数、component动态组件 、组件异步加载、errorCaptured生命周期函数 

## 常见组件库（pc端）

- element ui
- ant design vue
- mint-ui 不再维护，不建议使用

## element ui 使用

- 安装element-ui

- ```bash
  npm i element-ui -S
  ```

- 借助 [babel-plugin-component](https://github.com/QingWei-Li/babel-plugin-component)，我们可以只引入需要的组件，以达到减小项目体积的目的。

- 首先，安装 babel-plugin-component：

- ```bash
  npm install babel-plugin-component -D
  ```

- 增加babel.config.js配置文件

- ```js
   "plugins": [
      [
        "component",
        {
          "libraryName": "element-ui",
          "styleLibraryName": "theme-chalk"
        }
      ]
    ]
  ```

- 之后就可以按需引入需要的组件了

## slot作用域及动态名字插槽

- 看文档
- slot实现组件的封装实例了解实现过程

## keep-alive

- 在keep-alive内部的组件中，一旦检测到需要销毁，keep-alive会将该组件缓存起来，阻止销毁，当你下一次需要创建该组件时，阻止创建，直接使用缓存

## keep-alive新增生命周期函数

- activated 被keep-alive缓存的组件被激活时调用
- deactivated 被keep-alive缓存的组件停用时调用
- 这两个生命周期函数再服务器渲染期间不被调用

## component动态组件

- ```html
  <component :is=""></component>
  ```

- 动态组件显示什么组件，取决于is的属性是什么组件的名字，就显示什么组件

## 异步加载组件

- 同步加载组件

- ```js
  import Home from '组件地址'
  export default {
      components: {
          Home
  	}
  }
  ```

- 同步加载组件，不管组件有没有使用到（显示），组件都会加载造成资源的浪费

- 异步加载组件（组件需要显示时，才加载组件，提升页面首次进入的性能）

- ```js
  export default {
      components: {
          Home: () => import('组件地址')
          Home: () => import(/* webpackChunkName:"home" */'组件地址')
        // webpackChunkName:"home"  打包生成的js生成 再home中，便于后期维护和管理
  	}
  }
  ```
## 捕获异常的生命周期函数errorCaptured

  - 当捕获一个来自子孙组件的错误时被调用
  - 此钩子会收到三个参数：错误对象、发生错误的组件实例以及一个包含错误来源信息的字符串。此钩子可以返回 `false` 以阻止该错误继续向上传播。
  - 开发过程中只需要再根节点写一个errorCaptured生命周期函数，即可控制所有的组件报错
  - 该生命周期函数是用来收集错误并提交到后台
  - 定义一个error组件，将errorCaptured生命周期函数定义再组件内，其他组件引入该组件，将error组件包裹组要收集错误的组件，即可接收到组件错误