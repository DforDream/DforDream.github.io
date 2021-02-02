### props类型检查

1. 使用插件prop-types `npm install prop-types -S`

2. 组件内检查props

   ```js
   Child.propTypes = {
     // count: PropTypes.number.isRequired
     count: PropTypes.oneOf([1, 2, 3]),
     onChange:PropTypes.func.isRequired
   }
   ```

### Hooks

1. React 16.8开始增加了Hooks新特性，它允许函数式组件使用生命周期、ref、context和state等特性，可以在保证函数式组件性能的同时不影响React特性的使用
2. Hooks 实际上就是一组api，帮助我们使用React的固有特性
3. useState
   - 组件内引入`import {useState} from 'react'`
   - 语法：`const [count, setCount] = useState(1);`
   - 原则：不要直接修改count，使用setCount修改count
   - 特点：使用setCount修改count后，会触发diff算法，重新渲染视图
4. useEffect
   - 组件内引入`import {useEffect} from 'react'`
   - 在函数式组件内，如果要使用副作用(调接口、DOM、开启定时器、建立长连接等)，必须使用生命周期的特性，useEffect 可以帮助我们模拟出生命周期的特性
   - 语法： `useEffect(() => { return () => {} }, []);`写在回调函数内的代码，相当于在生命周期`componentDidMount()`中的代码，回调函数中的`return `函数相当于`componentWillUnmount()`,第二个数组参数为空，则该副作用只会执行一次，如数组内的参数为`count`则每次count更新，该副作用内的回调函数就会被执行一次
   - 如果在副作用中没有需要清除的任务，`则return可以为undefined`
   - `useEffect(() => { return () => {} });`没有第二个参数，则该副作用只要有数据更新就会执行

### react-router

1. react路由有三个库：react-router（核心库），react-router-dom（web开发使用），react-router-native
2. react路由的特点，都是组件，必须引入再使用
3. 安装`npm i react-router-dom -S`
4. 两种路由模式选择：BrowserRouter（history路由模式）、HashRouter（hash路由模式）
5. NavLink / Link 来实现声明式路由跳转
6. Route 定义路由一一对应的匹配规则
7. Redirect 实现路由重定向，必须要使用Switch（表示跳转哪一个路由） 将所有跳转的路由包裹起来
8. Redirect 和 Route 必须是兄弟关系，他们两个必须是Switch的子元素