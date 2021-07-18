
# MAC通过PD安装的Ubuntu显示问题

### 背景

1. 在Macbook下安装虚拟机Parallels desktop。

2. Parallels desktop下安装了Window后，在图形中开启开启Retina后显示超棒。

3. 单安装了Ubuntu后，在图形中开启Retina显示后，图形字体特别小，不适合使用，显示细腻。

4. 不开启Retina显示，显示效果模糊，影响美观。

5. 开启Retina显示后，再在Ubuntu设置了缩放200%后显示超棒，非常细腻。

6. 但这种设置，当调整了Ubuntu虚拟机的窗口后，缩放失效，回到100%。

7. 研究发现Parallels desktop调整窗口后自动适应的原理是设置虚拟机的分辨率。

8. 因此我们要想办法固定缩放设置，在分辨率改变的时候不改缩放设置。

### 设置方法
1. 在Ubuntu->设置->图形中开启Retina显示。

2. 在Ubuntu->终端输入    
	- gsettings get org.gnome.desktop.interface scaling-factor
	- 表示查看缩放值

3. 在Ubuntu->终端输入    
	- gsettings set org.gnome.desktop.interface scaling-factor 2
	- 表示设置缩放值为2

4. 重启Ubuntu虚拟机生效

- 注意：缩放值不能设置小数，个人觉得在Retina屏幕上设置2倍刚刚好 👍