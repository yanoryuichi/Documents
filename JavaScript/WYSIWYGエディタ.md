# WYSIWYG エディタ

## 解説

## 参考

- http://www.mozilla-japan.org/editor/midas-spec.html
- http://arinogotokuatumarite.blog19.fc2.com/blog-entry-101.html

## サンプル

```clike
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style type="text/css">
td {
vertical-align: top;
}
</style>
<script type="text/javascript">
( function () {
  var isFirefox = navigator.userAgent.indexOf('Firefox') != -1 ? true : false;
  var isIE = navigator.appName == 'Microsoft Internet Explorer' ? true : false;
  var $ = function (id) { return document.getElementById(id) };
  var $$ = function (tagname, element) { return element.getElementsByTagName(tagname) };
  var viewMode = ''; // 'text' or 'source'
  var updateTextArea = function (form){
    //var form = evt.target;
    if (isFirefox) console.log(form);
    form.text1.value = $('edit_iframe').contentWindow.document.body.innerHTML;
  
  }
  var viewSource = function () {
    var doc = $('edit_iframe').contentWindow.document;
    if (isIE) {
      var iHTML = doc.body.innerHTML;
      doc.body.innerText = iHTML;
    } else {
      var html = document.createTextNode(doc.body.innerHTML);
      doc.body.innerHTML = "";
      doc.body.appendChild(html);
    }
    viewMode = 'source';
  };
  var viewText = function () { 
    var doc = $('edit_iframe').contentWindow.document;
    if (isIE) {
      var iText = doc.body.innerText;
      doc.body.innerHTML = iText;
    } else {
      var html = doc.body.ownerDocument.createRange();
      html.selectNodeContents(doc.body);
      console.log(html.toString());
      doc.body.innerHTML = html.toString();
    }
    viewMode = 'text';
  };
  var replaceTextAreaWithIframe = function () {
    var iframe = document.createElement('iframe');
    iframe.id = 'edit_iframe';
    iframe.style.width = '500px';
    iframe.style.height = '150px';
  
    $('edit_ta').style.display = 'none';
    $('edit_div').insertBefore(iframe, $('edit_div').firstChild);
    
    var value = $('edit_ta').value;
    var doc = $('edit_iframe').contentWindow.document;
    doc.open();
    doc.write(value);
    doc.close();
    doc.body.contentEditable = true;
    doc.designMode = 'on';
  }
  var textFormat = function (target, type, selected){
    if (viewMode == 'source') { 
      alert ("don't do this");  
      return;
    }
    var doc = $(target);
    if (isFirefox) {
      doc.contentWindow.document.execCommand('styleWithCSS', false, false);
    }
    doc.contentWindow.focus();
    doc.contentWindow.document.execCommand(type, false, selected);
  }
  var test1 = function (target) {
    var iframe = $(target);
    var range;
    if (isIE) {
      range = document.selection.createRange(); 
    } else {
      range = iframe.contentWindow.getSelection().getRangeAt(0); 
    }
    if (isIE) {
      var html = '<b>hello</b>';
      range.pasteHTML(html);
    } else {
      iframe.contentWindow.document.execCommand('inserthtml',false,'<b>hello</b>');
    }
  }
  var alert = function () { alert('ALERT'); }
  if (!this['WEdit']) {
    WEdit = {
        isIE:isIE,
        isFirefox:isFirefox,
        updateTextArea:updateTextArea,
        viewSource:viewSource,
        viewText:viewText,
        replaceTextAreaWithIframe:replaceTextAreaWithIframe,
        textFormat:textFormat,
        test1:test1,
        alert:alert
    };
  }
})();
window.onload = function() {
  WEdit.replaceTextAreaWithIframe();
  if (WEdit.isIE) {
    for (var idx=0; idx < document.forms.length; idx++) {
      document.forms[idx].attachEvent('onsubmit', function(event) { WEdit.updateTextArea(event.srcElement); });
    }
  } else {
    for (var idx=0; idx < document.forms.length; idx++) {
      document.forms[idx].addEventListener('submit', function(evt) { WEdit.updateTextArea(evt) }, true);
    }
  }
};
</script>
</head>
<body>
<?php if ($_REQUEST) { 
$req = htmlspecialchars(print_r($_REQUEST,1));
print "<pre>$req</pre>";
}?>
<form id="test_form" action="index.php" method="post">
  <table>
    <tr>
      <td>
        <div id='edit_div'><textarea name="text1" id="edit_ta">test</textarea></div>
      </td>
      <td>
        <ul>
          <li><input type="button" onclick="WEdit.textFormat('edit_iframe','bold',null)" value="太"/></li>
          <li><input type="button" onclick="WEdit.textFormat('edit_iframe','forecolor','#ff0000')" value="赤"/></li>
          <li><input type="button" onclick="WEdit.textFormat('edit_iframe','forecolor','#0000ff')" value="青"/></li>
          <li><input type="button" onclick="WEdit.textFormat('edit_iframe','forecolor','#000000')" value="黒"/></li>
        </ul>
        <ul>
          <li><input type="button" onclick="WEdit.test1('edit_iframe')" value="test1"/></li>
        </ul>
        <ul>
          <li><input type="button" onclick="WEdit.viewSource()" value="ソースモード"/></li>
          <li><input type="button" onclick="WEdit.viewText()" value="テキストモード"/></li>
        </ul>
        <ul>
        <li><input type="submit"/></li>
        <ul>
      </td>
    </tr>
  </table>
</form>
</body>
</html>
```
