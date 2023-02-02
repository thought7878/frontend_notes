
```javascript
/** @type {import('tailwindcss').Config} */
const defaultTheme = require("tailwindcss/defaultTheme");

module.exports = {
	content: ["./src/**/*.{js,jsx,ts,tsx}"],
	theme: {
		extend: {
			colors: {
				primary: "#a0d911", //hope-500
				inputFocusColor: "#a0d911", //hope-500
				success: "#a0d911", //hope-500
				warning: "#faad14", //gold 6
				danger: "#ff4d4f",
				hope: {
					50: "#fcffe6", //selected bg color
					100: "#f4ffb8",
					200: "#eaff8f",
					300: "#d3f261",
					400: "#bae637", //hover
					500: "#a0d911", //brand
					600: "#7cb305", //click
					700: "#5b8c00",
					800: "#3f6600",
					900: "#254000",
				},
				auiLight: {
					//antD
					title: "#262626", //black 85%
					primary: "#595959", //65%
					secondary: "#8c8c8c", //45%
					disable: "#bfbfbf", //25%
					border: "#d9d9d9", //15%
					divider: "#f0f0f0", //6%
					background: "#f5f5f5", //4%
					tableHeader: "#fafafa", //2%
				},
			},
			boxShadow: {
				input: `0 0 0 2px #a0d911`,
				button: `0 0 0 2px #a0d911`,
			},
		},
	},
	plugins: [],
};

```


### Text 
- Color:text-gray-900


### List/
#### border
-  radius:`rounded-lg`
-  width:`border`
-  color:`border-gray-200`
-  style:`border-solid`
#### item 
- padding:`px-4` `py-2`


### Input
#### size
- padding:`px-3` `py-1.5`
- color:

#### Input

$btn-padding-y-lg: py-2
$btn-padding-x-lg: px-4 
$btn-font-size-lg: text-lg
$btn-border-radius-lg:rounded-lg

#### Button

$btn-padding-y-md: py-1.5
$btn-padding-x-md: px-3 
$btn-font-size-md: text-md
$btn-border-radius-md:rounded-md

$btn-padding-y-lg: py-2
$btn-padding-x-lg: px-4 
$btn-font-size-lg: text-lg
$btn-border-radius-lg:rounded-lg

#### border
- width:`border`
- color:`border-gray-200`
- style:`border-solid`
- radius:`rounded-md`

#### font
- size:`text-base`/`text-sm`   font-size: 1rem/16px;line-height: 1.5rem/24px; 
- weight:`font-normal`   font-weight: 400;
- color: `text-gray-900`/`text-gray-500`;
- placeholder:text-gray-400;

#### background
- color:bg-white
- clip:bg-clip-padding

#### disabled
- disabled:bg-gray-200;

#### focus
- focus:shadow-md

#### opacity
- btn-disabled-opacity:opacity-70