#HoldScaleImageView
最近的需求，希望imageview的宽度固定，高度随图片的缩放大小一致，保持图片的缩放比。

scaleType有的是支持缩放的，但是会把超出部分裁剪掉。

我希望的样子是，图片尺寸x\*y，控件宽度固定为w，控件高度会随图片缩放后的高度来定，也就是w\*y/x

最终效果图：

![image](https://github.com/Blankeer/HoldScaleImageView/blob/master/image.png)

每行左边的是最终自定义控件效果。

第一行，规定宽度为100dp,scaleType="centerCrop"

第二行宽度也是100dp，scaleType="fitCenter"

第三行规定高度为100dp,scaleType="centerCrop"

图片绿色部分是layout的背景，红色为imageview背景

第二行右边的图片缩放在中间，导致控件上下还有多的间隙

第三行和前面的情况相反，固定高度，宽度跟随改变

实现思路就是自定义onMeasure(),根据上面的公式手动算出缩放后的大小，从而设置控件大小

使用方法：

 1.设置android:scaleType="centerCrop"
 
 2.android:layout_width或layout_height设置固定值
 
 3.设置app:holdHeight="true"或app:holdWidth="true"，含义是高度/宽度固定，必须和第2条设置的对应
 
Step 1. Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url "https://jitpack.io" }
		}
	}
Step 2. Add the dependency

	dependencies {
	        compile 'com.github.Blankeer:HoldScaleImageView:0.1.3'
	}


