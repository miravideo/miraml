# miraml

Miraml 是一个基础的描述视频制作的文件，可以用 XML 或者 JSON 等方式表示。

如下是一个基本的结构：
```xml
<miraml version="1.0">
    <canvas width="1080" height="720" beat="1">
        <scene>
            <image path="https://cos.mirav.cn/jianshuo/render.jpg" x="180rpx" y="180rpx" width="360rpx" height="240rpx">
            <video path="https://cos.mirav.cn/jianshuo/render.mp4" x="180rpx" y="180rpx" width="360rpx" height="240rpx">
            <text text="Sample Text" color="red" fontFamily="verdana" fontSize="30rpx" x="20rpx" y="20rpx">
        </scene>
    </canvas>
</miraml>
```
每一个 tag，都有一个必须的名称(name)，以及一些列属性构成，所有的属性都是可选的。

## tag
### miraml

* `version`: 现在只支持`1.0`

### canvas

* `width`: 画板宽度，缺省 1080
* `height`: 画板高度，缺省 1080
* `engine`: 渲染引擎。miraml支持多种渲染方式，可选值是 `mirajson`  和 `mirajsonlite` 缺省 `mirajson`,
* `fps`: 输出 FPS，缺省 `25`,

另外，如果是 mirajson 引擎，支持如下给 FFMPEG 传递的参数：
* `crf`: 23,
* `inputOptions`: FFMPEG 命令的输入参数 '',
* `outputOptions`: FFMPEG 命令的输出参数 '',
* `normalizeAudio`: 是否把音频的音量调整到一致，1,


### scene

* `duration`: `0`
* `transition`: `fade`
* `transitionDuration`: `0.5`
* `bgcolor`: `black`

### text

* `text`: 文字
* `color`: 文字颜色
* `x`: 文字中心点的 x 坐标 `180rpx`
* `y`: 文字中心点的 y 坐标`520rpx`
* `width`: `360rpx`
* `align`: `center`
* `backgroundColor`: `white`
* `fontSize`: `26rpx`
* `fontFamily`: `思源黑体CN-Bold.otf`
* `stroke`: `black`
* `strokeThickness`: `3rpx`
* `tts`: `true`
* `volume`: `1`
* `voice`: `volcengine_zh_female_qingxin`
* `start`: 在本 scene 中开始的时间。缺省 `2`
* `end`: 在本 scene 中结束的时间。缺省 `2`
* `anchor`: 中心点的位置。比如 0 意味着左上角，0.5意味着中心点。缺省 `0.5`
* `fontStyle`: `normal`
* `fontVariant`: `normal`
* `fontWeight`: `normal`
* `letterSpacing`: `0`
* `lineHeight`: `0`
* `lineJoin`: `miter`
* `miterLimit`: `10`
* `padding`: `0`
* `textBaseline`: `alphabetic`
* `trim`: `false`
* `whiteSpace`: `pre`
* `wordWrap`: `false`
* `wordWrapWidth`: `360rpx`
* `leading`: `0`
* `fillGradientType`: `0`
* `fillGradientStops`: `[]`
* `breakWords`: `true`
* `dropShadow`: `false`
* `dropShadowAlpha`: `1`
* `dropShadowAngle`: `Math.PI / 6`
* `dropShadowBlur`: `0`
* `dropShadowColor`: `black`
* `dropShadowDistance`: `5`

## video

* `path`: ``
* `width`: `360rpx`
* `height`: `720rpx`
* `x`: `180rpx`
* `y`: `180rpx`
* `audio`: 是否包含背景的音乐，0 是不包含， 1 是包含。缺省 `0`
* `start`: 视频在本 scene 中开始的时间 `0`
* `end`: 视频在本 scene 中结束的时间 `0`
* `ss`: 对于视频是进行剪裁的开始时间，-1 为不剪裁`-1`
* `to`: 对于视频是进行剪裁的结束时间，-1 为不剪裁`-1`

 ## image

* `path`: ``
* `width`: `360rpx`
* `height`: `720rpx`
* `x`: `180rpx`
* `y`: `320rpx`
* `start`: 在本 scene 中开始的时间。缺省 `2`
* `end`: 在本 scene 中结束的时间。缺省 `2`


## 度量

所有支持长度的度量，比如 `width`, `height`, `x`, `y`, `fontSize` 等，都支持如下几种单位：
* 数字 或者 `px` - 像素
* `rpx` - relative pixel，定义画布的宽度为360rpx，然后计算实际长度
* `vw` - viewport width，定义画布的宽度为100vw，然后计算实际长度
* `vh` - viewport width，定义画布的高度为100vh，然后计算实际长度

所有支持时间的属性，都支持如下单位
* 数字或者`s` - 秒
* `beat` - 以画布的 beat 为单位计算实际时长，比如 `beat="3s"`, `end="2beat"`  就等同于 `end="6s"`

特例： 只有 canvas 的 width，height 不可以使用 rpx 、vh 、 vw 单位， canvas 的 beat 不可以使用 beat 单位
