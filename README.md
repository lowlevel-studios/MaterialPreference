# Material Preference [ ![Download](https://api.bintray.com/packages/anggrayudi/maven/materialpreference/images/download.svg)](https://bintray.com/anggrayudi/maven/materialpreference/_latestVersion)
A library designed for people who love simplicity. Hate the old preference style? Try this library.

It combines libraries from `android.support.v7.preference` and `net.xpece.android.support.preference`.
Available from API 17.
<br><a href="https://play.google.com/store/apps/details?id=com.anggrayudi.materialpreference.sample" target="_blank"><img alt="Google Play" height="80" src="https://play.google.com/intl/en_US/badges/images/generic/en_badge_web_generic.png" align="right"/></a><br><br><br>

## Screenshots

![Alt text](art/1-generic.png?raw=true "Material Preference")
![Alt text](art/2-generic.png?raw=true "Material Preference")
![Alt text](art/3-generic.png?raw=true "DatePreference")
![Alt text](art/4-generic.png?raw=true "ListPreference")

## Usage

This library available in 2 versions:
1. Version `1.0.0` that uses Support Library v28.0.0
2. Version `2.0.0` that uses AndroidX Jetpack
3. Version `3.0.0` that have been migrated to Kotlin

You can choose which version you want to use. But I recommend you to use v2.0.0 since v1.0.0 will not be supported for future release. Notice that [Google announced](https://android-developers.googleblog.com/2018/05/hello-world-androidx.html) where Support Library v28.0.0 is the final version and will be replaced with AndroidX Jetpack soon. So it is your decision whether to migrate to AndroidX Jetpack or not.

```groovy
repositories {
    maven { url 'https://dl.bintray.com/anggrayudi/maven/' }
}

dependencies {
    implementation 'com.anggrayudi:materialpreference:3.0.1'
}
```

From your `preferences.xml`:

```xml
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android">

    <!-- To make Preferences floating, you must wrap them inside PreferenceCategory -->
    <PreferenceCategory>
        <Preference
            android:key="about"
            android:title="About"
            android:icon="@drawable/..."
            app:tintIcon="?colorAccent"
            app:legacySummary="false"/>
    </PreferenceCategory>
</PreferenceScreen>
```

From your `SettingsFragment`:

```kotlin
class SettingsFragment : PreferenceFragmentMaterial() {

    override fun onCreatePreferences(savedInstanceState: Bundle?, rootKey: String?) {
        addPreferencesFromResource(R.xml.preferences)
    }
}
```

From your `SettingsActivity`:

```kotlin
class SettingsActivity : PreferenceActivityMaterial() {

    private var settingsFragment: SettingsFragment? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        if (savedInstanceState == null) {
            settingsFragment = SettingsFragment.newInstance(null)
            supportFragmentManager.beginTransaction().add(R.id.fragment_container, settingsFragment!!, TAG).commit()
        } else {
            settingsFragment = supportFragmentManager.findFragmentByTag(TAG) as SettingsFragment?
            title = settingsFragment!!.preferenceFragmentTitle
        }
    }
}
```

## Preferences

- `Preference`
- `CheckBoxPreference`
- `SwitchPreference`
- `EditTextPreference`
- `ListPreference`
- `MultiSelectListPreference`
- `SeekBarDialogPreference`
- `SeekBarPreference`
- `RingtonePreference`
- `IndicatorPreference`
- `FolderPreference`
- `DatePreference`
- `TimePreference`
- `ColorPreference`

### RingtonePreference

`RingtonePreference` will show only system ringtone sounds by default.
If you want to include sounds from the external storage your app needs to request
`android.permission.READ_EXTERNAL_STORAGE` permission in its manifest.
Don't forget to check this runtime permission before opening ringtone picker on API 23.

## Donation
Any donation you give is really helpful for us to develop this library. It feels like energy from power stone.

<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TGPGSY66LKUMN&source=url" target="_blank"><img alt="Donate with PayPal" src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" border="0"/></a>

## License

    Copyright 2018-2019 Anggrayudi Hardiannicko A.
 
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
 
        http://www.apache.org/licenses/LICENSE-2.0
 
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
