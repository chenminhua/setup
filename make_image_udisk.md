## 转换镜像
hdituil:是一个Mac OS上面处理镜像文件的命令,可以对镜像文件进行制作，验证和转换等...
我们知道DMG格式是Mac OS上常用的打包格式文件，需要把下载的Ubuntu安装文件（.iso）转换成(.dmg)格式的文件,方便在Mac OS上面进行操作，转换命令:

hdiutil convert -format UDRW -o ubuntu.iso ubuntu-14.04.5-desktop-amd64.iso

-format为生成文件的权限,UDRW :表示转换成有read/write的权限的镜像。

## 操作U盘
diskutil:操作本地磁盘，可以对磁盘进行卸载，挂载等操作。
列出当前挂载的磁盘，然后把u盘卸载掉  

diskutil list
diskutil unmountDisk /dev/disk5

## 把安装文件写入U盘
mv ubuntu.iso.dmg ubuntu.iso
sudo dd if=./ubuntu.iso of=/dev/rdisk5 bs=1m

## 销毁安装数据
sudo dd if=/dev/urandom of=/dev/rdisk5
