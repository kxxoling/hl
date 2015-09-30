### 1. 安装 GHC

GHC 有独立的许可证、FAQ 页面、下载链接以及变更纪录，根据你的操作系统，它可能提供了包管理器或者下载二进制安装包（比如在 Windows 上）来安装。

你可以手动下载并解压 .tar.gz/.zip 安装包来安装。

也可以[参照文档](https://ghc.haskell.org/trac/ghc/wiki/Building)下载源代码安装。

[下载 GHC →](https://www.haskell.org/ghc/download)

### 2. 安装 Cabal-install

安装 GHC 之后，你还需要安装 Haskell 包管理器：

[获取 Cabal →](http://hackage.haskell.org/package/cabal-install)

下载 tar.gz 文件，在解压后的目录中运行：

    $ sh ./bootstrap.sh

它将会自动下载并安装设置 Cabal 所必需的依赖。

还没结束，你需要把 `$HOME/.cabal/bin` 加入 PATH 中。你可以简单地编辑
`~/.bashrc` 并把下面这行加入其中：

    export PATH=$HOME/.cabal/bin:$PATH

现在，你应该可以正常使用 cabal 了：

    $ cabal --version
    cabal-install version 1.18.0.2
    using version 1.18.1.2 of the Cabal library

你可以这样更新安装包信息：

    $ cabal update

然后在沙盒中安装应用，这样就不会和其它项目产生冲突了：

    $ mkdir my-project
    $ cd my-project
    $ cabal sandbox init
    $ cabal install the-package-name
