# linux-ssr
备份知网网上找到的在Linux环境（Ubuntu18.04）可用的ssr客户端软件

1. 首先克隆ssr文件：git clone ssr.sh
2. 修改执行权限：chmod a+x ssr.sh
3. 安装ssr:./ssr.sh install
4. 配置ssr：./ssr.sh config（使用vim编辑代理内容，如代理服务器，服务器端口，本地端口（插件switchomega需要做相应配置），密码，加密协议，混淆等）
5. 保存之后退出，可用注意到会自动检测所用代理是否正常连接
6. 启动ssr: ./ssr.sh start（貌似我没有执行这个命令前面config之后就可以了，火狐浏览器安装SwhichOmega插件，配置修改为sock5,127.0.0.1:1080）
7. 停止ssr: ./ssr.sh stop
8. 卸载ssr: ./ssr.sh uninstall
