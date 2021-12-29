# Jinja

MiraML 里面可以写一些程序的语句，控制变量，循环等等。

我们支持左右的 Jinja 模版的语句。具体的内容请参考 Jinja 的文档 http://docs.jinkan.org/docs/jinja2/

这些是最最简单的一些语法：


## 常用标记：

### 注释：

`{# 这是注释 #}`

### 变量：

`{{ post.title }}`，

或字典元素 `{{your_dict['key']}}`，

或列表 `{{your_list[0]}}`

多行代码块：`{% 开始 %} HTML 标签 {% 结束 %}`

示例：
```
{% if user %}
    {{ user }}
{% else %}
    hello!
    {% for index in indexs %}
        {{ index }} 
{% endfor %}
```

###  Delimiters（分隔符）

```
{% … %} 语句（[Statements](http://jinja.pocoo.org/docs/dev/templates/#list-of-control-structures)）
{{ … }} 打印模板输出的表达式（[Expressions](http://jinja.pocoo.org/docs/dev/templates/#expressions)）
{# … #} 注释
# … ## 行语句（[Line Statements](http://jinja.pocoo.org/docs/dev/templates/#line-statements)）
```

## Variables（变量）

除了普通的字符串变量，Jinja2 还支持列表、字典和对象，你可以这样获取变量值：

```
{{ mydict['key'] }}
{{ mylist[3] }}
{{ mylist[myintvar] }}
{{ myobj.somemethod() }}
```


获取一个变量的属性有两种方式：

```
{{ foo.bar }}
{{ foo['bar'] }}
```


这两种方法基本相同（深层次的区别可以暂不考虑）

## Filter 过滤器()

一个 filter 过滤器的本质就是一个 function 函数。使用格式为：变量名 | 函数。
它做到的就是，把变量传给函数，然后再把函数返回值作为这个代码块的值。

```
<!-- 带参数的 -->
{{ 变量 | 函数名(*args)}}
```

```
<!-- 不带参数可以省略括号 -->
{{ 变量 | 函数名 }}
```

链式调用（管道式）：
和命令行的 pipline 管道一样，可以一次调用多个函数（过滤器），如：

```
{{ "hello world" | reverse | upper }}
```

文本块调用（将中间的所有文字都作为变量内容传入到过滤器中）：

```
{% filter upper %}
    一大堆文字
{% endfilter %}
```

### Jinja2 常用过滤器

safe：禁用转义
```
{{ '<em>hello</em>' | safe }}
```


capitalize：把变量值的首字母转成大写，其余字母转小写
```
{{ 'hello' | capitalize }}
```


lower：把值转成小写
```
{{ 'HELLO' | lower }}```
```


upper：把值转成大写
```
{{ 'hello' | upper }}
```


title：把值中的每个单词的首字母都转成大写
```
{{ 'hello' | title }}
```


reverse：字符串反转
```
{{ 'olleh' | reverse }}
```


format：格式化输出
```
{{ '%s is %d' | format('name',17) }}
```


striptags：渲染之前把值中所有的 HTML 标签都删掉
```
{{ '<em>hello</em>' | striptags }}
```


truncate: 字符串截断
```
{{ 'hello every one' | truncate(9)}}
```


### 列表操作：

first：取第一个元素
```
{{ [1,2,3,4,5,6] | first }}
```


last：取最后一个元素
```
{{ [1,2,3,4,5,6] | last }}
```


length：获取列表长度
```
{{ [1,2,3,4,5,6] | length }}
```


sum：列表求和
```
{{ [1,2,3,4,5,6] | sum }}
```


sort：列表排序

```
{{ [6,2,3,1,5,4] | sort }}
```


##  Members

```
{% for user in users %}
  <li>{{ user.username|e }}</li>
{% endfor %}
```

As variables in templates retain their object properties, it is possible to iterate over containers like dict:

```
{% for key, value in my_dict.items() %}
    <dt>{{ key|e }}</dt>
    <dd>{{ value|e }}</dd>
{% endfor %}
```

## 循环索引

loop.index: 循环当前迭代(从 1 开始)。
loop.index0: 循环当前迭代(从 0 开始)。
loop.revindex: 循环迭代的数量(从 1 开始)。
loop.revindex0: 循环迭代的数量(从 0 开始)。
loop.first: 是否为迭代的第一步。
loop.last: 是否为迭代的最后一步。
loop.length: 序列中元素的数量。

```
{% if users %}
<ul>
{% for user in users %}
    <li>{{ user.username|e }}</li>
{% endfor %}
</ul>
{% endif %}
```

```
{% if kenny.sick %}
    Kenny is sick.
{% elif kenny.dead %}
    You killed Kenny!  You bastard!!!
{% else %}
    Kenny looks okay --- so far
{% endif %}
```
