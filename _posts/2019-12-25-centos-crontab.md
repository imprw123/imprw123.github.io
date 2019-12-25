手把手教你在Github上建立自己的个人博客网站

原创置顶 Marcus灬Li 发布于2017-08-30 14:26:30 阅读数 46764  收藏
展开
 
概述

之前闲着没事,就利用Github建了一个个人博客网站,效果还不错,今天就来分享一下. 
建立自己个人博客网站的好处: 
1.面试装逼,这个不必多说… 
2.把平时积累的知识和项目记录下来,方便日后查看使用 
3.不受其他博客平台的限制

准备工作

开始之前,先大致介绍一下用到的技术和相关概念

Github是什么:

GitHub是一个利用Git进行版本控制、专门用于存放软件代码与内容的共享虚拟主机服务,很多人都把它称作程序员的同性交友网站,具体为啥这么叫我也不知道

GitHub Pages是什么？

Github Pages设计的初衷是为托管在GitHub上的项目提供介绍页面,开发者们可以通过GitHub Pages为他们的每一个项目创建一个用于介绍该项目的静态网站,不过由于他的空间免费而且稳定,因此用它搭建一个个人博客网站是再好不过了.

Git是什么？

Git是一个开源的分布式版本控制系统,可以有效、高速的处理从很小到非常大的项目版本管理.它的作用 
和Svn类似,就是一个版本控制的工具,用它可以将我们写的代码提交到Github上.

Jekyll是什么？

jekyll是一个简单的免费的Blog生成工具,将纯文本转化为静态网站和博客;由于咱们的GitHub Pages生成的是静态页面,每次更新博客都需要手动更改HTML,这就使得每次写博客都变得很麻烦,而用了这个工具以后,它会根据预先设置好的格式来生成博客内容,你就无需关心html代码,只需要把重心放在博客的写作上.

Liquid是什么?

Liquid是一种模板语言,可以在HTML页面中使用它;而他的作用就是使用标记、对象和过滤器的组合来加载一些动态内容.

废话不多说,下面来讲讲大致流程 
1.登陆你的个Github账号(注册的话这里就不讲了…) 
2.新建一个仓库用来保存个人网站项目 
3.把做好的个人网站上传到Github上 
4.上传成功后,根据域名来访问你的主页

入门案例-Hello Github

创建仓库

先登陆你的Github账号,没有账号的自己去注册一个(注册过程这里就不讲了),如下图新建一个仓库 


Repository name就是你的仓库名,这个仓库名必须按图中的格式来写,到时候访问的地址就是这个了,至于下面的Initialize this repository with a README这里,想搞就搞一下,我这里由于是演示就不弄了

配置

好了,经过上面的步骤咱们的Github仓库就算是建好了,下面要来讲讲本地怎么配置了;需要用到Git这个工具,请提前准备好.

一.创建一个本地仓库

1.找一个目录来作为你本地的仓库,比如我的是”F:\Cloud”,那么就在Cloud文件夹下初始化仓库.

2.初始化仓库的方式有两种,一种是用git的图形化界面来创建,另一种是用git命令来初始化,这里我选用图形化界面的方式来创建(极(lan)力(ren)推(bi)荐(bei));

3.来到Cloud目录下右键选择Git GUI Here–>选择Create New Repository

二.配置SSH Key

1.还是用Gui的形式来创建,在help中选择Show SSH key,点击Generate Key(期间啥都不用填,只需要下一步)来生成key

2.把生成的key填写到Github中,在Settings的SSH and GPG keys那里填,title随便写,主要是用来注明的,如图 


三.用户配置

使用git命令的方式来配置,右键选择Git Bash Here打开命令窗口,作如下配置

git config –global user.name “你的Github用户名” 
git config –global user.email “你的Github邮箱地址”
上传代码

一.写代码(index.html)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style type="text/css">
        h1{
            text-align: center;
            font-size: 50px;
        }
    </style>
</head>
<body>
    <h1>Hello Github</h1>   
</body>
</html>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
二.提交代码到Github仓库

1.在本地做一次提交(以命令行的方式)

git add . 
git commit -m “This is the message describing the commit”添加commit信息
2.把项目提交到Github上

git remote add origin 你的远程仓库地址(git@github.com:MarcusKun/io.git) 
注:在创建好Github仓库后有两个地址,一个是https的地址,另一个是SSH地址,也就是上面这个地址. 
git push -u origin master(执行这个之前必须先在本地做一次提交操作)


3.配置Github Pages 
在自己仓库那里找到Settings,配置Github Pages,如下图 


4.通过Github Pages那里给的地址访问自己的网页 


进阶使用-使用Jekyll来打造自己的个人博客

概述

经过上面的步骤,相信大家已经可以用Github来生成自己的静态网站了,可是毕竟咱们是要打造博客网站啊,不可能每次都用html语法来写博客吧;好了,这个时候就要用到Jekyll这个工具了,有一点要强调的是,我这里不会讲解从头打造一个个人博客网站,而是利用别人提供的Jekyll模板来制作,如果想深入学习的同学可以自行学习Jekyll以及Liquid

一个标准的使用Jekyll工具生成的网站,其目录结构一般是像这样的

├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
简单介绍一下每个目录和文件的作用

文件 / 目录	描述
_config.yml	保存配置数据。很多配置选项都会直接从命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。
_drafts	drafts 是未发布的文章。这些文件的格式中都没有 title.MARKUP 数据。学习如何使用 drafts.
_includes	你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签 {% include file.ext %} 来把文件 _includes/file.ext 包含进来。
_layouts	layouts 是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。 这将在下一个部分进行介绍。标签 {{ content }} 可以将content插入页面中。
_posts	这里放的就是你的文章了。文件格式很重要，必须要符合: YEAR-MONTH-DAY-title.MARKUP。 The permalinks 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。
_data	放一些其他配置文件,必须是.yml或者.yaml格式的,比如有一个文件叫members.yml,如果想引用这个文件里的内容就通过site.data.membres来引用
_site	一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的 .gitignore 文件中。
应用

第一步:去JekyllThemes下载一个自己喜欢的模板 
第二步:按照之前的步骤把下载好的模板上传到自己的Github仓库中 
第三步:在_posts文件夹中放入自己写好的博客,文件名必须是日期-标题名,例如:2016-10-25-我的第一篇博客 
第四步:上传博客到Github中即可访问自己的博客

参考

Liquid语法:https://help.shopify.com/themes/liquid 
Jekyll中文网:http://jekyll.com.cn/ 
Git官网:https://git-scm.com/

点赞 30
————————————————
版权声明：本文为CSDN博主「Marcus灬Li」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u012168038/article/details/77715439