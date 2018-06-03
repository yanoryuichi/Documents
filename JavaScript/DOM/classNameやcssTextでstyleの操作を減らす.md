# classNameやcssTextでstyleの操作を減らす

```clike
element.style.color = "red";
element.style.fontSize = "25px";
```

```clike
.active {
    color: red;
    fontsize: 25px;
}

element.className = "active";
```

```clike
element.style.cssText = "color: red; fontSize: 25px;"
```

## 出典

http://www.slideshare.net/nzakas/writing-efficient-javascript
