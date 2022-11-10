ubuntu disable wayland:
sudo nano /etc/gdm3/custom.conf


11/18课程思政学习实施总结
图文并茂
11/25信息化教学实施总结
图文并茂
大一17周往前调

ubuntu font:
1、下载缺失的字体文件，然后复制到 Linux 系统中的 /usr/share/fonts 文件夹中。

下载完成后，解压并进入目录中，继续执行：

$ sudo cp * /usr/share/fonts
2、执行以下命令，生成字体的索引信息：

$ sudo mkfontscale
$ sudo mkfontdir
3、运行 fc-cache 命令更新字体缓存。

$ sudo fc-cache
4、重启 wps 即可，字体缺失的提示不再出现。


Ubuntu22.04, EasyConnect:
easyconnect 在 ubuntu20 下无法打开，需要降级 pango 来解决问题，默认 easyconnect 依赖的 pango 库：
$ cd /usr/share/sangfor/EasyConnect
$ ldd EasyConnect | grep pango
libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007f9713518000)
libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007f971337e000)
libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007f97116d8000

将降级的库拷贝到 /usr/share/sangfor/EasyConnect 中，千万不要将降级的库覆盖 /lib/x86_64-linux-gnu / 下相关库，会导致系统重启后无法进入界面。降级库下载地址：

链接：http://feihu.otmiao.com/wp-content/uploads/2021/05/libpango.zip

创建 EasyConnect 的依赖的链接文件
$ cd /usr/share/sangfor/EasyConnect
$ sudo ln -sn /usr/share/sangfor/EasyConnect/libpangoft2-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpangoft2-1.0.so.0
$ sudo ln -sn /usr/share/sangfor/EasyConnect/libpangocairo-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpangocairo-1.0.so.0
$ sudo ln -sn /usr/share/sangfor/EasyConnect/libpango-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpango-1.0.so.0
$ ldd EasyConnect | grep pango
libpangocairo-1.0.so.0 => /usr/share/sangfor/EasyConnect/./libpangocairo-1.0.so.0 (0x00007f71d007a000)
libpango-1.0.so.0 => /usr/share/sangfor/EasyConnect/./libpango-1.0.so.0 (0x00007f71cfce2000)
libpangoft2-1.0.so.0 => /usr/share/sangfor/EasyConnect/./libpangoft2-1.0.so.0 (0x00007f71cde3a000)
$ ./EasyConnect

sudo ln -sn /usr/share/sangfor/EasyConnect/libpangoft2-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpangoft2-1.0.so.0
sudo ln -sn /usr/share/sangfor/EasyConnect/libpangocairo-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpangocairo-1.0.so.0
sudo ln -sn /usr/share/sangfor/EasyConnect/libpango-1.0.so.0.4000.14 /usr/share/sangfor/EasyConnect/libpango-1.0.so.0

v2ray, qv2ray
install qv2ray on ubuntu store
install v2ray core:
unzip v2ray-linux-64.zip to ~/.config/qv2ray/vcore/

onedrive:
https://github.com/abraunegg/onedrive/