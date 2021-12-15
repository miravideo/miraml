# 使用 MiraML 制作 NFT 相关的视频教程

NFT 的所有 token 天生有结构化的信息，而且数量众多，可以使用 MiraML 自动化的为每一个 NFT 生成视频。

{% set contract_id, contract_slug = '0xc2c747e0f7004f9e8817db2ca4997657a7746928', 'hashmasks' %}
{% set data = read_json('https://api.opensea.io/api/v1/asset_contract/' + contract_id) %}

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


https://cos.mirav.cn/jianshuo/beats.mp3
{{data.collection.banner_image_url}}#.jpg [effect="slideInRight" effectTime="5beat" width="400vw"]
# *一分钟了解 {{contract_slug}} 的最新信息* [effect="fadeInUp" effectTime="3beat"]

-------------------------------------------

{{data.collection.banner_image_url}}#.jpg [effect="slideInRight" effectTime="5beat" width="400vw"  opacity="0.2"]
## *{{translate(data.description)}}*

-------------------------------------------

{{data.collection.banner_image_url}}#.jpg [effect="slideInRight" effectTime="5beat" width="400vw"  opacity="0.2"]
# *售价最高的5个NFT* [effect="fadeInDown" effectTime="3beat" effectDelay="0"]

-------------------------------------------

{{opensea_scene('https://api.opensea.io/api/v1/assets?asset_contract_address=' + contract_id + '&order_by=sale_price&order_direction=desc&offset=0&limit=5')}}

-------------------------------------------

{{data.collection.banner_image_url}}#.jpg [effect="slideInRight" effectTime="5beat" width="400vw"  opacity="0.2"]
# *售价最低的5个NFT* [effect="fadeInDown" effectTime="3beat" effectDelay="0"]

-------------------------------------------

{{opensea_scene('https://api.opensea.io/api/v1/assets?asset_contract_address=' + contract_id + '&order_by=sale_price&order_direction=asc&offset=0&limit=5')}}

-------------------------------------------

https://cos.mirav.cn/jianshuo/Ink-67358.mp4
# Thanks for watching
