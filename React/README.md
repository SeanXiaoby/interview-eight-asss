# React 面试题

---

## React和vue的区别

## React 特性与用法

### 组件间通信

- 父->子组件

父组件通过子组件的`props`参数向子组件传参

- 子->组件

子组件通过调用父组件传进来的回调函数向父组件传参

- 兄弟组件

一个父组件的不同子组件（兄弟组件）通过共用父组件的变量传参

- 其他方式

没有直接关联的组件/兄弟组件/多级子组件 通过`context`传参



### React路由

React组件的生命周期分为三个阶段：挂载阶段（Mounting）、更新阶段（Updating）和卸载阶段（Unmounting）。

- 挂载阶段：
  - constructor()：组件构造函数，用于初始化组件的状态和绑定方法等操作。
  - static getDerivedStateFromProps()：组件初始化或props更新前调用，用于根据传入的props更新state状态。
  - render()：组件渲染函数，用于输出组件的结构和内容。
  - componentDidMount()：组件挂载后调用，用于进行DOM操作或获取数据等副作用操作。

- 更新阶段：
  - static getDerivedStateFromProps()：组件更新props时调用，用于根据传入的props更新state状态。
  - shouldComponentUpdate()：组件更新前调用，用于控制组件是否需要重新渲染。
  - render()：组件重新渲染函数，用于输出组件的结构和内容。
  - getSnapshotBeforeUpdate()：组件更新前调用，用于获取更新前的快照信息。
  - componentDidUpdate()：组件更新后调用，用于进行DOM操作或获取数据等副作用操作。

- 卸载阶段：
  - componentWillUnmount()：组件卸载前调用，用于清理组件中使用的定时器、取消网络请求等资源。

在React组件的生命周期中，每个阶段都有不同的钩子函数可以调用，这些钩子函数可以让开发者在组件的不同生命周期中实现不同的逻辑和处理。这些生命周期函数的使用可以让组件的开发和维护更加方便和灵活。

---

## React 实现功能

### 用户登录

---

## Rest API