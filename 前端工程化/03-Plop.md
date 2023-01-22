# [Plop](https://www.npmjs.com/package/plop)
一个小而美的脚手架工具

## 安装

```bash
npm install -D plop
```

## 基本使用

### 配置
- 配置plopfile.js

```javascript
// projectfolder/plopfile.js

module.exports = (plop) => {
	plop.setGenerator("component", {//生成器的名字
		description: "create a component",
		prompts: [
			{
				type: "input",
				name: "name", //输入返回值的key
				message: "component name", //屏幕上的提示
				default: "MyComponent", //默认答案
			},
		],
		actions: [
			{
				type: "add", //添加文件
				path: "src/components/{{name}}{{name}}.js", //添加文件的路径
				templateFile: "plop-templates/component.hbs", //指定模板文件
			},
            {
				type: "add", //添加文件
				path: "src/components/{{name}}/_{{name}}.scss", //添加文件的路径
				templateFile: "plop-templates/component.scss.hbs", //指定模板文件
			},
		],
	});
};

```



- 配置plop-templates

```javascript
// projectfolder/plop-templates/component.hbs
import React from 'react';

export default (props)=>(
    <div>{{name}} Component</div>
)
```

- 配置 package.json

```json
// package.json
{
    ...,
    "scripts": {
        "plop": "plop"
    },
    ...
}
```
### 使用

```console
npm run plop component //component：生成器的名字
```