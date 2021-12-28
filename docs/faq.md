# 常见问题

## 支持哪些字体？如果我想添加字体怎么办？

字体列表在这里：http://mar.mirav.cn/hola/available_fonts 
如果有希望使用但是不支持的字体，现在可以联系我们，提供字体文件，我们帮你添加到系统里面。
晚一些会给自助添加字体的功能。

## 声音支持淡入淡出吗？

支持。例子： https://cos.mirav.cn/cocafe/sample_159.htm
<audio path="https://cos.mirav.cn/jianshuo/beats.mp3" start="1" fadeIn="2" fadeOut="5" />

声音放在 canvas 之下可以从头到尾播放，放在scene之下可以在本场景播放

## 是否支持两段或者多段音乐联播？

支持。比如有两个音乐，希望分别前10秒钟播放·音乐1`的第20秒到30秒，后面10秒播放`音乐2`的40到50秒：

<audio ss="20" to="30" start="0"/>
<audio ss="40" to="50" start="10"/>

