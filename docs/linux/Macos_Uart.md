## Mac终端自带screen连接串口

### 1、查看相关串口设备：

```shell
	命令：
	ls /dev/tty.*
	
	执行结果：
	/dev/tty.Bluetooth-Incoming-Port	
	/dev/tty.usbserial-14440
	/dev/tty.Yonxiner-Airpod-Wireles
```

### 2、连接串口设备

```shell
	screen 设备名 115200
	
	实例命令：
	screen /dev/tty.usbserial-14440 115200
```



## Mac终端minicom连接串口

### 1、安装brew

```shell
curl -LsSf http://github.com/mxcl/homebrew/tarball/master | sudo tar xvz -C/usr/local --strip 1
```
### 2、安装minicom

```shell
brew install minicom
```

### 3、配置minicom

```shell
minicom -s
```

### 4、启动minicom

```shell
minicom
```