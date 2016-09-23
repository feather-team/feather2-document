### 模板语法标签
feathe2考虑到了单或多页面应用，及为了提高页面的重用性，对html进行了扩展，支持模板继承(extends, block)，模板引用功能(widget, pagelet)，并可互相组合使用。

#### extends、block、widget

layout.html
```html
<html>
<head>
<title>
    <!--可重写title-->
    <block "title">layout.html</block>
</title>
</head>
<body>

<!--引用widget/a.html-->
<widget "a">

<!--声明一个block块，用于被重写-->
<block "content">
<!--此处可以无内容-->
lalala
</block>

</body>
</html>
```
main.html
```html
<!--继承layout.html-->
<extends "./layout.html">

<block "title">main.html</block>
<block "content">lalala, i'm main.html</block>

<div>因为页面是继承，所以我会被feather忽略掉，不显示</div>
<block "ignore">
    lalalala
</block>
```

#### pagelet

使用格式

```html
<pagelet "pagelet名[#外部包裹textarea的id]">
```

main.html
```html
<!--继承layout.html-->
<extends "./layout.html">

<block "title">main.html</block>
<block "content">
    <div id="show"></div>

    <pagelet "a#lalala">
    
    <scirpt>
    require.async('jquery', function($){
        setTimeout(function(){
            //5秒后，将lalala里的东西，显示在show容器中
            $('#show').append($('#lalala').val());
        }, 5000);
    });
    </script>
</block>
```

相同布局的页面可使用extends结合block的方式进行开发， 一些通用模块可使用widget引入。

