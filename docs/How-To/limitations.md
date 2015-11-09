
Limitations of WebViews off the UI Thread
======
**Last Updated: 11/8/2015**

##Context
Now you've set your WebView ExecutionMode to *SeparateThread*, and your app is running smoother than it ever did before. "Gee" you wonder, "Why isn't that the default execution mode?"

While running WebView content on a background thread is convenient for the page loads to not block the UI thread, there are several limitations that you should keep in mind

##Limitations
The [MSDN page](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.webviewexecutionmode.aspx) for the WebView.ExecutionMode property states that there are the following limitations when the WebView is not on the UI thread:

> When the WebView is not on the UI thread, the behaviors listed here are not supported:

> * Scroll chaining and pointer chaining. (Input events aren't propagated to parent controls that uses DirectManipulation like ScrollViewer or FlipView.)

> * Tab navigation to escape focus on WebView.

> * Printing.