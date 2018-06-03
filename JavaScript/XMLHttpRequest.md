# XMLHttpRequest

```clike
function getXmlHttp(){
 if (window.ActiveXObject) {
   try {
     return new ActiveXObject("Msxml2.XMLHTTP");
   } catch (e) {
     try {
       return new ActiveXObject("Microsoft.XMLHTTP");
     } catch (e) {
       return null;
     }
   }
 } else if (window.XMLHttpRequest) {
   return new XMLHttpRequest();
 } else {
   return null;
 }
}
```

```clike
function getUserName(user_id) {
 var xmlhttp = getXmlHttp();
 xmlhttp.onreadystatechange = function () {
   if (xmlhttp.readyState == 4) {
     var text = xmlhttp.responseText;
     var user_name = eval(text);
   }
 }
 xmlhttp.open("GET", "index.php?user_id=" + unit_id, true);
 xmlhttp.send();
}
```
