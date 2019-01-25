# chrome-custom-tab
Custom Scroll and Page load Callback for chrome custom tab

In the file <a href="https://github.com/ankitkumarsingh-aksingh/chrome-custom-tab/blob/master/AKS_CustomTabActivityHelper.java" target="_blank">AKS_CustomTabActivityHelper</a> I tried to implement callback for <b>Page Load</b>

as defined at <a href="https://developer.android.com/reference/android/support/customtabs/CustomTabsCallback#NAVIGATION_FINISHED" target="_blank">CustomTabsCallback#NAVIGATION_FINISHED</a>.

I updated the file <a href="https://github.com/GoogleChrome/custom-tabs-client/blob/master/demos/src/main/java/org/chromium/customtabsdemos/CustomTabActivityHelper.java" target="_blank">CustomTabActivityHelper</a> by implementing
<b>CustomTabsCallback</b> in the following ways:

```
    private static class NavigationCallback extends CustomTabsCallback {
        @Override
        public void onNavigationEvent(int navigationEvent, Bundle extras) {
            Log.e("CustomTabActivityHelper", "onNavigationEvent: Code = " + navigationEvent);
        }
    }
 ```   
 
 and initialize above Callback like:
 
 ```
     public CustomTabsSession getSession() {
        if (mClient == null) {
            mCustomTabsSession = null;
        } else if (mCustomTabsSession == null) {
            mCustomTabsSession = mClient.newSession(new NavigationCallback()); // My custom Code
        }
        return mCustomTabsSession;
    }
 ```
 
 
 Added a custom <b>NavigationCallback</b> class and log all the <b>NavigationEvent</b> that occured but it does not logged any single event.
