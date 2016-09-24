## widget模板组件

widget指的是以模板文件为主实现组件化的独立html组件包，widget组件与业务关系较为密切

以下页面目录规范：
```sh
widget
  ├── footer
  │   ├── footer.css
  │   └── footer.html
  └── header
      ├── header.css
      ├── header.html
      └── header.js
```

widget与component的区别：

component以js和css为主，多作为公用插件，类库，同时也可使用js后期生成html，进行异步加载渲染

widget一般作为公用页面的html部分，可直接通过引入实现同步加载，如公用头尾，一个项目基本都长一个样

公共点， 2个目录中的js和css文件都可通过标签，或require方式直接引入

另外widget的html页面会自动加载当前目录下同名js和css，开发无需自己引入，如果需要在js的执行位置上有改变，则可以自行在任何位置引入

在页面中实现widget也非常方便， feather2为了便于大家的开发方便，支持了widget标签扩展：

index.html

```html
<widget 'header' />
hello, world
<widget 'footer' />
```

刷新页面查看效果， css文件全部会出现在head结束标签的上方，而header.js则使用require.async方式加载，并且出现在了header widget源码的下方， why？

其实这是feather2帮助开发者自行完成的性能优化， 目的有2点：

* require.async是异步加载文件，所以在js加载的同时，并不会堵塞下方html和资源的加载
* 我们在前端开发中，不仅仅是为了完成工作，同时还要考虑到用户体验， 让js使用异步的方式，并且尽早的返回，用户则可以更早的体验已经加载好的html部分的交互功能
