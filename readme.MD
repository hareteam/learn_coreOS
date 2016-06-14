    安装步骤：模拟真机安装
  1.先写出网络配置文件
    sudo vi /etc/systemd/network/static.netwok
        [Match]
          Name=enp0s3 #可以通过执行ifconfig看到网卡名
        [Network]
          Address=192.168.1.158
          Gateway=192.168.1.1
          DNS=192.168.1.1
     sudo systemctl restart systemd-networkd
     先执行sudo coreos-install -C stable -d /dev/sda
     看一下他是从哪里下载安装文件和签名文件，把链接复制出来，从别的地方下载好
     在局域网架192.168.1.124设一台web服务器
     将cloud-config.yaml bz2 sig文件放在下载目录
     先执行wget http://192.168.1.124/1010.5.0/cloud-config.yaml
     后执行sudo coreos-install -C stable -d /dev/sda -b http://192.168.1.124 -c ./cloud-config.yaml
  2.下载iso镜像以及安装包.