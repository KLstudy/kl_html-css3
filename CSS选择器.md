# 常用选择器

## 元素选择器

```
作用：根据标签名来选中指定的元素
语法：标签名{}
例子：p{}  h1{}  div{}
```

## id选择器

```
作用：根据元素的id属性值选中一个元素
语法：#id属性值{}
例子：#box{} #red{}  
```

## 类选择器

```
作用：根据元素的class属性值选中一组元素
语法：.class属性值
```

代码：

```css
元素选择器
p{
     color: red;
 }

id选择器
#red{
     color: red;
} 

类选择器
.blue{
     color: blue;
}
```

# 复合选择器

## 概述

所谓复合选择器就是把多种选择器合在一起去用

```css
/* 将class为red的div字体大小设置为30px */
/* 
   交集选择器
   作用：选中同时复合多个条件的元素
   语法：选择器1选择器2选择器3选择器n{}
   注意点：
        交集选择器中如果有元素选择器，必须使用元素选择器开头
*/
div.red{
    font-size: 30px;
}


/* div#box1{} */
/*
     选择器分组（并集选择器）
         作用：同时选择多个选择器对应的元素
         语法：选择器1,选择器2,选择器3,选择器n{}

          #b1,.p1,h1,span,div.red{}
*/
h1, span{
    color: green
}

```

# 关系选择器

## html中元素的关系

​        父元素

​            \- 直接包含子元素的元素叫做父元素

​        子元素

​            \- 直接被父元素包含的元素是子元素

​        祖先元素

​            \- 直接或间接包含后代元素的元素叫做祖先元素

​            \- 一个元素的父元素也是它的祖先元素

​        后代元素

​            \- 直接或间接被祖先元素包含的元素叫做后代元素

​            \- 子元素也是后代元素

​        兄弟元素

​            \- 拥有相同父元素的元素是兄弟元素

## 相关代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 
            为div的子元素span设置一个字体颜色红色
            （为div直接包含的span设置一个字体颜色）

            子元素选择器
                作用：选中指定父元素的指定子元素
                语法：父元素 > 子元素
         */

        /* div.box > span{
            color: orange;
        } */

        /* 
            后代元素选择器：
                作用：选中指定元素内的指定后代元素
                语法：祖先 后代
         */
         /* div span{
             color: skyblue
         } */

         /* div > p > span{
             color: red;
         } */

         /* 
            选择下一个兄弟
                语法：前一个 + 下一个
            选择下边所有的兄弟
                语法：兄 ~ 弟
          */

          p + span{
              color: red;
          }
          p ~ span{
              color: red;
          }
    </style>
</head>
<body>
    <div class="box">
        我是一个div
        <p>
            我是div中的p元素
            <span>我是p元素中的span</span>
        </p>
        <div></div>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>
        <span>我是div中的span元素</span>
    </div>
    <span>
        我是div外的span
    </span>   
</body>
</html>
```

# 属性选择器

## 直接上代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        /* 
            [属性名] 选择含有指定属性的元素
            [属性名=属性值] 选择含有指定属性和属性值的元素
            [属性名^=属性值] 选择属性值以指定值开头的元素
            [属性名$=属性值] 选择属性值以指定值结尾的元素
            [属性名*=属性值] 选择属性值中含有某值的元素的元素
         */
        /* p[title]{ */
        /* p[title=abc]{ */
        /* p[title^=abc]{ */
        /* p[title$=abc]{ */
        p[title*=e]{
            color: orange;
        }
    </style>
</head>
<body>
        <p title="abc">少小离家老大回</p>
        <p title="abcdef">乡音无改鬓毛衰</p>
        <p title="helloabc">儿童相见不相识</p>
        <p>笑问客从何处来</p>
        <p>秋水共长天一色</p>
        <p>落霞与孤鹜齐飞</p>
</body>
</html>
```

# 伪类选择器

## 直接上代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* 
            将ul里的第一个li设置为红色
         */

/* 
        伪类（不存在的类，特殊的类）
            - 伪类用来描述一个元素的特殊状态
                比如：第一个子元素、被点击的元素、鼠标移入的元素...
            - 伪类一般情况下都是使用:开头
                :first-child 第一个子元素
                :last-child 最后一个子元素
                :nth-child() 选中第n个子元素
                    特殊值：
                        n 第n个 n的范围0到正无穷
                        2n 或 even 表示选中偶数位的元素
                        2n+1 或 odd 表示选中奇数位的元素

                    - 以上这些伪类都是根据所有的子元素进行排序

                :first-of-type
                :last-of-type
                :nth-of-type()
                    - 这几个伪类的功能和上述的类似，不通点是他们是在同类型元素中进行排序

            - :not() 否定伪类
                - 将符合条件的元素从选择器中去除
 */
        /* ul > li:first-child{
            color: red;
        } */
    
        /* ul > li:last-child{
            color: red;
        } */

        /* ul > li:nth-child(2n+1){
            color: red;
        } */

        /* ul > li:nth-child(even){
            color: red;
        } */

        /* ul > li:first-of-type{
            color: red;
        } */

        ul > li:not(:nth-of-type(3)){
            color: yellowgreen;
        }
    </style>
</head>
<body>
    
    <ul>
        <span>我是一个span</span>
        <li>第〇个</li>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>


</body>
</html>
```

## a元素的伪类

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

        /* 
            :link 用来表示没访问过的链接（正常的链接）
         */
        a:link{
            color: red;
            
        }

        /* 
            :visited 用来表示访问过的链接
            由于隐私的原因，所以visited这个伪类只能修改链接的颜色
        */
        a:visited{
            color: orange; 
            /* font-size: 50px;   */
        }

        /* 
            :hover 用来表示鼠标移入的状态
         */
         a:hover{
             color: aqua;
             font-size: 20px;
         }

         /*
            :active 用来表示鼠标点击
         */
         a:active{
             color: yellowgreen;
             
         }
    
    </style>
</head>
<body>
    
    <!-- 
        1.没有访问过的链接
        2.访问过的链接

     -->

    <a href="https://www.baidu.com">访问过的链接</a>

    <br><br>

    <a href="https://www.baidu123.com">没访问过的链接</a>

</body>
</html>
```

# 伪元素选择器

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        p{
            font-size: 20px;
        }

       /* 
            伪元素，表示页面中一些特殊的并不真实的存在的元素（特殊的位置）
                伪元素使用 :: 开头

                ::first-letter 表示第一个字母
                ::first-line 表示第一行
                ::selection 表示选中的内容
                ::before 元素的开始 
                ::after 元素的最后
                    - before 和 after 必须结合content属性来使用
        */
        p::first-letter{
            font-size: 50px;
        }

        p::first-line{
            background-color: yellow; 
        }

        p::selection{
            background-color: greenyellow;
        }

        /* div::before{
            content: 'abc';
            color: red;
        }

        div::after{
            content: 'haha';
            color: blue;
        } */

        div::before{
            content: '『';
         }

        div::after{
            content: '』';
        }

    </style>
</head>
<body>

    <!-- <q>hello</q> -->
    <div>Hello Hello How are you</div>
    
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque velit modi veniam nisi veritatis tempore laborum nemo ipsa itaque optio. Id odit consequatur mollitia excepturi, minus saepe nostrum vel porro.
    </p>


</body>
</html>
```



