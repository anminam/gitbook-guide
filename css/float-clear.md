# float clear

```markup
<!-- overflow:hidden을 이용해서 클리어를 합시다 -->
<div class="wrap">
  <div class="box">가나다</div>
  <div class="box">라마바</div>
</div>
<!-- after를 이용해서 클리어를 합시다 -->
<div class="wrap2">
  <div class="box">가나다</div>
  <div class="box">라마바</div>
</div>
<!-- 빈태그를 이용해서 클리어를 합시다 -->
<div class="wrap3">
  <div class="box">가나다</div>
  <div class="box">라마바</div>
  <span class="clear"></span>
</div>
<!-- block forammting context란? 뭘까 -->
<div class="wrap4">
  <div class="box">가나다</div>
  <div class="box">라마바</div>
</div>
```

```css
.wrap{
  background-color: pink;
  overflow: hidden;
}
.box{
  float: left;
}

.wrap2{
  background-color: orange;
}
.wrap2:after{
  content: '';
  display: block;
  clear: both;
}

.wrap3{
  background-color: ivory;
}
.wrap3 .clear{
  display: block;
  clear: both;
}

.wrap4{
  display: inline-block;
  background-color: skyblue;
  width: 100%;
}

```

