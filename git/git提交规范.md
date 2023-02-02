```javascript
<type>(<scope>): <subject>
// 注意冒号 : 后有空格
// 如 feat(miniprogram): 增加了小程序模板消息相关功能
```

scope选填表示commit的作用范围，如数据层、视图层，也可以是目录名称
subject必填用于对commit进行简短的描述
type必填表示提交类型，值有以下几种：

- feat - 新功能 feature
- fix - 修复 bug
- docs - 文档注释
- style - 代码格式(不影响代码运行的变动)
- refactor - 重构、优化(既不增加新功能，也不是修复bug)
- perf - 性能优化
- test - 增加测试
- chore - 构建过程或辅助工具的变动
- revert - 回退
- build - 打包



## 参考资料
- [超详细的Git提交规范引入指南](https://juejin.cn/post/6844903793033756680)