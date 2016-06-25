# AutoGrideLayout
九宫格布局，继承FrameLayout，根据显示数量的不同出现不同的布局，例如微博首页的九个图片根据显示的数量出现不同的布局</br>
代码在我的另一个项目当中[https://github.com/cyuanyang/imagebrowser](https://github.com/cyuanyang/imagebrowser)，demo里面写的很详细</br>
可以自定义item 的布局</br>
![截图](https://github.com/cyuanyang/imagebrowser/blob/master/screenshot/demo.gif)

# 特点
* 根据显示的数量不同定义不同的布局
* 不同的布局自定义不同的宽高比，例子宽高比是1:1
* 继承FrameLayout 可以在Listview中使用，不影响重用
* 自定义不同数量的布局

# 如何使用
```Xml
  <com.cyy.imagebrowserdemo.mlayout.NormalGridLayout
                android:id="@+id/autoGridLayout"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginLeft="10dp"
                android:layout_marginRight="10dp"
                android:background="#00ffff">
  </com.cyy.imagebrowserdemo.mlayout.NormalGridLayout>
```
我在adapter 中使用的方式 layout 是holder中的变量
```Java
 final List<String> uriStrs = datas.get(position);
        holder.layout.setHowMuchImageView(uriStrs,true);
        holder.layout.setItemClickListener(new AutoGridLayout.ItemClickListener() {
            @Override
            public void onItemClick(View view, int position) {
                ///这里holderUri应该传入缩略图的Uri ，但是测试没有缩略图，所以传入的大图。
                //
                // sorry
                YImageBrowser.newInstance().startBrowserImage((Activity) context ,uriStrs, uriStrs , view , position);
            }
        });
```



