# activity5
Android实验5

**题目要求：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190505171919453.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**核心代码:**
MainActivity.java
```java
package com.example.myapplication5;

import android.content.Intent;
import android.net.Uri;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    private EditText editText;
    private Button button;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        init();
    }

    public void init(){
        editText=(EditText)findViewById(R.id.url);
        button=(Button)findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent(Intent.ACTION_VIEW);
                intent.putExtra("data",editText.getText().toString());
                startActivity(intent);
                finish();
            }
        });
    }
}
```
WebViewActivity.java
```java
package com.example.myapplication5;

import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.util.Log;
import android.webkit.WebView;

public class WebViewActivity extends AppCompatActivity {

    private WebView webView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.layout_web);
        init();
    }

    public void init(){
        webView=(WebView)findViewById(R.id.webView);
        Intent intent=getIntent();
        String url = (String)intent.getStringExtra("data");
        Log.d("huang", "url" + url);
        webView.loadUrl(url);
    }
}
```
activity_main.xml
```java
    
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center_horizontal"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/url"
        android:layout_marginTop="50dp"
        android:layout_width="300dp"
        android:layout_height="50dp" />

    <Button
        android:layout_marginTop="20dp"
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="浏览该网页"/>

</LinearLayout>
```

**截图：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190505172609494.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190505172626624.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190505172638429.png)
