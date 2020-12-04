# CSS

## CSS基本语法

### CSS书写位置

1.行内式：

```html
<p style="color: red; font-size: 60px;">今天天气真不错！</p>
```

卸载标签内部的称为行内式，开发中一般不会用到行内式

2.内联式：

``` html
<!doctype html>
<html lang="zh">
    <head>
        <title>CSS练习</title>
        <style>
            样式。。。
        </style>
    </head>  
    <body>
        
    </body>
</html>
```

3.外联式

```html
<!DOCTYPE html>
<html>
    <head>
        <head>
            <link rel="stylesheet" href="./style.css">
        </head>
    </head>
    <body>
    </body>
</html>
```

外联式需要独立新建一个css文件，里面专门来写css样式

