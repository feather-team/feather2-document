## js组件包(components)



feather2中直接对bower包的安装进行了支持，以便更好的进行组件的管理， 因为bower的资源是非常丰富的，甚至可以支持github上的某一个仓库的分支。

但是bower包几乎都采用了amd或umd规范，甚至有些bower包的是没有规范的，而feather因为静态资源管理的问题，采用了commonjs规范，因此feather对其进行了一定的处理，尽可能的让bower中的包能够正常的运行。同时删除了bower包中无用的文件。

另外，在项目中支持直接在页面中引用某一个组件包，而不需要知道具体引用的包文件，就像npm结合node中的require一样，大大提高开发者的便捷

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

#### 包查找原理及规则
feather首先会对所有components目录中包当中的**.json文件进行分析，提取main属性，并缓存。
当使用某一个文件时，无论是否是全路径还是段路径，都会直接先查找components中的包，如果找到正确的文件，则引用，否则会直接按照全路径做对应的处理