# useEffect

## [是什么？为什么？](https://zh-hans.reactjs.org/docs/hooks-effect.html)
为函数组件增加生命周期特性。可以把 useEffect Hook 看做 componentDidMount，componentDidUpdate 和 componentWillUnmount 这三个函数的组合。

与 componentDidMount 或 componentDidUpdate 不同，使用 useEffect 调度的 effect 不会阻塞浏览器更新屏幕，这让你的应用看起来响应更快。

## 无需清除的 effect
有时候，我们只想在 React 更新 DOM 之后运行一些额外的代码。比如发送网络请求，手动变更 DOM，记录日志，这些都是常见的无需清除的操作。因为我们在执行完这些操作之后，就可以忽略他们了。

### useEffect 做了什么？
你可以告诉 React 组件需要**在渲染后执行某些操作，在执行 DOM 更新之后调用它**。可以执行数据获取。
### 为什么在组件内部调用 useEffect？
将 useEffect 放在组件内部让我们可以在 effect 中直接访问 state 变量（或其他 props）。
### useEffect 会在每次渲染后都执行吗？
是的，默认情况下，它在第一次渲染render之后和每次更新render之后都会执行。React 保证了每次运行 effect 的同时，DOM 都已经更新完毕。


### 通过跳过 Effect 进行性能优化

```javascript
useEffect(effect: EffectCallback, deps?: DependencyList): void
```
- [为什么React18的useEffect effect callback会执行两次？](https://juejin.cn/post/7137654077743169573)

初始化执行：render --> effect callback --> cleanup --> effect callback(v16.8只有一次effect callback)

- deps=[]

仅在组件挂载和卸载时执行。这就告诉 React 你的 effect 不依赖于 props 或 state 中的任何值，所以它永远都不需要重复执行。

effect callback 类似 componentDidMount，cleanup 类似 componentWillUnmount

初始化执行：render --> effect callback

update执行：render 

- deps=undefined

此时类似componentDidMount/componentDidUpdate/componentWillUnmount

初始化执行：render --> effect callback

update执行：render --> cleanup --> effect callback

- deps=[dep]

此时类似componentDidMount/componentDidUpdate/componentWillUnmount

初始化执行：render --> effect callback

update执行：render --> cleanup --> effect callback 
