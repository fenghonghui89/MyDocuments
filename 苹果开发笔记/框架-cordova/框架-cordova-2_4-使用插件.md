
# 使用插件
cordova自带网页注释掉以下代码，否则点击无反应
```
 <meta http-equiv = "Content-Security-Policy" content = "default-src 'self' data: gap: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src * ” >
```

网页中添加事件监听是否成功加载
```
<script type="text/javascript">
      document.addEventListener("deviceready", onDeviceReady, false);
      function onDeviceReady() {
        console.log(navigator.camera);
        alert("camera is ok~");
      }
</script>
```


网页中使用插件
```
<script type="text/javascript">
      function showCamera() {
        navigator.camera.getPicture(onSuccess, onFail, { quality: 50,targetWidth:200,targetHeight:200,correctOrientation:true,destinationType:Camera.DestinationType.DATA_URL,sourceType:Camera.PictureSourceType.PHOTOLIBRARY});
                                    
      }
    function onSuccess(imageData) {
      var image = document.getElementById('myImage');
      image.src = "data:image/jpeg;base64," + imageData;
    }
    
    function onFail(message) {
      alert('Failed because: ' + message);
    }
   
  </script>


<input type="button" value="btn" style="width:100px;height:50px; position:absolute; top:100px;left:100px;" onclick="showCamera()”/>
```
