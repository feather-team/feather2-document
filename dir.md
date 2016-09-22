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
