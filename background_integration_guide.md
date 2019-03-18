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
    compile 'com.teragence:background:x.x.x.x'
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

3. Add `com.teragence.client.service.PresenceReceiver` in `AndroidManifest.xml`
with specific intent-filter actions `QUICKBOOT_POWERON`, `BOOT_COMPLETED`:

##### AndroidManifest.xml

    <application
    ...
        <receiver android:name="com.teragence.client.service.PresenceReceiver" >
            <intent-filter>
                <action android:name="android.intent.action.QUICKBOOT_POWERON" />
                <action android:name="android.intent.action.BOOT_COMPLETED" />
            </intent-filter>
        </receiver>
    </application>
    
4. Add your `partner id` as a meta-data value with name `"teragencePartnerId"` in an `AndroidManifest.xml`:

##### AndroidManifest.xml
    <application
    ...
        <meta-data
            android:name="teragencePartnerId"
            android:value="myPartnerId" />
    
    </application>
    
5. [Request all required runtime permissions:](https://developer.android.com/training/permissions/requesting.html)

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

6. Initialize background work:

```java
import com.teragence.client.SdkControls;

public class MyActivity {
    
    @Override
    protected void onCreate(Bundle savedInstanceState){
        SdkControls.initialize(this);
    }
	
}

```

7. Troubleshooting:

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
