## vue-router

- 新增文件夹router，创建index.js

- ```js
  import Vue from 'vue' // 引入vue
  import Router from 'vue-router' // 引入vue-router
  // 页面引入
  import Home from '../pages/Home'
  import Discover from '../pages/Discover'
  import Setting from '../pages/Setting'
  Vue.use(Router) // 使用vue-router
  // 路由配置表
  const routes = [
      // 一个对象,就是一个路由的配置项
      {
          // 命名路由，名字需要唯一
          name: 'home'
          path: '/home', // 路由跳转的地址
          component: Home, // 跳转地址后显示的组件
          // 配置子路由
        children: [
              {
                  path: 'detail', // 子路由不能设置/
                  component: Detail
              }
          ]
      },
      {
          path: '/discover',
          component: Discover
      },
      {
          path: '/setting',
          component: Setting
      },
      // 路由配置的路由表，是从上 往下加载，如果 匹配到了就直接使用，不再向下执行
      {
          // 重定向首页（匹配其他所有的地址跳转到home页面）
          path: '*',
          redirect: '/home'
       }
  ]
  // 创建路由对象
  const router = new Router({
      routes
  })
  // 导出路由对象
  export default router
  ```
  
- main.js中使用导出的router

- ```js
  import Vue from 'vue'
  import App from './App.vue'
  import router from './router'  // 引入路由对象
  Vue.config.productionTip = false
  new Vue({
    render: h => h(App),
    // 通过混入的方式挂载到该实例的所有实例和组件上
    router // Vue实例配置该router配置项，整个vue实例都可以通过this.$router访问该路由对象 该路由可以管理这个实例
  }).$mount('#app')
  ```
  
- App.vue中使用配置好的路由(router-link标签跳转路由)

- ```js
  <template>
    <div id="app">
      <h1>app</h1>
      <!-- 路由跳转后组件会显示再 router-view标签内 -->
      <router-view></router-view>
  
      <!-- <nav>
        <a href="#/home">首页</a>
        <a href="#/discover">发现</a>
        <a href="#/setting">设置</a>
      </nav> -->
  
    <nav>
      <!-- 标签切换路由 -->
      <!-- to 路由跳转的地址 tag 需要显示的标签是什么默认为a标签 点击的标签会添加router-link-active类名 -->
      <router-link to="/home" tag="li">首页</router-link>
      <router-link to="/discover">发现</router-link>
      <router-link to="/setting">设置</router-link>
    </nav>
  	
  
    </div>
  </template>
  
  <script>
  export default {
    // 路由（vue-rotuer）：统一管理页面切换
  }
  </script>
  
  // scoped style标签内的样式只作用再该组件内
  <style scoped>
  .router-link-active {
    color: red;
  }
  </style>
  ```
  
- js跳转路由

- ```js
  <div @click="handleClick">首页</div>
  
  methods: {
        handleClick(){
          //   操作路由对象 js操作路由
            this.$router.push('/home') // 将页面加入history中可以点击浏览器的后退按钮回到前一个页面
            this.$router.back() // 操作路由对象返回上一个页面
            this.$router.replace('/home') // 跳转页面，不加入history中，无法通过浏览器的后退按钮回退到前一个页面
            this.$router.forward() // 前进，回到前一个退出的页面
            this.$router.go(num) // 正数前进，负数后退
        }
    }
  ```

- 使用router-link标签切换导航叫做声明式导航

- 使用js中的$router切换导航叫做编程式导航

- 命名路由的跳转(命名唯一)

- ```js
  <router-link :to="{name:'home',params:{id:''},query:{}}" tag="li">设置</router-link>
  // name 配置跳转路由的名字
  // params 配置后面需要的动态路由
  // query配置路由后的请求字段
  ```

- 

  

