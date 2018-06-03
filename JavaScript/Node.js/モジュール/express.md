# express


## クエリーパラメータ・フォームデータの参照

```clike
(req.params) Checks route params, ex: /user/:id 

(req.query) Checks query string params, ex: ?id=12 Checks urlencoded body params  

(req.body) ex: id=12 To utilize urlencoded request bodies, req.body should be an object. 
           This can be done by using the _express.bodyParser middleware.
```

- http://stackoverflow.com/questions/6912584/how-to-get-get-query-string-variables-in-node-js/6913287#6913287
- http://stackoverflow.com/questions/5710358/how-to-get-post-query-in-express-node-js

## 参考

- GUIDE: http://expressjs.com/guide.html
