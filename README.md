# AdvancedWebview

Welcome to AdvancedWebview! This AdvancedWebview comes with internet connection detection, banner and interstitial ads, and other exciting features.

## Features

- **Internet Connection Detection:** The app can detect whether the device has an internet connection.

- **Banner Ad:** Display a banner ad at the bottom of the app to generate revenue.

- **Interstitial Ad:** Show a full-screen ad when the user returns to the app, providing a seamless ad experience.

- **Google Analytics:** (Add your `google_services.json` file to the app directory).

- **Swipe to Refresh:** Swipe from the top of the page to refresh the current page.

- **Link Loading Indicator:** Show an indication when a link is loading using a progress bar.

## Installation

To install the app on your own device:

1. Download the app APK and Zip file from [marabytes.com](https://marabytes.com/).

2. Install the APK on your Android device.

## Setting Up Ad IDs

To integrate your AdMob Ad IDs, follow these steps:

1. Open the `MainActivity.java` file.

   ```java
   // Initialize the AdView
   adView = findViewById(R.id.adView);
   
   // ...

   // Initialize the InterstitialAd
   interstitialAd = new InterstitialAd(this);
   
   // Replace "YOUR_INTERSTITIAL_AD_UNIT_ID" with your actual AdMob Interstitial Ad Unit ID
   InterstitialAd.load(this, "ca-app-pub-3940256099942544/1033173712", adRequest,
                new InterstitialAdLoadCallback() {
                    @Override
                    public void onAdLoaded(@NonNull InterstitialAd interstitialAd) {
                        // The mInterstitialAd reference will be null until
                        // an ad is loaded.
                        fullscreen();
                        mInterstitialAd = interstitialAd;
                        Log.i(TAG, "onAdLoaded");
                    }

                    @Override
                    public void onAdFailedToLoad(@NonNull LoadAdError loadAdError) {
                        // Handle the error
                        Log.d(TAG, loadAdError.toString());
                        mInterstitialAd = null;
                    }
                });
   
   // ...
Replace "YOUR_INTERSTITIAL_AD_UNIT_ID" with your actual AdMob Interstitial Ad Unit ID.

Save the changes and rebuild the app.


```xml
//Replace with your application ID
<meta-data
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="ca-app-pub-6433617325894503~7780935405"/>

// ...
```
Also in XML replace with your banner ID.

```
<com.google.android.gms.ads.AdView
    xmlns:ads="http://schemas.android.com/apk/res-auto"
    android:id="@+id/adView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_gravity="bottom"
    ads:adSize="BANNER"
    ads:adUnitId="ca-app-pub-3940256099942544/6300978111">
