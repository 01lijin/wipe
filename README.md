﻿## ver 0.0.1 ##
PC端实现涂抹擦除效果, 超过50%的涂抹面积可以查看全部. 涂抹颜色和背景图片手动指定. 2018-11-12
## ver 1.0.0 ##
1. 实现了对移动端的支持
1. 函数优化
## ver 2.0.0 ##
实现了面向对象方式,
增加了参数配置
## ver 3.0.0 ##
1. 浏览器在滚动距离下bug修复
2. canvas画布在有偏移和绝对定位下bug修复
3. 增加了回调函数. 让用户可以自己完成后继功能

使用步骤说明:
1. 在HTML中添加指定id的canvas标签.

例如:
``` 
<canvas id="cas" width="375" height="667"></canvas>
 ```

2. 编辑配置文件:

### 属性名----取值类型-----备注 ###
1. id ---- 字符串 ---- canvas标签的id 
2. coverType ---- 字符串 ---- 取值"color"或"image" 
3. color ---- 字符串 ---- 十六进制颜色码, 或rgba().如果不指定默认值为#666 
4. imgUrl ---- 字符串 ---- 前面的覆盖图片 
5. backImgUrl ---- 字符串 ---- canvas背景图片 
6. width ---- 字符串 ---- canvas宽度, 必须和canvas标签中宽度一致 
7. height ---- 字符串 ---- canvas高度, 必须和canvas标签中高度一致 
8. radius ---- 字符串 ---- 涂抹笔的半径 
9. transpercent ---- 数值 ---- 透明面积占整个画布的百分比, 超出此数字显示全部画布 
10. callback ---- 函数 ---- 用户自定义的回调函数名称 


例如:
``` 
var wipeConfig = {
	id:"cas",
	coverType:"color", // 取值类型color, image
	color:"rgb(185,122,87)",
	imgUrl:"image/wipe2.jpg",  // 前面的覆盖图
	backImgUrl:"image/wipe1.jpg",  // 背景图片
	width:"375",  // canvas宽
	height:"667",  // canvas高
	radius:"20",  // 涂抹的半径
	transpercent:50,  // 透明面积占整个画布的百分比, 超出此数字显示全部画布
	callback:wipeCallback  // 用户自定义回调函数名称
}
 ```3. 初始化wipe插件,并将上一步的配置作为参数传入例如:``` 
new Wipe(wipeConfig);
 ```4. 编写回调函数. 用户在涂抹完成的后继操作必须写在此回调函数中例如:``` 
function wipeCallback(percent){	if (percent>50) {		console.log("透明面积超过50%, 查看底图");	};}
 ``` ## ver 3.1.0 ## 1. 添加文字 2. 延迟透明面积计算 