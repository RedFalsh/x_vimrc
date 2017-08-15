# x_vimrc
我的vimrc配置文件

# 下载：

git下载：
`git clone https://github.com/RedFalsh/x_vimrc.git`

# 使用方法：

## Windows：

1、复制autoload文件夹下面的plug.vim到VIM安装目录下的autoload文件夹下面

2、复制`vimrc`文件内容到`~/.vimrc`，即：`C:\Users\admin\.vimrc`

3、复制`vimrc.bundles`文件内容到`~/.vimrc.bundles`,即：`C:\Users\admin\.vimrc.bundles`

4、打开vim，输入命令：`:PlugInstall`开始安装插件。

## Linux：

1、复制autoload文件夹下面的plug.vim到 `~/.vim/autoload/`文件夹下面

`mkdir -p ~/.vim/autoload/`

`mkdir -p ~/.vim/bundle/`

`cp autoload/plug.vim ~/.vim/autoload/plug.vim`

2、复制`vimrc`文件内容到`~/.vimrc`

`cp vimrc ~/.vimrc`

3、复制`vimrc.bundles`文件内容到`~/.vimrc.bundles`

`cp vimrc.bundles ~/.vimrc.bundles`

4、打开vim，输入命令：`:PlugInstall`开始安装插件


* python高亮设置 --self高亮设置
安装完插件pyhton-syntax后，找此插件文件目录，修改文件夹下python.vim文件,windows路径`C:\Users\Administrator\.vim\bundle\python-syntax\syntax\python.vim`

如下：`self`颜色设置跟`import`一样
`
syn keyword pythonInclude       import
syn keyword pythonImport        import self
syn keyword pythonException     try except finally
syn keyword pythonOperator      and in is not or
`


