hl
=====

从 Haskell.org 官网 fork 而来。

## 如何修改页面

如果你想要贡献内容请首先阅读以下内容。

All pages that are produced by markdown
所有页面都由[这里的 Markdown 文档](https://github.com/haskell-infra/hl/tree/master/static/markdown)生成。
贡献新内容首先需要 fork 这个项目并发起 Pull Request，如果合适的的话将会在短时间内合并重新部署。

如果你的提交中含有定制代码，那可能需要等到下一个构建执行才可能生效。也许你需要看一下先看一下[架构设计](#architecture)。

如果你想要在 Markdown 中插入 Haskell 代码，可以这样写：

    ``` haskell
    main = putStrLn "Hello, World!"
    ```

如果你想要在 Haskell 页面中插入示例代码可以这样写：

``` haskell
haskellPre "main = print 123"
haskellCode "peyton `simon` jones"
```

Pre 代表 `<pre>` HTML 块，Code 指 `<code>` 标签片段。

## 如何构建

clone 项目代码：

    $ git clone git@github.com:haskell-infra/hl.git

搭建沙盒环境：

    $ cabal sandbox init

安装依赖并构建：

    $ cabal install --only-dependencies
    $ cabal build

大功告成！

## 本地运行

启动路径 http://localhost:1990/。

手动运行二进制程序：

    $ dist/build/hl/hl

在 GHCi 中运行：

    > :l DevelMain
    > DevelMain.update

Run this every time you want to update the web handler in-place, as in
[this demo](https://github.com/chrisdone/ghci-reload-demo).

如果你使用 Emacs，可以这样绑定快捷键：

``` lisp
(define-key html-mode-map [f12] 'haskell-process-reload-devel-main)
```

按下 f12 即可构建并重新启动。

## 架构设计

这个项目结构组织遵守 Yesod 和 MVC 模式。

* HL.Model.\* -- [models](https://github.com/haskell-infra/hl/tree/master/src/HL/Model)
* HL.View.\* -- [views](https://github.com/haskell-infra/hl/tree/master/src/HL/View)
* HL.Controller.\* -- [controllers](https://github.com/haskell-infra/hl/tree/master/src/HL/Controller)

模板使用了 [Lucid](https://github.com/chrisdone/lucid)，现在并不依赖数据库。

## 样式规范

本项目代码遵照[这个规范](https://github.com/chrisdone/haskell-style-guide)，但是并不要求你遵守这个规范，我们会在接收到补丁后将其规范化。
