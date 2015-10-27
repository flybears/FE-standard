# 项目目录结构

## 1 大型前端项目开发

``` 
|-- frame		前端组件框架名称
		|-- doc 		组件api使用文档       
        |-- fonts		字体图标
        |-- utils		工具类(模板渲染引擎、时间工具类等等)
        |-- images		图片库
        |-- less		less文件
        |-- vendor		第三方插件库(echarts、hightcharts等)
        |-- lib			基础库(jquery、underscore以及自定义库等等)
        |-- i18n		国际化
|-- project		前端项目名称		
        |-- assets		框架压缩文件夹
        |-- i18n		国际化
        |-- widget		与项目相关的自定义组件
        |-- mock-data   模拟json数据文件夹
        |-- commons		公共文件夹
        		|-- assets		和项目有关的widget、css压缩在此文件夹
                |-- utils		工具类
                |-- vendor		第三方插件库
                |-- lib			基础库
        |-- images		图片库
        |-- css		less文件
        |-- src			业务源码
        		|-- bz1			业务名称
            			|--js		js文件夹
                        |-- tpl		模板文件
                        |-- css		css文件

                |-- bz2
                        |--js
                        |-- tpl
                        |-- css
```



## 2 中小型项目开发

``` 
|-- 项目名
		|-- assets		项目发布目录
        		|-- css	
                |-- js
                |-- fonts
                |-- images
                |-- src
        |-- i18n		国际化
        |-- fonts		图标字体
        |-- widget		自定义组件库
        |-- mock-data	模拟数据
        |-- images		图片文件夹
        |-- less		less文件夹
        |-- commons		公共文件化
        		|-- utils		工具类
                |-- vendor		第三方插件
                |-- lib			基础库
        |-- src			业务代码
        		|-- bz1			业务名
                		|--js			js文件夹
                        |--tpl			模板文件
                        |--css			css文件
```