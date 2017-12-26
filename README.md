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

## Windows安装会出现的问题

1.新建build文件夹

2.打开命令窗口，进入上一步的build文件夹

3.执行命令，用cmake编译YouCompleteMe插件下的第三方程序(因为Program Files中间有空格,所以用双引号调用cmake.exe程序)

`"C:\Program Files\CMake\bin\cmake.exe" -G "MinGW Makefiles" . C:\Users\admin\.vim\bundle\YouCompleteMe\third_party\ycmd\cpp`

会得到如下结果:

```
min\.vim\bundle\YouCompleteMe\third_party\ycmd\cpp
-- The C compiler identification is GNU 6.3.0
-- The CXX compiler identification is GNU 6.3.0
-- Check for working C compiler: C:/mingw-w64/x86_64-6.3.0-posix-seh-rt_v5-rev2/mingw64/bin/gcc.exe
-- Check for working C compiler: C:/mingw-w64/x86_64-6.3.0-posix-seh-rt_v5-rev2/mingw64/bin/gcc.exe -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: C:/mingw-w64/x86_64-6.3.0-posix-seh-rt_v5-rev2/mingw64/bin/g++.exe
-- Check for working CXX compiler: C:/mingw-w64/x86_64-6.3.0-posix-seh-rt_v5-rev2/mingw64/bin/g++.exe -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found PythonLibs: C:/Python27/libs/libpython27.a (found suitable version "2.7.14", minimum required is "2.6")
NOT using libclang, no semantic completion for C/C++/ObjC will be available
-- Configuring done
-- Generating done
-- Build files have been written to: C:/Users/admin/.vim/bundle/YouCompleteMe/build
```

4.执行命令，用cmake编译生成ycm_core(因为Program Files中间有空格,所以用双引号调用cmake.exe程序)

`C:\mingw-w64\x86_64-6.3.0-posix-seh-rt_v5-rev2\mingw64\bin\mingw32-make.exe ycm_core`

得到如下结果:

```
[ 89%] Building CXX object ycm/CMakeFiles/ycm_core.dir/LetterNode.cpp.obj
[ 91%] Building CXX object ycm/CMakeFiles/ycm_core.dir/LetterNodeListMap.cpp.obj
[ 92%] Building CXX object ycm/CMakeFiles/ycm_core.dir/PythonSupport.cpp.obj
[ 94%] Building CXX object ycm/CMakeFiles/ycm_core.dir/Result.cpp.obj
[ 95%] Building CXX object ycm/CMakeFiles/ycm_core.dir/Utils.cpp.obj
[ 97%] Building CXX object ycm/CMakeFiles/ycm_core.dir/versioning.cpp.obj
[ 98%] Building CXX object ycm/CMakeFiles/ycm_core.dir/ycm_core.cpp.obj
[100%] Linking CXX shared library C:\Users\admin\.vim\bundle\YouCompleteMe\third_party\ycmd\ycm_core.pyd
[100%] Built target ycm_core
```
编译完成后将`C:\Users\admin\.vim\bundle\YouCompleteMe\third_party\ycmd\ycm_core.pyd`复制到`C:/Users/admin/.vim/bundle/YouCompleteMe/python/`文件夹下面

如果编译出错，根据错误信息，进行修改源程序即可，就是cpp文件夹下面的一些.c文件

5.编译完成后里面要设置下面两个才能使用,这里非常重要，不设置的话，用不了！！！

```
" 打开后台Python2支持的自动补全服务
let g:ycm_server_python_interpreter = 'C:\\Python27\\python2.exe'
" 添加Python2二进制运行程序
let g:ycm_python_binary_path = 'C:\\Python27\\python2.exe'
```

完整设置YouCompleteMe如下:

```
" YouCompleteMe {{{
    "youcompleteme  默认tab  s-tab 和自动补全冲突
    " let g:ycm_server_python_interpreter = 'C:\\Python35\\python3.exe'
    let g:ycm_server_python_interpreter = 'C:\\Python27\\python2.exe'
    " let g:ycm_python_binary_path = 'python.exe'
    let g:ycm_python_binary_path = 'C:\\Python27\\python2.exe'
    " let g:ycm_python_binary_path = 'C:\\Python35\\python3.exe'
    "let g:ycm_key_list_select_completion=['<c-n>']
    let g:ycm_key_list_select_completion = ['<Down>']
    "let g:ycm_key_list_previous_completion=['<c-p>']
    let g:ycm_key_list_previous_completion = ['<Up>']
    let g:ycm_complete_in_comments = 1  "在注释输入中也能补全
    let g:ycm_complete_in_strings = 1   "在字符串输入中也能补全
    let g:ycm_use_ultisnips_completer = 1 "提示UltiSnips
    let g:ycm_collect_identifiers_from_comments_and_strings = 1   "注释和字符串中的文字也会被收入补全
    let g:ycm_collect_identifiers_from_tags_files = 1
    " 开启语法关键字补全
    let g:ycm_seed_identifiers_with_syntax=1

    "let g:ycm_seed_identifiers_with_syntax=1   "语言关键字补全, 不过python关键字都很短，所以，需要的自己打开

    " 跳转到定义处, 分屏打开
    let g:ycm_goto_buffer_command = 'horizontal-split'
    " nnoremap <leader>jd :YcmCompleter GoToDefinition<CR>
    nnoremap <leader>jd :YcmCompleter GoToDefinitionElseDeclaration<CR>
    nnoremap <leader>gd :YcmCompleter GoToDeclaration<CR>

    " 引入，可以补全系统，以及python的第三方包 针对新老版本YCM做了兼容
    " old version
    if !empty(glob("~/.vim/bundle/YouCompleteMe/cpp/ycm/.ycm_extra_conf.py"))
        let g:ycm_global_ycm_extra_conf = "~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py"
    endif
    " new version
    if !empty(glob("~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py"))
        let g:ycm_global_ycm_extra_conf = "~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py"
    endif

    " 直接触发自动补全 insert模式下
    " let g:ycm_key_invoke_completion = '<C-Space>'
    " 黑名单,不启用
    let g:ycm_filetype_blacklist = {
        \ 'tagbar' : 1,
        \ 'gitcommit' : 1,
        \}
    let g:ycm_python_binary_path = 'C:/Python35/python3'
    let g:ycm_python_binary_path = 'python3'
" }}}

```

## python

### 高亮设置 --self高亮设置

安装完插件pyhton-syntax后，找此插件文件目录，修改文件夹下python.vim文件

windows路径:`C:\Users\Administrator\.vim\bundle\python-syntax\syntax\python.vim`

如下：`self`颜色设置跟`import`一样
```
syn keyword pythonInclude       import
syn keyword pythonImport        import self
syn keyword pythonException     try except finally
syn keyword pythonOperator      and in is not or
```


