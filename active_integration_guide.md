1. Add in a `build.gradle` file:
##### build.gradle
```groovy
android {
    repositories {
        maven { url "https://raw.github.com/teragence/android-sdk/mvn-rep" }
    }
}
```
```groovy
dependencies {
    compile 'com.teragence:active:x.x.x.x'
}
```

To find last version visit [release notes](https://github.com/Teragence/android-sdk/blob/master/release_notes.md) 

2. Add these rules to the proguard file:

```
-keep class tg_*.** { *; }
-keep class com.teragence.** { *; }
-dontwarn tg_*.**
-dontwarn android.net.ConnectivityManager
```
    
3. Add your `partner id` as a meta-data value with name `"teragencePartnerId"` in an `AndroidManifest.xml`:

##### AndroidManifest.xml
    <application
    ...
        <meta-data
            android:name="teragencePartnerId"
            android:value="myPartnerId" />
    
    </application>
    
4. [Request all required runtime permissions:](https://developer.android.com/training/permissions/requesting.html)

```android.permission.INTERNET
android.permission.ACCESS_COARSE_LOCATION
android.permission.ACCESS_FINE_LOCATION
android.permission.ACCESS_WIFI_STATE
android.permission.CHANGE_WIFI_STATE
android.permission.ACCESS_NETWORK_STATE
android.permission.CHANGE_NETWORK_STATE
android.permission.WAKE_LOCK
android.permission.RECEIVE_BOOT_COMPLETED
```

5. Use `com.teragence.client.Measurement` class.

* To make a measurement, call 
```java
new Measurement(context).make();
```

* To handle a measurement progress, use `android.content.BroadcastReceiver` and `STARTED/STOPPED` actions from the `com.teragence.client.service.ServiceStateConstants` class.

    Pay attention that measurement doing asynchronous and take 1-2 minutes.

6. Troubleshooting:

In case of the error: 
>Error:Execution failed for task ':app:transformResourcesWithMergeJavaResForDebug'.
More than one file was found with OS independent path 'META-INF/DEPENDENCIES'
    
add in a `build.gradle` file:
    
##### build.gradle
```groovy
android {
    packagingOptions {
            exclude 'META-INF/DEPENDENCIES'
        }
}
```

8. Optional:

    - In the case, if you want to disable mobile network tests when a user uses
    a Wi-Fi network add `false` as a meta-data value with the name `"mobileMeasureOnWiFi"`
    in an `AndroidManifest.xml`:

    ##### AndroidManifest.xml
        <application
        ...
            <meta-data
                android:name="teragenceMobileMeasureOnWiFi"
                android:value="false" />

        </application>