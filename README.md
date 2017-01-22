# img-previewer
预览本地图片

## 示例
![](../example.png)

## 说明
#### 实现方式一：使用FileReader
```javascript
var preview = document.getElementById("preview");
var file = document.getElementById("file-input").files.item(0);
var reader = new FileReader();
reader.onload = function() {
    preview.src = reader.result;
}
if (file) {
    reader.readAsDataURL(file);
} else {
    preview.src = "";
}
```
#### 实现方式二：使用URL.createObjectURL
```javascript
var id = "file-input";
var preview = document.getElementById("preview");
var url;
if (navigator.userAgent.indexOf("MSIE") >= 1) { // IE
    url = document.getElementById(id).value;
} else if (navigator.userAgent.indexOf("Firefox") > 0) { // Firefox
    url = window.URL.createObjectURL(document.getElementById(id).files.item(0));
} else if (navigator.userAgent.indexOf("Chrome") > 0) { // Chrome
    url = window.URL.createObjectURL(document.getElementById(id).files.item(0));
}
preview.src = url;
```
完整示例请查看

[DEMO](https://vincentpat.github.io/img-previewer/)
