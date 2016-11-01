##基于mustache模板引擎的应用开发

feather2不仅支持了纯静态项目或结合mvvm框架的webapp等单页面应用开发外，同时还集成了[mustache](http://mustache.github.io/)模板引擎，以便实现非纯ajax数据交互的项目场景

why mustache？

mustache是一种 Logic-less's template engine，语法相对比较轻量， 支持的语言多达几十种，基本上覆盖了所有能够进行web开发的语言，另外因为需要支持各种后端语言，feather2的后续需要对各种基于后端环境的定制化开发，既然mustache是通用的，不如就直接对其进行支持，可以满足大部分需要后端输出数据的项目场景


在feather2中使用mustache也非常简单，只需要熟悉mustache的语法即可，具体语法可见官方网站，这里只做简单介绍

开启mustache

```js
feather.config.set('template.mustache', true);
```

开发者可和后端开发在开发前期进行数据格式的约定：


test/index.json
```
{
    "title": "first data",
    "desc": ["a", "b", "c"]
}
```

index.html

```
<title>{{title}}</title>

{{#desc}}
    <p>{{.}}</p>
{{/desc}}
```

同样 widget和pagelet也是支持数据渲染的，只需要在test目录下建立与其路径一致的.json文件即可， 并且等此widget或者pagelet被其他页面引用时， 引用页面也会自动加载其测试数据，以便调试方便

另外 feather2提供了一个 test/\_global\_.json文件，作为全局数据使用，所有的页面均为加载该数据文件

###注：目前有部分带有模板引擎的前端类库中，界定符可能存在于mustache一样的情况，此时使用会存在问题，程序运行时，会被mustache直接解析，比如vue，发生这种情况时，请设置前端类库的界定符为其他字符，目前feather2中，未支持对mustache界定符的设定
