##安装

feather2是基于nodejs进行开发的npm包，所以需要安装node，具体可见 [Node官网](https://nodejs.org)

安装node完成后，打开命令终端，进行feather2的安装

```sh
npm install -g feather2
```

等待执行结束后，可执行feather2命令，差看是否安装成功

```sh
feather2 -v
```

### 命令

执行feather2 -h|--help 查看feather2所支持的命令

```sh
feather2 -h
```

####* init
    
    init用于快速创建一个标准feather2项目，一个完整的feather2项目的目录结构大概如下：

    ```sh
├── components      #组件包
│   ├── backbone
│   │   ├── backbone.js
│   │   └── bower.json
│   └── underscore
│       ├── bower.json
│       └── underscore.js
├── conf
│   ├── conf.js     #2.0的核心配置文件
│   ├── deploy
│   │   └── local.js
│   ├── pack.json   #打包文件，对全局起作用
│   └── rewrite.js  #url重写文件
├── data            #测试目录，同1.x中的test目录
│   └── ajax
│       └── test.json
├── index.html
├── layout.html
├── pagelet         #pagelet目录，feather会对此目录中的文件进行特殊封装，此文件夹下的文件同widget
│   ├── ajax
│   │   ├── ajax.css
│   │   └── ajax.html
│   └── bigrender
│       ├── bigrender.css
│       ├── bigrender.html
│       └── bigrender.js
├── static
│   ├── index.css
│   └── index.js
├── test
│   └── test.html   #预览情况下才会产出，正式环境下不会产出，此目录用于测试，预览下于其他模板文件无异
└── widget
    ├── footer
    │   ├── footer.css
    │   └── footer.html
    └── header
        ├── header.css
        ├── header.html
        └── header.js
```

####* install 
    install命令用于安装ui组件，feather2中对bower进行了集成，以便用户更好，更快的安装组件，安装完成后，组件会被放置于components目录下进行统一管理。

    why is bower？ bower的资源非常丰富，甚至可以支持安装github上的某一个仓库的分支，并且能够自行处理依赖，就像使用npm安装feather2一样方便。同时，在项目中还可以像使用node中引用一个npm包一样引用 components组件，用户无需知道组件的main文件到底是什么，具体使用可见[components](./components.md)

    注：bower包几乎都采用了amd或umd规范，甚至有些bower包的是没有规范的，而feather因为静态资源管理的问题，采用了commonjs规范，因此feather对其进行了一定的处理，尽可能的让bower中的包能够正常的运行。同时删除了bower包中无用的文件。