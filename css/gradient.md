css3渐变   
linear-gradient   线性渐变   默认情况向是从上往下渐变（相当于to bottom）
渐变角度设置：
	to left：设置渐变为从右到左。
	to right：设置渐变从左到右。
	to top：设置渐变从下到上。
	to bottom：设置渐变从上到.
	通过角度设置：是以顺时针方向旋转。

渐变颜色设置：至少需要设置2个颜色(可以是相同的颜色)
同时也可以指定每种颜色渐变的百分比，若未设置颜色渐变的百分比值，默认每种颜色占据的百分比相等
	未设置颜色的百分比，各种颜色占据的比例相等
	background-image: linear-gradient(to right,red,red,yellow,gray, black);
	设置百分比效果
	background-image: linear-gradient(to right,red 0%,yellow 70%,yellow 80%,gray 90%, black 100%);



radial-gradient:径向渐变  默认值渐变方式为circle（圆形的径向渐变）
渐变形式设置
第一个值为X轴，第二个值为Y轴（若只设置一个值，第二个值默认为center）
	left：设置左边为径向渐变圆心。
	center①：设置中间为径向渐变圆心。
	right：设置右边为径向渐变圆心。
	同时也可以通过百分比以及具体的像素设置
系统给出的形式
	circle：指定圆形的径向渐变
	ellipse：指定椭圆形的径向渐变。
	closest-side：指定径向渐变的半径长度为从圆心到离圆心最近的边
	closest-corner：指定径向渐变的半径长度为从圆心到离圆心最近的角
	farthest-side：指定径向渐变的半径长度为从圆心到离圆心最远的边
	farthest-corner：指定径向渐变的半径长度为从圆心到离圆心最远的角

	background-image:  radial-gradient(at center, red,yellow,green,blue);

	background-image:  radial-gradient(closest-side, red,yellow,green,blue);

渐变颜色设置：至少需要设置2个颜色(可以是相同的颜色)
同时也可以指定每种颜色渐变的百分比，若未设置颜色渐变的百分比值，默认每种颜色占据的百分比相等
	未设置颜色的百分比，各种颜色占据的比例相等
	设置百分比效果



repeating-linear-gradient:重复线性渐变（与线性渐变形同，知识渐变灰重复）
	repeating-linear-gradient(#f00, #ff0 10%, #f00 15%);

repeating-radial-gradient：重复径向渐变
	background-image:  repeating-radial-gradient(circle, #f00 0, #ff0 10%, #f00 15%);		

		