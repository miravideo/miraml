# miraml - markdown

Miraml 是一个基础的描述视频制作的文件，支持markdown。

如下是一个基本的结构：
```
https://avatars.githubusercontent.com/u/2012831?s=48&v=4#.jpg

# *这是一级标题*
## *这是一级标题*
### *这是一级标题*
#### *这是一级标题*
##### *这是一级标题*
###### *这是一级标题*
*这是普通文字*

---

https://avatars.githubusercontent.com/u/2012831?s=48&v=4#.jpg

    # *这是一级标题* []
    ## *这是一级标题*
    ### *这是一级标题*
    #### *这是一级标题*
    ##### *这是一级标题*
    ###### *这是一级标题*
*这是普通文字*
```
> 

## 标题
标题在行首使用 1-6 个 # 字符，对应于标题级别 1-6。例如：
```
这是普通文本
# 这是1级标题
## 这是2级标题
### 这是3级标题
#### 这是4级标题
##### 这是5级标题
###### 这是6级标题
```
> https://cos.mirav.cn/public2/scene这是普通文d0b8460.mp4
## 语音播报
语音播报在文本左侧和右侧各使用 1 个 * 字符。例如：
```
# *语音播报*
*这是第一句话*
*这是第二句话*
*这是最后一句话*
```
> https://cos.mirav.cn/public2/video_459.mp4
## 背景
可以直接输入图片/视频链接（若链接不是以 .文件格式 结尾，需要加 #.文件格式）
```
https://avatars.githubusercontent.com/u/2012831?s=60&v=4#.jpg
# *背景图片*
```
> https://cos.mirav.cn/public2/video_374.mp4

## 场景分割
场景之间使用一行 --- 字符进行分割。例如：
```
# *场景分割*
---
https://avatars.githubusercontent.com/u/2012831?s=60&v=4#.jpg
# *这是第一个场景*
有图
---
# *这是第二个场景*
无图
---
https://avatars.githubusercontent.com/u/2012831?s=60&v=4#.jpg
# *这是最后一个场景*
有图
```
> https://cos.mirav.cn/public2/video_358.mp4

## 注释
注释行左侧使用 `<!--` ，右侧使用 `-->`。
```
# *注释*
<!-- 中间的都是注释 --->
```
> https://cos.mirav.cn/public2/video_197.mp4

## tag (更多tag -> README.md)
```
<!-- 将图片长宽均设置为100rpx -->
https://avatars.githubusercontent.com/u/2012831?s=48&v=4#.jpg [width="100rpx" height="100rpx"]
# *tag 1* [color="white" y="10vh"]
## *tag 2*
### *tag 3*
tag 4
```
> https://cos.mirav.cn/public2/video_560.mp4

## 代码块
同级递进的文本将共享同一tag
```
<!-- 同级递进的 3 个tag -->
    # *tag 1* [color="white" y="10vh"]
    ## *tag 2*
    ### *tag 3*
tag 4
```
> https://cos.mirav.cn/public2/video_591.mp4
