## js组件包(components)

在feather中，component是指功能独立或完善的js插件或带有css的组件，这些组件可以当成模块供其他的js调用，或者供html引用，比如jquery、jquery-ui，backbone等都可以称之为components

component的目录结构如下：
```sh
components      #组件包
├── backbone
│   ├── backbone.js
│   └── bower.json
├── bootstrap
│   ├── bootstrap.css
│   ├── lib.js  #bower.json中的main属性指向此文件，调用时，直接 使用bootstrap即可
│   └── bower.json
└── underscore
    ├── bower.json
    └── underscore.js
```
feather2对component的安装提供了install命令，该命令是对bower的封装，可以方便开发更好的进行组件的管理

why is bower？ 

首先bower的资源是非常丰富的，可以支持github上的某一个仓库的分支， 其次bower会自动处理组件之间的依赖关系，也就是说，我们需要使用一个js的组件时，并不需要知道该组件依赖了其他的某些组件，符合模块化处理依赖的思想

但是bower包几乎都采用了amd或umd规范，甚至有些bower包的是没有规范的，而feather因为静态资源管理的问题，采用了commonjs规范，因此feather对其进行了一定的处理，尽可能的让bower中的包能够正常的运行。同时删除了bower包中无用的文件。

在项目中使用组件就像npm结合node中的require一样，只需要知道组件的名称即可

#### 安装包
```sh
cd demo
feather2 install socket.io-client bootstrap vue #包会被直接安装至components目录下
```

#### 使用包

index.html

```html 
<link href="bootstrap/css/bootstrap.css" type="text/css" />

<script>
require.async('vue', function(Vue){
    console.log(Vue);
});

require.async('socket.io-client', function(io){
    console.log(io);
});
</script>
```

#### components查找规则
feather首先会对所有components目录中包当中的**.json文件进行分析，提取main属性，并缓存。

bower.json
```js
{
    "name": "bootstrap",
    "main": "lib.js",
    //其他属性
}
```

当使用某一个文件时，无论是否是全路径还是段路径，都会直接先查找components中的包，如果找到正确的文件，则引用，否则会直接按照全路径做对应的处理
