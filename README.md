# 标题，这是 H1
## 标题，这是 H2
### 标题，这是 H3

> 引用
引用换行，董事局佛自己水电费
>> 二级引用
引用换行


* 段落一
 > 区块标记一
* 段落二
 > 区块标记二

### 无序列表
- Red
- Green
换行,段落dadadada
- Blue
* Red
换行dadadada
* Green
* Green

### 有序列表，数字+.
1. Bird
1. McHale
1. Parish

### 列表嵌套，与子级隔1-3个空格
- Red
 - Bird
 - McHale
 - Parish

### 列表段落，项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：
1. This is a list item with two paragraphs. Lorem ipsum dolor
 sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.

 Vestibulum enim wisi, viverra nec, fringilla in, laoreet
 vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
 sit amet velit.

2. Suspendisse id sem consectetuer libero luctus adipiscing.

### 代码块-强调
`强调`
提升标题`Ctrl + H`
提升标题`Ctrl + H`提升标题

- [x] dd

### 代码块
```java
public static void main(){
 System.out.println("这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串，这是一段非常长的串");
}
```
### 分隔线
---
***

### 字体，加入\特殊字符会有bug
*斜体*
_斜体_
**粗体**
__粗体__
***斜体加粗***
~~删除线~~

[id]: http://example.com/  "Optional Title Here"


### 图片
![图片加载失败显示的文字](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=702257389,1274025419&fm=27&gp=0.jpg "鼠标提示文字")
![图片加载失败显示的文字](/path/to/img.jpg "鼠标提示文字")

### 超链接，需要优化  target="_blank"
[超链接名](超链接地址 "鼠标提示文字，可不加")

### 自动连接
<https://www.jianshu.com/p/b03a8d7b1719>

<http://example.com/>
<address@example.com>

### 表格
表头|表头|表头
-|:-:|-:
内容|内容|内容
内容|内容|内容

```plaintext
-有一个就行（为了对齐，可以多加几个）文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
```
### 标题锚点
[标题锚点](#1) 

### 引用链接
I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

[1]: http://google.com/        "Google" 
[2]: http://search.yahoo.com/  "Yahoo Search" 
[3]: http://search.msn.com/    "MSN Search"


### 脚注，在文章最后面显示脚注 {#1}
Markdown[^1]
Markdown2[^2]

### 按键
<kbd>alt</kbd>
 

[^1]: Markdown是一种纯文本标记语言

[^2]: xx是一种纯文本标记语言
