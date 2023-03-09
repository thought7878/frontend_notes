# 创建一个 node 命令行工具

## 让 node 项目在命令行中执行

- 在根目录创建 bin 文件夹，创建 index.js

  ```js
    #!/usr/bin/env node
    console.log("hello");
  ```

- package.json

  ```json
  "bin": {
      "l-nrm": "bin/index.js"
  }
  ```

### 将代码安装到电脑上

## link

`npm link` 创建软连接到全局（node/v12.8.0/lib/node_modules），即：可以在不发布 npm 模块的情况下，调试该模块，并且修改模块后会实时生效，不需要通过 npm install 进行安装

```bash
# aui/
npm link
```

```bash
# aui-test/
npm link aui
```

- [使用软链 npm link](https://juejin.cn/post/6844904030620090382)
