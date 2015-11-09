
Webviews off of the UI Thread
======
**Last Updated: 11/8/2015**

##Context
By default, Webview elements in XAML run on the UI thread. For some purposes, this may be acceptable, but oftentimes, when hosting web content, you will want the webview to host its content on a background thread, off the UI thread.

For instance, the webview may only be a small portion of the larger page. When the webview is loading content, it may be desirable to have the user continue being able to interact with the app UI. In Windows 10, the *Webview.ExecutionMode* property allows you to do just that. 

##Code Sample
Currently, two execution modes are supported *SameThread* and *SeparateThread*. Naturally, the values are as you would expect: *SameThread* essentially means the UI Thread and *SeparateThread* means a non-UI background thread. The default is *SameThread*. To create a webview instance with a *SameThread* execution mode, you may specify the following in the constructor:

```cs
WebView webview = new WebView(WebViewExecutionMode.SeparateThread);
```

Of course, the above assumes you're creating your WebView in the code behind rather than the XAML markup. The same line of code in more context might be something like:

```cs
_webview = new WebView(WebViewExecutionMode.SeparateThread);
_webview.HorizontalAlignment = HorizontalAlignment.Stretch;
_webview.VerticalAlignment = VerticalAlignment.Stretch;

MainGrid.Children.Add(_webview);
```

The relevant piece of XAML markup might look something like:
```xml
<Grid HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
    <Grid Name="MainGrid" 
		  HorizontalAlignment="Stretch" 
		  VerticalAlignment="Stretch">     
    </Grid>
</Grid>
```

To learn about the limitations of hosting webview content off the UI thread, click [here](limitations.md).