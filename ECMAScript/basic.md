

## 小知识点
- ...

```javascript
const Button: React.FC<ButtonProps> = (props) => {
	const { btnType, className, disabled, size, children, href, ...restProps } =
		props;
```