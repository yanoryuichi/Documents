# mocha

```clike
--- base.js.20131014    2013-10-14 21:01:29.581749224 +0900
+++ base.js     2013-10-14 21:41:37.483734057 +0900
@@ -40,23 +40,23 @@
  */

 exports.colors = {
-    'pass': 90
+    'pass': 0
   , 'fail': 31
-  , 'bright pass': 92
-  , 'bright fail': 91
-  , 'bright yellow': 93
+  , 'bright pass': 32
+  , 'bright fail': 31
+  , 'bright yellow': 33
   , 'pending': 36
   , 'suite': 0
   , 'error title': 0
   , 'error message': 31
-  , 'error stack': 90
+  , 'error stack': 33
   , 'checkmark': 32
-  , 'fast': 90
+  , 'fast': 32
   , 'medium': 33
   , 'slow': 31
   , 'green': 32
-  , 'light': 90
-  , 'diff gutter': 90
+  , 'light': 33
+  , 'diff gutter': 32
   , 'diff added': 42
   , 'diff removed': 41
 };
@@ -66,9 +66,9 @@
  */

 exports.symbols = {
-  ok: '✓',
-  err: '✖',
-  dot: '․'
+  ok: 'O',
+  err: 'X',
+  dot: '.'
 };

 // With node.js on Windows: use symbols available in terminal default fonts
```
