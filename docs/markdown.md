# miraml - markdown

Miraml 是一个基础的描述视频制作的文件，支持markdown。

如下是一个基本的结构：
```
<!-- 图片 -->
https://wallpaperaccess.com/full/508751.jpg

# *这是1级标题*
## *这是2级标题*
### *这是3级标题*
#### *这是4级标题*
##### *这是5级标题*
###### *这是6级标题*
*这是普通文字*

---

https://wallpaperaccess.com/full/495111.jpg [width="256rpx" height="256rpx"]

    # *这是一级标题* [color="red" y="10vh"]
    ## *这是2级标题*
    ### *这是3级标题*
    #### *这是4级标题*
    ##### *这是5级标题*
    ###### *这是6级标题*
*这是普通文字*
```
> https://cos.mirav.cn/public2/canvasheig4547.mp4

## 标题
标题在行首使用 1-6 个 `#` 字符，对应于标题级别 1-6。例如：
```
这是普通文本
# 这是1级标题
## 这是2级标题
### 这是3级标题
#### 这是4级标题
##### 这是5级标题
###### 这是6级标题
```
> https://cos.mirav.cn/public2/canvasheigc026.mp4

## 语音播报
语音播报在文本左侧和右侧各使用 1 个 `*` 字符。例如：
```
# *语音播报*
*这是第一句话*
*这是第二句话*
*这是最后一句话*
```
> https://cos.mirav.cn/public2/canvasheiga64e.mp4
## 背景
可以直接输入图片/视频链接（若链接不是以 .文件格式 结尾，需要加 #.文件格式）
```
https://wallpaperaccess.com/full/508751.jpg
# *背景图片*
```
> https://cos.mirav.cn/public2/canvasheigc363.mp4

```
https://mira-1255830993.cos.ap-shanghai.myqcloud.com/public2/pexels-caroline-veronez-9917770.mp4
# *背景视频*
```
> https://cos.mirav.cn/public2/canvasheig88c9.mp4

## 场景分割
场景之间使用一行三个或以上 - 字符进行分割。例如：
```
# *场景分割*
---
https://wallpaperaccess.com/full/508751.jpg
# *这是第一个场景*
图片
---------------------
https://cos.mirav.cn/public2/pexels-caroline-veronez-9917770.mp4
# *这是第二个场景*
视频
---
https://wallpaperaccess.com/full/495111.jpg
# *这是最后一个场景*
图片
```
> https://cos.mirav.cn/public2/canvasheiga898.mp4

同时，--- 后面也可以添加属性标签，比如
```
{{tag('backgrounds')|random}}
--- [duration="5" transition="wipeleft" transitionDuration="1"]
{{tag('backgrounds')|random}}
*abc*
--- [duration="3" transition="wiperight" transitionDuration="1"]
{{tag('backgrounds')|random}}
*123*
---- [duration="2"]
{{tag('backgrounds')|random}}
*alpha*
```
> https://cos.mirav.cn/cocafe/canvasheiga490.htm

## 注释
注释行左侧使用 `<!--` ，右侧使用 `-->`。
```
# *注释*
<!-- 中间的都是注释 --->
```
> https://cos.mirav.cn/public2/canvasheig0c97.mp4

## 属性 (更多属性 -> README.md)
可以在行尾添加中括号 `[]` ，中括号内可自定义物体属性，格式为 `[attributeName1="attributeVal1" attributeName2="attributeVal2 attributeName3="attributeVal3""]` ，多组属性以空格分割。
```
<!-- 将图片长宽均设置为100rpx -->
https://wallpaperaccess.com/full/508751.jpg [width="100rpx" height="100rpx"]
# *tag 1* [color="white" y="10vh"]
## *tag 2*
### *tag 3*
tag 4
```
> https://cos.mirav.cn/public2/canvasheig936d.mp4
