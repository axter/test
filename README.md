# Android善跑开发说明

[TOC]

## 代码格式化
- 使用TAB缩进
- javadoc单行显示为 /** xxx */

## 常量使用
- colors.xml 颜色记录包括透明位
- 详见《Android善跑常量查询.xls》

## 使用图片
- 优先考虑是否可以使用shape实现效果

## 基础类
三个基础类
- CommonActivity
- CommonFragment 
- CommonFragmentActivity

统一执行顺序   
1. receiveIntentArgs()  **处理Initent传递数据**
1. getContentView()  **设置View** 
1. initView()  **初始化View**
1. initData()  **设置数据**

其他方法
- isUseEventBus()  **是否使用EventBus,有需求重写方法返回true**

### 示例
```java

```

## 显示缩略图 DisplayUtil

```java
/** 获取缩略图地址 */
public static String getThumbnailPath(String url, int w, int h)
/** 显示运动记录缩略图 */
public static void displaySport(int motion_id, ImageView imageview)
/** 显示头像 100px */
public static void displayHead(String url, ImageView imageview)
/** 显示小图片 150px */
public static void display11(String url, ImageView imageview)
/** 显示横幅图片 400px */
public static void display44(String url, ImageView imageview)
/** 显示大图片 600px */
public static void display66(String url, ImageView imageview)
```

## 选择图片 ChoosePhotoActivity

```java
// 设置最多选择9张图片
intent_photo.putExtra(ChoosePhotoActivity.EXTRA_COUNT, 9);
// 结果处理
onActivityResult方法内
data.getStringArrayListExtra(ChoosePhotoActivity.EXTRA_OUT_PICS)
```

## 预览图片 PreviewPhotoActivity
```java
// 传入图片地址数据
intent.putStringArrayListExtra(PreviewPhotoActivity.EXTRA_IMAGE_PATHS, pics);
// 浏览起始图片坐标
intent.putExtra(PreviewPhotoActivity.EXTRA_POSITION, 0);
// 预览图片模式
// 删除模式	PreviewPhotoActivity.EXTRA_TYPE_DEL
// 浏览模式	PreviewPhotoActivity.EXTRA_TYPE_PREVIEW
intent.putExtra(PreviewPhotoActivity.EXTRA_TYPE, PreviewPhotoActivity.EXTRA_TYPE_DEL);

// 删除模式数据处理,坐标数据倒叙返回,如:[11,10,5,2]
data.getIntegerArrayList(PreviewPhotoActivity.EXTRA_OUT_DEL_POSITION);
```

## 底部弹出选择对话框 AutoBottomMenuDialog
```java
mDialog = new AutoBottomMenuDialog(mContext, true, true, true);
	mDialog.addButtonView("拍照");
	mDialog.addButtonView("相册");
	mDialog.addButtonView("取消");
	mDialog.setOnclickListener(new View.OnClickListener() {
		@Override
		public void onClick(View v) {
			mDialog.dismiss();
			switch (v.getId()) {
				case 0:
					openCamera();
					break;
				case 1:
					openPhotos();
					break;
				case 2:
					break;
			}
		}
	});
}
mDialog.show();
```

## 确定,取消对话框 AutoAlert
```java
AutoAlert dialog = new AutoAlert(mContext);
dialog.setTitle("确定删除?")
		.setOnClick(new AutoAlert.OnClick() {
			@Override
			public void onCancel() {

			}

			@Override
			public void onConfirm() {
				postDelete();
			}
		});

// 静态调用
AutoAlert.getAlert(mContext, alert_click)
				.setTitle("确定删除?")
				.show();
```
## 一行menu样式 MenuItem
```xml
<com.imohoo.shanpao.common.ui.MenuItem
	android:id="@+id/rl_chart_notification"
	style="@style/menuitem_style.title.toggle.extra"
	wk:menuTitle="@string/message_notification" />
```

## XListView使用封装《XListViewUtils 》
数据源内应该具备的方法
- getList() 当前获取的数据
- getPerpage() 每页显示数
- getCount() 总数

```java
initList(...);// 初始化 (必须)
doRefresh();// 主动触发刷新
stopXlist();// 数据加载或错误时关闭动画 (必须)

XListViewUtils.CallBack 回调接口使用
---------------------------------------
onRefresh 下拉刷新触发
onLoadMore 上拉加载触发
onRefreshNoData 下拉刷新无数据,可以显示无数据页
onShowData	显示数据了(与onRefreshNoData相对)
onConvertData 数据格式转换(一般不需要使用)
onItemClick  item点击事件
```

## 网络使用,通用入口类《Request》
```java
/**post请求*/
Request.post(...)
/**上传*/
Request.upload(...)
/**下载*/
Request.download(..) 
```




# The largest heading
## The second largest heading
### The thrid heading
#### The fourth heading
##### The fifth heading
###### The smallest heading
# The largest heading
## The second largest heading
## The second largest heading
### The thrid heading
### The thrid heading
#### The fourth heading
#### The fourth heading
##### The fifth heading
##### The fifth heading
###### The smallest heading
###### The smallest heading
```html
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
<iframe height=498 width=510 src="http://player.youku.com/embed/XNjcyMDU4Njg0" frameborder=0 allowfullscreen></iframe>
```

![Alt text](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1518107883182&di=2bbcbf051f76ed81a280913c0c19a9d3&imgtype=0&src=http%3A%2F%2Fa.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2F500fd9f9d72a6059f550a1832334349b023bbae3.jpg "Optional title")

<iframe height=400 width=510 src="/static/music.html" frameborder=0 allowfullscreen></iframe>

**this is the bold text**

*this text is italicized*

~~This was misstaken text~~

**this text is _extremely_ important**

In the words of Abraham Lincoln:

> Pardon my French

Use `git status` to list all new or modified files that haven't yet been commited

Some basic Git commands are:
```
git status
git add
git commit
```

```java
/**
 * Test main function
*/
public static void main(){
}
```

This site was built using [Github Pages](https://pages.github.com).

- George Washington
- John Adams
- Thomas Jefferson


1. James Madison
2. James Monroe
3. John Quincy Adams


1. Make my changes
   1. Fix bug
   2. Improve formatting
      * Make the heading bigger
2. Push my commits to Github
3. Open a pull request
   * Describe my changes
   * Mention all the members of my team
     * Ask for feedbackk

<ul>
    <li class="task-list-item" checked="">
        <input type="checkbox" class="task-list-item" checked="" disabled=""> Finish my changes
    </li>
    <li class="task-list-item">
        <input type="checkbox" class="task-list-item" disabled=""> Push my commits to Github
    </li>
    <li class="task-list-item">
        <input type="checkbox" class="task-list-item" disabled=""> Open a pull request
    </li>
</ul>

key  | value | desc
----- | -------- | -----
getFunc | function | get the property of the key
setFunc | function | set the property of the key



# 欢迎使用马克飞象

@(示例笔记本)[马克飞象|帮助|Markdown]

**马克飞象**是一款专为印象笔记（Evernote）打造的Markdown编辑器，通过精心的设计与技术实现，配合印象笔记强大的存储和同步功能，带来前所未有的书写体验。特点概述：
 
- **功能丰富** ：支持高亮代码块、*LaTeX* 公式、流程图，本地图片以及附件上传，甚至截图粘贴，工作学习好帮手；
- **得心应手** ：简洁高效的编辑器，提供[桌面客户端][1]以及[离线Chrome App][2]，支持移动端 Web；
- **深度整合** ：支持选择笔记本和添加标签，支持从印象笔记跳转编辑，轻松管理。

-------------------

[TOC]

## Markdown简介

> Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成格式丰富的HTML页面。    —— [维基百科](https://zh.wikipedia.org/wiki/Markdown)

正如您在阅读的这份文档，它使用简单的符号标识不同的标题，将某些文字标记为**粗体**或者*斜体*，创建一个[链接](http://www.example.com)或一个脚注[^demo]。下面列举了几个高级功能，更多语法请按`Ctrl + /`查看帮助。 

### 代码块
``` python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None
class SomeClass:
    pass
>>> message = '''interpreter
... prompt'''
```
### LaTeX 公式

可以创建行内公式，例如 $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$。或者块级公式：

$$	x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

### 表格
| Item      |    Value | Qty  |
| :-------- | --------:| :--: |
| Computer  | 1600 USD |  5   |
| Phone     |   12 USD |  12  |
| Pipe      |    1 USD | 234  |

### 流程图
```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```

以及时序图:

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

> **提示：**想了解更多，请查看**流程图**[语法][3]以及**时序图**[语法][4]。

### 复选框

使用 `- [ ]` 和 `- [x]` 语法可以创建复选框，实现 todo-list 等功能。例如：

- [x] 已完成事项
- [ ] 待办事项1
- [ ] 待办事项2

> **注意：**目前支持尚不完全，在印象笔记中勾选复选框是无效、不能同步的，所以必须在**马克飞象**中修改 Markdown 原文才可生效。下个版本将会全面支持。


## 印象笔记相关

### 笔记本和标签
**马克飞象**增加了`@(笔记本)[标签A|标签B]`语法, 以选择笔记本和添加标签。 **绑定账号后**， 输入`(`自动会出现笔记本列表，请从中选择。

### 笔记标题
**马克飞象**会自动使用文档内出现的第一个标题作为笔记标题。例如本文，就是第一行的 `欢迎使用马克飞象`。

### 快捷编辑
保存在印象笔记中的笔记，右上角会有一个红色的编辑按钮，点击后会回到**马克飞象**中打开并编辑该笔记。
>**注意：**目前用户在印象笔记中单方面做的任何修改，马克飞象是无法自动感知和更新的。所以请务必回到马克飞象编辑。

### 数据同步
**马克飞象**通过**将Markdown原文以隐藏内容保存在笔记中**的精妙设计，实现了对Markdown的存储和再次编辑。既解决了其他产品只是单向导出HTML的单薄，又规避了服务端存储Markdown带来的隐私安全问题。这样，服务端仅作为对印象笔记 API调用和数据转换之用。

 >**隐私声明：用户所有的笔记数据，均保存在印象笔记中。马克飞象不存储用户的任何笔记数据。**

### 离线存储
**马克飞象**使用浏览器离线存储将内容实时保存在本地，不必担心网络断掉或浏览器崩溃。为了节省空间和避免冲突，已同步至印象笔记并且不再修改的笔记将删除部分本地缓存，不过依然可以随时通过`文档管理`打开。

> **注意：**虽然浏览器存储大部分时候都比较可靠，但印象笔记作为专业云存储，更值得信赖。以防万一，**请务必经常及时同步到印象笔记**。

## 编辑器相关
### 设置
右侧系统菜单（快捷键`Ctrl + M`）的`设置`中，提供了界面字体、字号、自定义CSS、vim/emacs 键盘模式等高级选项。

### 快捷键

帮助    `Ctrl + /`
同步文档    `Ctrl + S`
创建文档    `Ctrl + Alt + N`
最大化编辑器    `Ctrl + Enter`
预览文档 `Ctrl + Alt + Enter`
文档管理    `Ctrl + O`
系统菜单    `Ctrl + M` 

加粗    `Ctrl + B`
插入图片    `Ctrl + G`
插入链接    `Ctrl + L`
提升标题    `Ctrl + H`

## 关于收费

**马克飞象**为新用户提供 10 天的试用期，试用期过后需要[续费](maxiang.info/vip.html)才能继续使用。未购买或者未及时续费，将不能同步新的笔记。之前保存过的笔记依然可以编辑。


## 反馈与建议
- 微博：[@马克飞象](http://weibo.com/u/2788354117)，[@GGock](http://weibo.com/ggock "开发者个人账号")
- 邮箱：<hustgock@gmail.com>

---------
感谢阅读这份帮助文档。请点击右上角，绑定印象笔记账号，开启全新的记录与分享体验吧。




[^demo]: 这是一个示例脚注。请查阅 [MultiMarkdown 文档](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide#footnotes) 关于脚注的说明。 **限制：** 印象笔记的笔记内容使用 [ENML][5] 格式，基于 HTML，但是不支持某些标签和属性，例如id，这就导致`脚注`和`TOC`无法正常点击。


  [1]: http://maxiang.info/client_zh
  [2]: https://chrome.google.com/webstore/detail/kidnkfckhbdkfgbicccmdggmpgogehop
  [3]: http://adrai.github.io/flowchart.js/
  [4]: http://bramp.github.io/js-sequence-diagrams/
  [5]: https://dev.yinxiang.com/doc/articles/enml.php

