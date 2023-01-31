## 自定义hook

- 是什么？

如果函数的名字以 “use” 开头并调用其他 Hook，我们就说这是一个自定义 Hook。

你可以创建涵盖各种场景的自定义 Hook，如表单处理、动画、订阅声明、计时器。

- [为什么使用？](https://zh-hans.reactjs.org/docs/hooks-overview.html#building-your-own-hooks)
  - 有时候我们会想要在组件之间重用一些状态**逻辑**
  - 自定义 Hook 可以让你在不增加组件(高阶组件和 render props)的情况下达到重用一些状态**逻辑**


