jQuery拖拽  
使用mousedown mousemove变更坐标  
  
例子  
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		*{
			margin:0;
			padding: 0;
		}
		#main{
			width:200px;
			height:200px;
			background: yellow;
			position: absolute;
			top:100px;
			left:100px;
			-webkit-user-select: none;
			cursor: move;
		}
	</style>
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
</head>
<body>
	<div id="main">
		我能被拖动
	</div>
    <script type="text/javascript">
        var lastPoint = {};
        var docWidth = $(document).width(),
            docHeight = $(document).height();
        var divPasition = {};
        var delta = {};
        var flag = false;
        var newCoor = {};
        $('#main').mousedown(function(event) {
            lastPoint.left = event.pageX;
            lastPoint.top = event.pageY;
            flag = true;
        });
        $(document).mousemove(function(event) {
            divPasition.left = $('#main').offset().left;
            divPasition.top = $('#main').offset().top;
            delta.left = event.pageX - lastPoint.left;
            delta.top = event.pageY - lastPoint.top;
            if (flag) {
                if (divPasition.left + delta.left < 0) {
                    newCoor.left = 0;
                } else if (divPasition.left + delta.left > (docWidth - 200)) {
                    newCoor.left = docWidth - 200;
                } else {
                    newCoor.left = divPasition.left + delta.left;
                }
                if (divPasition.top + delta.top < 0) {
                    newCoor.top = 0;
                } else if (divPasition.top + delta.top > (docHeight - 200)) {
                    newCoor.top = docHeight - 200;
                } else {
                    newCoor.top = divPasition.top + delta.top;
                }
            };
            lastPoint.left = event.pageX;
            lastPoint.top = event.pageY;
            $('#main').offset({ left: newCoor.left, top: newCoor.top});
        }).mouseleave(function(event) {
            flag = false;
        }).mouseup(function(event) {
            flag = false;
        });
    </script>
</body>
</html>
```
  
html5拖拽(拖放)  
HTML5权威手册page.787~801  
http://www.w3school.com.cn/html5/html_5_draganddrop.asp   w3c的教程,相对于html5书籍更新一些  
https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_Drag_and_Drop_API MDN介绍  
