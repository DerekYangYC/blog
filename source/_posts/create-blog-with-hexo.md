title: 使用Hexo搭建博客
date: 2014-08-06 14:27:00
tags: [hexo]
---

最近觉得用`markdown`来写点东西，是个相当愉快的过程，因此萌生了搭一个支持`markdown`的博客。比较来比较去，觉得`github`+`Hexo`比较方便快捷，而且够geek。

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



##同步




  [1]: https://github.com/hexojs/hexo/issues/632
  [2]: http://hexo.io/docs/configuration.html
  [3]: http://hexo.io/docs/commands.html