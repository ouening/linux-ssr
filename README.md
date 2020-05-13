# linux-ssr
备份网上找到的在Linux环境（Ubuntu18.04）可用的ssr客户端配置软件

1. 首先克隆ssr项目并切换到对应路径：`git clone https://github.com/ouening/linux-ssr.git && cd linux-ssr` 
2. 修改执行权限：`chmod a+x ssr.sh`
3. 安装ssr:`./ssr.sh install`
4. 配置ssr：`./ssr.sh config`（使用vim编辑代理内容，如代理服务器，服务器端口，本地端口（插件switchomega需要做相应配置），密码，加密协议，混淆等）
5. 保存之后退出，可用注意到会自动检测所用代理是否正常连接

5.1 如果使用chacha加密，需要另外下载libsodium源码编译安装：`wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz`；

5.2 如果提示安装proxychains4来进行代理服务器网速测试，在Ubuntu中直接安装即可：`sudo apt install proxychains4`

6. 启动ssr: `./ssr.sh start`（貌似我没有执行这个命令前面config之后就可以了，火狐浏览器安装SwhichOmega插件，配置修改为`sock5,127.0.0.1:1080`）
7. 停止ssr: `./ssr.sh stop`
8. 卸载ssr: `./ssr.sh uninstall`

其实大家可以查看ssr.sh源码可以发现其另外克隆了项目地址：https://github.com/shadowsocksrr/shadowsocksr.git，并将其放到了路径`$HOME/.local/share/shadowsocksr`，代理配置文件`config.json`默认放置在`$HOME/.local/share/shadowsocksr/config.json`

-------
在主流的Linux系统下，还可以更方便的使用图像界面版本`electron-ssr`：https://github.com/qingshuisiyuan/electron-ssr-backup，安装方式为：
```bash
sudo apt install libcanberra-gtk-module libcanberra-gtk3-module gconf2 gconf-service libappindicator1
sudo apt-get install libssl-dev
sudo apt install python
wget -N --no-check-certificate https://dl.ssrss.club/electron-ssr-0.2.6.deb
sudo dpkg -i electron-ssr_0.2.6.deb
wget --no-check-certificate -N "https://github.com/jedisct1/libsodium/releases/download/1.0.17/libsodium-1.0.17.tar.gz"
tar -xzf libsodium-1.0.17.tar.gz && cd libsodium-1.0.17
./configure --disable-maintainer-mode && make -j2 && make install
echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf
sudo ldconfig
```
但笔者在**Jetson Nano**开发板中无法使用，因为虽然是ubuntu系统，但是硬件系统是arm版本的，不是通用的amd64等常见架构。这种情况下使用命令行版本的ssr就派上用场了，最后还可以在**`Startup Applications`** 中设置开机自启动：设置命令`sh /home/jetson/ssr/ssr.sh start`即可
