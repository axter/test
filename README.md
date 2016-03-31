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

