# 使用 MiraML 制作 NFT 相关的视频教程

NFT 的所有 token 天生有结构化的信息，而且数量众多，可以使用 MiraML 自动化的为每一个 NFT 生成视频。

```html
<!--
    MiraML 支持变量，如下把 contract id 赋值给一个变量，
    在本文档里面可以多次使用
-->
{% set contract_id = '0xc2c747e0f7004f9e8817db2ca4997657a7746928' %}

<!--
    MiraML 支持一系列的函数，可以从外部获取数据。列表在这里。
    比如 set data = read_json(url) 就可以给一个 url ，从这个URL的API获取数据，然后把数据返回
    之后就可以用这个变量来访问 API 返回值的内容，比如 data.name 就是这个 collection 的名字。

    在API的地址 https://api.opensea.io/api/v1/asset_contract/0xc2c747e0f7004f9e8817db2ca4997657a7746928
    可以看到数据的结构
-->
{% set data = read_json('https://api.opensea.io/api/v1/asset_contract/' + contract_id) %}

<!--
    如下是建立一个宏（macro），以方便同样的代码在后面多次使用
-->
{% macro opensea_scene(api_url) -%}
    {{data.collection.banner_image_url}}#.jpg [effect="slideInLeft" effectTime="5beat" width="400vw" opacity="0.2"]
    {% for asset in read_json(api_url)['assets'] %}
        {{asset.name}} [start="{{loop.index0}}beat" end="{{loop.index0+1}}beat" x="5vw" y="5vh" anchor="0"  wordWrap="false" color="white" fontSize="30rpx"]
        {{asset.token_id}} [y="15vh" fontSize="20rpx"]
        {{((asset.last_sale.total_price|float)/1000000000000000000)|round(3)}} {{asset.last_sale.payment_token.symbol}}[y="90vh"]
        {{qrcode(asset.permalink)}} [width="36rpx" height="36rpx" x="90vw" y="90vh"]
        {{asset.image_url}}{{asset.image}}#.jpg [width="60vw" height="60vh" x="50vw" y="52vh"]
    {% endfor %}
{%- endmacro %}

<!--
    从这里开始正式的产生视频
    mp3 作为视频的背景音乐，可以循环播放
-->
https://cos.mirav.cn/jianshuo/beats.mp3

<style>
<h1 effect="slideInUp" effectTime="3s" />
<h2 effect="slideInRight" effectTime="5s" width="400vw"/>
</style>

<!--
    背景图片，来自 data.banner_image_url
    因为前面有一个 # ，就使用 h1 的风格，定义如上，就是
    effect="slideInRight" effectTime="5s"
    一个长度为5秒的从右向左的滑动进入
-->
## {{data.collection.banner_image_url}}#.jpg

<!--
    第一屏的欢迎页面
-->
# *一分钟了解 {{data.name}} 的最新信息*

<!--
    三个以上的 - 表示一个新的场景
-->
-------------------------------------------

<!--
    和第一屏几乎一样的背景，只是把透明度调低到 0.4
-->
## {{data.collection.banner_image_url}}#.jpg [opacity="0.4"]
<!--
    把描述翻译成中文显示并且读出来
-->
### *{{translate(data.description)}}*

<!--
    下面的部分和上面几乎是一样的
-->
-------------------------------------------

## {{data.collection.banner_image_url}}#.jpg [opacity="0.4"]
# *售价最高的5个NFT*

-------------------------------------------

<!--
    opensea_scene 就是上面定义的一个宏，可以在下面使用两次
-->
{{opensea_scene('https://api.opensea.io/api/v1/assets?asset_contract_address=' + contract_id + '&order_by=sale_price&order_direction=desc&offset=0&limit=5')}}

-------------------------------------------

## {{data.collection.banner_image_url}}#.jpg [effect="slideInRight" effectTime="5beat" width="400vw"  opacity="0.2"]
# *售价最低的5个NFT*

-------------------------------------------

{{opensea_scene('https://api.opensea.io/api/v1/assets?asset_contract_address=' + contract_id + '&order_by=sale_price&order_direction=asc&offset=0&limit=5')}}

-------------------------------------------

https://cos.mirav.cn/jianshuo/Ink-67358.mp4
# Thanks for watching
```

如上的代码生成如下视频：

> https://cos.mirav.cn/public2/video_469.mp4
