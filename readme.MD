##先配置目标机器
&emsp;&emsp;先设定主机的IP`sudo vi /etc/systemd/network/static.netwok`
```javascript

    [Match]
      Name=enp0s3 #可以通过执行ifconfig看到网卡名
    [Network]
      Address=192.168.1.158
      Gateway=192.168.1.1
      DNS=192.168.1.1
```
&emsp;&emsp;重新启动服务`sudo systemctl restart systemd-networkd`  


##收集服务器资料并且下载要用到的文件
&emsp;&emsp;然后执行`sudo coreos-install -C stable -d /dev/sda`，看一下他是从哪里下载安装文件和签名文件，把链接复制出来，从别的地方下载好后
     在局域网架设一台web服务器，将cloud-config.yaml(user-data) bz2 sig文件放在下载目录  


##开始安装     
&emsp;&emsp;然后在目标机器上先执行`wget http://192.168.1.124/1010.5.0/cloud-config.yaml`。
&emsp;&emsp;然后
     `sudo coreos-install -C stable -d /dev/sda -b http://192.168.1.124 -c ./cloud-config.yaml`
