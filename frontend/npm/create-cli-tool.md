# 创建一个node命令行工具

## 让node项目在命令行中执行

- 在根目录创建bin文件夹，创建index.js

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




