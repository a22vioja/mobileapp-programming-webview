
# Rapport
I renamed my App, enabled Internet access, created a WebView element and gave the WebView element ID.
```
 <string name="app_name">App By Violeta</string>
```

```
<uses-permission android:name="android.permission.INTERNET" />
```

```
<WebView
android:id="@+id/webview"
android:layout_width="match_parent"
android:layout_height="0dp"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toBottomOf="@+id/appBarLayout"
/>
```

I also created a private member variable called "myWebView" of type WebView and located it.
I created a new WebViewClient and attached it to my WebView.
I enabled Javascript execution, entered the url to load in my WebView.

```
public class MainActivity extends AppCompatActivity {
    private WebView myWebView;

    public void showExternalWebPage(){
        myWebView.loadUrl("https://his.se");
    }

    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/about.html");
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        myWebView = findViewById(R.id.webview);
        myWebView.setWebViewClient(new WebViewClient()); // Do not open in Chrome!

        WebView myWebView = (WebView) findViewById(R.id.webview);
        WebSettings webSettings = myWebView.getSettings();
        webSettings.setJavaScriptEnabled(true);
}
```
I also moved the code that loads a URL into the "showExternalWebPage()" and "showInternalWebPage()" methods
and called them.

```
 if (id == R.id.action_external_web) {
            Log.d("==>","Will display external web page");
            showExternalWebPage();
            return true;
        }

        if (id == R.id.action_internal_web) {
            Log.d("==>","Will display internal web page");
            showInternalWebPage();
            return true;
        }
```

This is my internal and external pages.

![](internal4.png)
![](external4.png)
