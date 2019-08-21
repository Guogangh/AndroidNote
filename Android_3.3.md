#### 3.3   详解4种基本布局

- 线性布局

  通过 android:orientation属性指定了排列方向是vertical（垂直）

  horizontal（水平）

  ```xml
  <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:app="http://schemas.android.com/apk/res-auto"
      android:orientation="vertical"
      android:layout_width="match_parent"
      android:layout_height="match_parent">
  
      <Button
          android:id="@+id/button1"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="Button 1"/>
  
      <Button
          android:id="@+id/button2"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="Button 2"/>
  
      <Button
          android:id="@+id/button3"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="Button 3"/>
  
  </LinearLayout>
  ```

  - 注意：如果LinearLayout的排列方向是horizontal（vertical），内部空间的宽度（高度）不能指定为match_parent，因为这样单独一个控件将会将整个水平方向占满，其他控件就没有可放置的位置了。

  - android：layout_gravity 用于指定***文字在控件中***的对齐方式。

    android：gravity 用于指定***控件在布局中***的对齐方式。

    注意：LinearLayout的排列方向是horizontal（vertical）时，只有垂直方向上的对齐方式才会生效，因为此时水平（垂直）方向上的长度是不固定的。

  - android：layout——weight用于使用比例的方式来指定控件的大小。

    以需要一个文本编辑框和一个发送按钮为例：

    ```xml
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:orientation="horizontal"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <EditText
            android:id="@+id/input_message"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="3"
            android:hint="Type something"
            />
    
        <Button
            android:id="@+id/send"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="2"
            android:text="Send"/>
    
    </LinearLayout>
    ```

    通过指定部分控件的layout_weight值来实现更好的效果：

    ```xml
    <EditText
            android:id="@+id/input_message"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:hint="Type something"
            />
    
        <Button
            android:id="@+id/send"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Send"/>
    ```

    优点：在各种屏幕的适配方面会非常好。

- 相对布局 RelativeLayout

  - 可以通过相对定位的方式让控件出现在布局的任何位置（相对于父布局定位）。

    ```xml
    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <Button
            android:id="@+id/button1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentLeft="true"
            android:layout_alignParentTop="true"
            android:text="Button 1"/>
    
        <Button
            android:id="@+id/button2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentRight="true"
            android:layout_alignParentTop="true"
            android:text="Button 2"/>
    
        <Button
            android:id="@+id/button3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerInParent="true"
            android:text="Button 3"/>
    
        <Button
            android:id="@+id/button4"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentBottom="true"
            android:layout_alignParentLeft="true"
            android:text="Button 4"/>
        <Button
            android:id="@+id/button5"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentBottom="true"
            android:layout_alignParentRight="true"
            android:text="Button 5"/>
    </RelativeLayout>
    ```

  - 控件相对于控件进行定位：

    - android：layout_alignLeft 表示一个控件的左边缘与另一个控件的左边缘对齐
    - android：layout_alignRight 表示一个控件的左边缘与另一个控件的右边缘对齐

    ```xml
    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <Button
            android:id="@+id/button3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerInParent="true"
            android:text="Button 3"/>
    
        <Button
            android:id="@+id/button1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@+id/button3"
            android:layout_toRightOf="@+id/button3"
            android:text="Button 1"/>
    
        <Button
            android:id="@+id/button2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_above="@+id/button3"
            android:layout_toRightOf="@+id/button3"
            android:text="Button 2"/>
    
        <Button
            android:id="@+id/button4"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@+id/button3"
            android:layout_toLeftOf="@+id/button3"
            android:text="Button 4"/>
        <Button
            android:id="@+id/button5"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_above="@+id/button3"
            android:layout_toLeftOf="@+id/button3"
            android:text="Button 5"/>
    </RelativeLayout>
    ```

    

- 帧布局  FrameLayout

  - 所有的空间都会默认摆放在布局的左上角

    ```xml
    <FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <TextView
            android:id="@+id/text_view"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="left"
            android:text="This is TextView" />
    
        <ImageView
            android:id="@+id/image_view"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="right"
            android:src="@mipmap/ic_launcher"/>
    </FrameLayout>
    ```

    

- 百分比布局

  - 只有LinearLayout支持使用layout_weight属性来实现按比例指定控件大小的功能，因此百分比布局只为FrameLayout和RelativeLayout进行了功能扩展，提供了PercentFrameLayout和PercentRealtiveLayout这两个全新的布局。

  - 百分比布局属于新增布局，Android团队将百分比布局定义在了support库当中，我们只需要在项目的build.gradle中添加百分比布局库的依赖，就能保证其兼容性。

    - 第一步：打开app/build/gradle文件，在dependencies闭包中添加一下内容:

      ```xml
      compile 'com.android.support:percent:24.2.1'
      ```

    - 第二步：点击弹出窗口中 <u>Sync Now</u> 按钮

    - 第三步：

      ```xml
      <android.support.percent.PercentFrameLayout
          xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto"
          android:layout_width="match_parent"
          android:layout_height="match_parent">
      
          <Button
              android:id="@+id/button1"
              android:text="Button 1"
              android:layout_gravity="left|top"
              app:layout_widthPercent="50%"
              app:layout_heightPercent="50%"/>
      
          <Button
              android:id="@+id/button2"
              android:text="Button 2"
              android:layout_gravity="right|top"
              app:layout_widthPercent="50%"
              app:layout_heightPercent="50%"/>
      
          <Button
              android:id="@+id/button3"
              android:text="Button 3"
              android:layout_gravity="left|bottom"
              app:layout_widthPercent="50%"
              app:layout_heightPercent="50%"/>
      
          <Button
              android:id="@+id/button4"
              android:text="Button 4"
              android:layout_gravity="right|bottom"
              app:layout_widthPercent="50%"
              app:layout_heightPercent="50%"/>
      </android.support.percent.PercentFrameLayout>
      ```

   
