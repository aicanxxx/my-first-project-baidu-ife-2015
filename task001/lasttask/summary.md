### index.html

- `header`部分

遇到的问题：

1.设置背景宽度为100%时，当浏览器低于980px时，出现横向滚动条，滚动滚动条，发现背景颜色是白色，而不是紫色
    
由于只设置了header的背景颜色，而没有设置header-main的背景颜色，其默认为透明的；而header的背景颜色的宽度为实际浏览器的宽度，超出浏览器宽度的位置自然为默认的颜色，故需重新给header-main添加背景颜色。

2.当浏览器低于980px时，右上角的Github图标在浏览器低于980px时消失。

这个问题刚开始困扰了我好久，因为github图标是根据header块进行绝对定位的，而header的宽度就是浏览器实际宽度，也就是说github图标一直在距离浏览器右边距10px的地方，滚动滚动条，会发现两个div互相覆盖了，而且都是用position进行定位，故只要将git-logo放在header-main前面就行。

html代码
```
<div class="header">
     <div class="git-logo">
         <a href="http://www.github.com"><img src="images/icon-github.png"></a>
     </div>
     <div class="header-main">
         <div class="logo f_left">
             <a href="http://www.baidu.com"><img src="images/logo.jpg"></a>
         </div>
         <div class="menu f_right">
             <ul>
                 <li><a href="index.html">首页</a></li>
                 <li><a href="blog.html">文章</a></li>
                 <li><a href="gallery.html">作品</a></li>
                 <li><a href="about.html">关于</a></li>
             </ul>
         </div>
     </div>
 </div>
```
css代码 
```
*{
     margin:0;
     padding:0;
}
.f_left{
     float: left;
}
.f_right{
     float: right;
}
.header{
     width:100%;
     height: 80px;
     background-color: #522a5c;
     position: relative;
}
.header-main{
     width: 980px;
     height: 80px;
     margin:0 auto;
     position: relative;
     background-color: #522a5c;
}
.logo,.menu{
     position: relative;
     top:50px;
}
a{
     text-decoration: none;
     font-family: "宋体","微软雅黑",sans-serif;
     font-size:14px;
     color:white;
}
.menu li{
     float: left;
     list-style: none;
     margin-left:28px;
}
.git-logo{
     position: absolute;
     right:10px;
     bottom:0;
}
``` 
- `banner`部分

遇到的问题：

1.图片与浏览器宽度问题

背景时宽度为100%，当浏览器小于980px时会出现滚动条，但滚动滚动条发现超出浏览器尺寸的地方没有背景图片，于是设置成min-height:980px,这样，即使尺寸小于980px，背景也有980px，和header部分相对应。

2.图片尺寸问题

由于图片尺寸过大，作为背景时宽度为100%，浏览器只能显示一部分，故使用background-size：100% 100%；

3.渐变透明度

```background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0.7) 0%, rgba(255, 255, 255, 0.5) 25%, rgba(255, 255, 255, 0) 100%);```

html代码
```
<div class="banner">
    <div class="context-wp">
        <div class="context">
            <span>标题</span>
            <p>接下来就是github图标了。要想把一张图片显示在一个div的右下方大概有：1.把图片作为该div的background-image；2.由于图片是行内元素，可以利用text-align；</p>
        </div>
    </div>
</div>
```
css代码
```
.banner{
    min-width:980px;
    height:526px;
    background: url("../images/banner-bg.jpg");
    background-size: 100% 100%;
}
.context-wp{
    width: 980px;
    height:100%;
    margin:0 auto;
    position: relative;
}
.context{
    width:360px;
    position: absolute;
    bottom:0;
    right:0;
    padding:10px 10px 30px 10px;
    background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0.7) 0%, rgba(255, 255, 255, 0.5) 25%, rgba(255, 255, 255, 0) 100%);
    font-family: "宋体", "微软雅黑", sans-serif;
    color: #ffffff;
}
.context p{
    font-size:12px;
    line-height:150%;
    text-indent: 24px;
}
.context span{
    display: block;
    font-size: 14px;
    margin-bottom: 12px;
    text-align: right;
}
```

