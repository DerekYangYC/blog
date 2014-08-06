title: 使用Hexo搭建博客
date: 2014-08-06 14:27:00
tags: [hexo]
---

最近觉得用`markdown`来写点东西，是个相当愉快的过程，因此萌生了搭一个支持`markdown`的博客。比较来比较去，觉得`github`+`hexo`比较方便快捷，而且够geek。

##安装

由于我在在windows使用`hexo`，安装过程也略微叙述一下。安装`hexo`需要用到`git`和`node.js`，`git`和`node.js`的安装很简单，下载对应版本，一路next即可。`linux`命令行环境的模拟，可以利用`git shell`和`ConEmu`解决。

完成以后，输入如下命令即可安装`hexo`

```bash
$ npm install -g hexo
```
安装完毕后，进入一个目录，输入如下命令即可新建一个`hexo`工程：

```bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

值得注意的是，`npm install`不可缺少。否则的话会出现[生成页面错误][1]。

##配置

配置方面，大部分配置可参考[官网][2]。

要注意的是，默认情况`deploy`是空，需要手动加入。例如我们要`deploy`到`github`上：

```
deploy:
  type: github
  repo: git@github.com:DerekYangYC/derekyangyc.github.io.git
```

**尤其注意格式，冒号和值之间要预留一个空格！**


除了`deploy`，`theme`也是一个要修改的地方，因为默认的主题，实在太丑。

##使用

详细的使用也可参考[官网][3], 不过我觉得，`hexo`的使用还是相当简单，来来去去都是这几个命令：

```bash
$ hexo init
$ hexo clean
$ hexo g
$ hexo s
$ hexo d
```

个人觉得，每次`hexo g`前都`clean`一下，比较好


##同步

通过`hexo deploy`可以将本地博客部署到`github`上。
在部署前，根据上面`repo`的位置，新建一个`repo`：`derekyangyc.github.io`

每次部署，都会把`hexo`目录下的`public`文件夹，推送到`derekyangyc.github.io`这个`repo`

因为我的机器常使用`github`，这里省略了`ssh`的设置，详细可以看[这里](https://help.github.com/articles/generating-ssh-keys)

但这样并不能解决在多台机器写博客的问题，因为`derekyangyc.github.io`上仅仅存的是`hexo`的`public`文件夹。

解决的问题的方法有两个：

1. 利用`dropbox`等同步软件同步整个目录，但这样并不好。因为`public`等文件夹的文件经常改动，会引起不必要的同步。
2. 利用`github`保存整个`blog`目录。

```bash
$ cd blog
git init
git add .
git commit -m "add all files"
git remote add origin git@github.com:derekyangyc/blog.git
git push -u origin master
```

这样，在另外一台机器上只需要`clone`这个`repo`，然后进行修改再`push`回`github`，即可。


##多说

我用的皮肤[Tinny](https://github.com/zhanglun/hexo-theme/tree/master/Tinny)，已经从`disqus`改成`多说`；但这不意味着马上能用。

- 首先得去多说注册，并创建网站
- 然后获得`通用代码`
- 然后在`_config.yml`和`comment.ejs`下，更改对应的`short_name`

![](/img/duoshuo.png)

这样多说才能使用。否则，使用别人的皮肤容易也把多说的`short_name`也一并使用，会造成评论乱入，自己的博客下出现不属于自己的评论。


自此，博客才算基本搭好；一旦单搭好了博客，写东西可谓赏心悦目。

参考：

[http://syxiaqj.github.io/2014/02/19/introduce-hexo-theme/](http://syxiaqj.github.io/2014/02/19/introduce-hexo-theme/)

[http://ibruce.info/2013/11/22/hexo-your-blog/](http://ibruce.info/2013/11/22/hexo-your-blog/)

[http://zipperary.com/categories/hexo/](http://zipperary.com/categories/hexo/)


  [1]: https://github.com/hexojs/hexo/issues/632
  [2]: http://hexo.io/docs/configuration.html
  [3]: http://hexo.io/docs/commands.html