# FileReader 文件上传图片,展示图片缩略图

> FileReader 是HTML5新方法，更好的解决文件上传图片时，前端可以使用base64编码格式展示图片缩略图。

> 解决fakepath，图片路径加密问题。

## 代码如下：

```html
    <!DOCTYPE html>
    <html>
    <head>
    	<title>文件上传图片，显示缩略图</title>
    	<style type="text/css">
    		div {
    			margin: 30px;
    		}
    		#mImg {
    			max-width: 100px;
    		}
    	</style>
    </head>
    <body>

    	<div>
    		<input id="mFile" type="file" name="file">
    	</div>
    	<div>
    		<img id="mImg" src="">
    	</div>


    	<script type="text/javascript">

    		document.getElementById('mFile').onchange = function (ev) {
    			//判断 FileReader 是否被浏览器所支持
    			if (!window.FileReader) return;

    			console.log(ev);

    			var file = ev.target.files[0];  

    			if(!file.type.match('image/*')){
    				alert('上传的图片必修是png,gif,jpg格式的！');
    				ev.target.value = ""; //显示文件的值赋值为空
    				return;
    			}

    			var reader = new FileReader();  // 创建FileReader对象

    			reader.readAsDataURL(file); // 读取file对象，读取完毕后会返回result 图片base64格式的结果

    			reader.onload = function(e){
    				document.getElementById('mImg').src = e.target.result;
    			}

    		}

    	</script>
    </body>
    </html>

```

#### 注意：新方法会有兼容问题，如果考虑ie低版本，请把老方法加进去~
