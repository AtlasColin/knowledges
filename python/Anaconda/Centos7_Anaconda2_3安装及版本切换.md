#CentOS7下Anaconda的安装与版本切换

## 1.   安装Anaconda2和Anaconda3

```shell
./Anaconda2-4.1.1-Linux-x86_64.sh
```

其中可选择安装位置以及选择是否将其写入环境变量，该处为`~/.bashrc` (可以不写入，后面地址改变)

##2.   安装pyenv

解压pyenv-1.0.9.tar.gz，`tar–xf  pyenv-1.0.9.tar.gz` 将解压后的文件夹命名为.pyenv，并放在/opt目录下(root模式，user模式建议放在$HOME目录下，下面的目录对应修改)

更改环境变量：（root）`gedit  /etc/profile` （user）`getdit  ~/.bashrc`

```
export PYENV_ROOT=/opt/.pyenv

export PATH=$PATH:$PYENV_ROOT/bin:$PYENV_ROOT/shims

eval "$(pyenvinit -)"
```

##**python版本查看**

查看当前已经安装了的python版本：

```shell
pyenv versions
```

将Anaconda2和Anaconda3的安装文件夹放在/opt/.pyenv/versions目录（可通过建立软链接`ln –s $ANACONDA_PATH   /opt/.pyenv/versions/anaconda2`）下，再次执行`pyenv versions` 

输出：

```shell
\* system (set by/opt/.pyenv/version)
  anaconda2
  anaconda3
```

##3.安装 pyenv virtualenv插件

解压pyenv-virtualenv-1.0.0.tar.gz，`tar –xfpyenv-virtualenv-1.0.0.tar.gz` ，将解压后的文件夹放在/opt/.pyenv/plugins文件夹下

```
[heroin@localhost plugins]$ pwd

/opt/.pyenv/plugins

[heroin@localhost plugins]$ ls

pyenv-virtualenv-1.0.0  python-build
```

添加`eval "$(pyenv virtualenv-init -)"`到环境变量 (root) gedit /etc/profile  (user) gedit ~/.bashrc

`source /etc/profile`后就可以用以下命令进行anaconda版本和python版本的切换了

`pyenv activate anaconda2`

用 `pyenv deactivate` 解除激活。

> 如果执行pyenv activate anaconda2出现pyenv-virtualenv未正常启用的情况可重新激活环境变量，或将/opt/.pyenv文件夹重新拷贝并再次激活环境变量(可能每次都要重新激活)。更好的办法是在~/.bashrc末尾加入source /etc/profile

 

注:最好先安装pyenv，设置好环境变量后再将anaconda安装到其versions目录下。因为如上教程安装后发现pip无法使用，所以可能还有一些有关联的程序无法使用.尝试使用软链接方式也可以解决上述问题，这样无需将anaconda安装文件夹放到versions文件夹下，只要ln –s 建立软链接即可。

安装教程到此结束。可详见一下网址：<http://www.php230.com/1490199361.html>

 