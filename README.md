# BlockChain-nebulasio

# 安装星云链

* [Nebulas 101 - 01 编译安装星云链](https://github.com/nebulasio/wiki/blob/master/tutorials/%5B%E4%B8%AD%E6%96%87%5D%20Nebulas%20101%20-%2001%20%E7%BC%96%E8%AF%91%E5%AE%89%E8%A3%85.md)

## 安装GIT

```
sudo apt-get update
sudo apt-get install git
```

If have question about `apt-get update`,you can try ....


## 安装GO

```
export PATH=$PATH:/usr/local/go/bin
export GOPATH=/path/to/you/workspace
```

After you update `/etc/profile`,you must try `source /etc/profile` if you don't want to restart.

### su root

init you `su root` password

```
sudo passwd root
```

## shared libraries error

```
./neb: error while loading shared libraries: librocksdb.so.5.13: cannot open shared object file: No such file or directory
```

```
# 1.将用户用到的库统一放到一个目录，如 /usr/loca/lib
cp libXXX.so.X /usr/loca/lib/           

# 2.向库配置文件中，写入库文件所在目录
vim /etc/ld.so.conf.d/usr-libs.conf    

/usr/local/lib  

# 3.更新/etc/ld.so.cache文件
ldconfig  
```


## Reference

* [https://github.com/nebulasio/wiki/blob/master/tutorials](https://github.com/nebulasio/wiki/blob/master/tutorials)

* [shared libraries error](https://blog.csdn.net/yjk13703623757/article/details/53217377)


