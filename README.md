# Appbid-ANE-Adobe-AIR
Appbid Air SDK - ANE for Adobe Air based apps.

# ![Alt text](https://appbid.com/img/appbid_logo.png?raw=true "AppBid") AppBid

Our technology helps publishers maximize the value of every impression.
We Increase profits by allowing the leading ad exchanges to compete on your impressions, in real time with Machine learning optimization.

Our system studies your sold ad auctions, selects the highest paying exchange and sets the optimal opt-in price on the right network for each impression of each user to make sure that you will achieve a notable uplift in revenue.

All this happens in milliseconds.

<p align="center"> 
<img src="https://appbid.com/img/appbid_flow.png">
<img src="https://appbid.com/img/appbid_chart.png">
</p>

## Download
Download the newest SDK from [Here](https://www.google.com)

## Usage & Implementation

#### Prerequisites
* Minimum Android API Level - 16
* Internet permission

#### Usage & Implementation
Include ane in your poject

#### Update Your Application Descriptor
Include a link to the extension in the descriptor: 

```
<extensions>
<extensionID>com.vungle.extensions.Vungle</extensionID>
</extensions>
```

Update your Android Manifest Additions in the android XML element to:
* add permissions
```
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" /> <!--optional -->
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> <!--optional -->
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" /> <!--optional-->
```

* add in application tag
```
  <activity
        android:name="com.mopub.mobileads.MoPubActivity"
        android:configChanges="keyboardHidden|orientation|screenSize" />
    <activity
        android:name="com.mopub.mobileads.MraidActivity"
        android:configChanges="keyboardHidden|orientation|screenSize" />
    <activity
        android:name="com.mopub.common.MoPubBrowser"
        android:configChanges="keyboardHidden|orientation|screenSize" />
    <activity
        android:name="com.mopub.mobileads.MraidVideoPlayerActivity"
        android:configChanges="keyboardHidden|orientation|screenSize" />
    <activity
        android:name="com.mopub.mobileads.RewardedMraidActivity"
        android:configChanges="keyboardHidden|orientation|screenSize" />

    <activity
        android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:theme="@android:style/Theme.Translucent.NoTitleBar" />

    <meta-data
        android:name="applovin.sdk.key"
        android:value="wrrEUGLy-02pbUJBKTGWn1UeuMSTX99R_-gTF0PE0R2cxMoGw3og4GKycnP9wZbvXGMoGn1HD4u9QfPKiB_nSK" />

    <activity
        android:name="com.facebook.ads.AudienceNetworkActivity"
        android:configChanges="keyboardHidden|orientation|screenSize" />
    <activity
        android:name="com.flurry.android.FlurryShareActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <activity
        android:name="com.flurry.android.FlurryTileAdActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:screenOrientation="portrait"
        android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <activity
        android:name="com.flurry.android.FlurryBrowserActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:theme="@android:style/Theme.Translucent.NoTitleBar" /> <!-- Include the AdActivity and InAppPurchaseActivity configChanges and themes. -->
    <activity
        android:name="com.google.android.gms.ads.AdActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:exported="false"
        android:theme="@android:style/Theme.Translucent" />

    <meta-data
        android:name="com.google.android.gms.version"
        android:value="@integer/google_play_services_version" />
        
```

#### Loading & Showing Ads

First need initialize

```
var appBid:AppBid = new AppBid("appbid_key_here");
```

The easiest way to load&show ads is using the following method - 

```
appBid.loadWithAutoShow();
```

This, as the signature suggests, loads an ad and show it as soon as it's ready.

Alternatively, you may load an ad and then show it when you see fit - 
```
appBid.load();
```

And - 
```
appBid.showLoadedAd();
```

It's worth mentioning that if you call ```
appBid.load()
``` followed by ```
appBid.showLoadedAd()```, when the ad isn't ready yet, then the SDK will show the ad once it's loaded.

#### Listener
Add event listeners to listen AppBid events (if need):

```
appBid.addEventListener(AppBidEvent.AD_LOADED, onLoaded);
appBid.addEventListener(AppBidEvent.AD_FAILED, onFailed);
appBid.addEventListener(AppBidEvent.AD_CLOSED, onClosed);
appBid.addEventListener(AppBidEvent.AD_OPENED, onOpened);
appBid.addEventListener(AppBidEvent.AD_CLICKED, onClicked);
```

One useful usecase for using the listener is loading an ad and showing it when it's ready - 
```
appBid.addEventListener(AppBidEvent.AD_LOADED, onLoaded);
...
function onLoaded(event:AppBidEvent):void {
    appBid.showLoadedAd();
}
...
appBid.load()

```


