# linux-ssr
备份知网网上找到的在Linux环境（Ubuntu18.04）可用的ssr客户端配置软件

1. 首先克隆ssr项目并切换到对应路径：`git clone https://github.com/ouening/linux-ssr.git && cd linux-ssr` 
2. 修改执行权限：`chmod a+x ssr.sh`
3. 安装ssr:`./ssr.sh install`
4. 配置ssr：`./ssr.sh config`（使用vim编辑代理内容，如代理服务器，服务器端口，本地端口（插件switchomega需要做相应配置），密码，加密协议，混淆等）
5. 保存之后退出，可用注意到会自动检测所用代理是否正常连接

5.1 如果使用chacha加密，需要另外下载libsodium编译安装：`wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz`；

5.2 如果提示安装proxychains4来进行代理服务器网速测试，在Ubuntu中直接安装即可：`sudo apt install proxychains4`

6. 启动ssr: `./ssr.sh start`（貌似我没有执行这个命令前面config之后就可以了，火狐浏览器安装SwhichOmega插件，配置修改为`sock5,127.0.0.1:1080`）
7. 停止ssr: `./ssr.sh stop`
8. 卸载ssr: `./ssr.sh uninstall`

其实大家可以查看ssr.sh源码可以发现其另外克隆了项目地址：https://github.com/shadowsocksrr/shadowsocksr.git，并将其放到了路径`$HOME/.local/share/shadowsocksr`，代理配置文件`config.json`默认放置在`$HOME/.local/share/shadowsocksr/config.json`
