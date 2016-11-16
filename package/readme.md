```javascript
 vulcanize target.html > build.html
```
> 将target.html及import到target.html中的html, js, css合并成一个文件

```javascript
 vulcanize --inline-scripts target.html > build.html
```

> 将target.html中引入的js文件和html文件合并成一个文件并以build.html的文件形式输出

```javascript
vulcanize --inline-css target.html > build.html
```

> 将target.html中以<link rel="import" type="css">方式引入的文件合并到build.html文件中

```javascript
vulcanize --strip-comments target.html > build.html
```

> 去除注释输出
