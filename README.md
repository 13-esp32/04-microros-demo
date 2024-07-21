0. docker ros2代理命令
docker run -it --rm -v /dev:/dev -v /dev/shm:/dev/shm --privileged --net=host microros/micro-ros-agent:humble udp4 --port 8090 -v4

# 6. 订阅速度话题
## 6.1 激活esp idf开发环境
cd ~
source ~/esp/esp-idf/export.sh
## 6.2 进入指定的项目目录
cd ~/esp/Samples/microros_sample/twist_subsciber
## 6.3 打开esp idf配置工具
idf.py menuconfig
## 6.4 设置demo的配置
### 6.4.1 micro ros setting --> ip地址
设置ip地址
### 6.4.2 micro ros setting --> wifi
设置wifi账户和密码
### 6.4.3 micro ros example-app
设置ros domain id of the micro-ros
## 6.5 编译
idf.py build
## 6.6 烧录
先把mina\par\bootload 拷贝到共享文件中
然后使用esp的烧录工具把文件烧到板子上
## 6.7 测试运行
先调用代理
然后运行 ros2 run yahboomcar_ctrl yahboom_key_board
按下相关的按键，esp32就是可以收到速度指令了
