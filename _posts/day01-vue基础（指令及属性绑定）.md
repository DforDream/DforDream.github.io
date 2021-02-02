# vue基础（指令及属性绑定）

# vue指令

## v-text ：

- {{}} 是v-text指令的简写 v-text指令将表达式的结果以innerText来实现 先将表达式的结果计算，再赋值给标签的innetText属性 

## v-html：

- v-html 是innerHTML的实现，vue 2.0之前，简写{{{}}} 现在已被删除，不推荐使用，存在安全隐患

## v-show: 

- 通过控制标签的display 来控制标签的显示 v-show：切换开销底，初始化开销高

## v-if: 

- 通过控制标签是否存在dom中来控制标签的显示  切换开销高，初始化开销低
- v-if中不要写其他代码 会报错
-  v-if v-else-if v-else 三个指令搭配使用 中间不能出现其他代码 否则编译会报错

## v-bind:

- v-bind 用于绑定标签的属性
- 标签属性： class style id title src href alt type... 标签属性，除class，style之外 ，所有的属性绑定方式都一样

## v-for:

- v-for 循环遍历重复的结构 
- 设置key值提升differ算法对比虚拟dom的速度，提升渲染速度

## v-for v-show v-if

- template 和v-show一起使用没有效果 
- 当v-for和template一起使用，key不能设置再template上
- 当v-for和v-if或v-show一起作用再一个标签上 先执行for for的优先级最高

## v-model

- v-model处理表单 数据双向绑定
- 单个值绑定字符串 多个值绑定数组

## 其他指令

- v-pre 指定这个范围不被vue作用
- v-cloak 防止vue不作用时 {{}}出现闪烁问题
- v-once 只解析一次

## v-on

- 原生事件,再vue中都能通过v-on指令改写
- v-on 简写 @
- 函数不写()默认有$event 参数

## v-on 修饰符

- .stop 事件修饰符 阻止事件冒泡 
- .capture 执行事件捕获
- 按键修饰符 .enter / 13

## class和style的绑定

- 数组形式 :class="['red','yellow']"
- 对象的形式 :class="{red:true,grren:false}" :class="obj"
- 数组对象得到形式 :class="['red','yellow',{green:true,blue:false}]"

