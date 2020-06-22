---
title: "React Native on Android"
date: 2020-05-05T17:00:00+02:00
draft: false
---
### Open Android project from terminal
`android-studio .` to open folder in Android studio

{{< error type="terminal">}}
  {{< terminal scope="error">}}
    Gradle error: IllegalStateException: No value has been specified for this provider
  {{< /terminal >}}

  {{< error-content >}}
  Seems to be because the cradle file is unsync, because we have generate it with different version of gradle.

  __Solution:__ We tried to clean the gradle with `./gradlew clean` in the android folder of the project and upgrading the Cradle file fixed the issue.
  {{</ error-content>}}
{{< /error >}}

### Check that you have accepted all licenses
If not all licenses is accepted you will not be able to clean gradle or build android.

__To accept all do the following:__

Go to the folder were the sdkmanager is.
`cd ~/Library/Android/sdk/tools/bin/`

__Then run:__
`./sdkmanager --licenses`

__On windows you do:__
`cd /d "%ANDROID_SDK_ROOT%/tools/bin"`
`sdkmanager --licenses`

## Issues and solutions

### Android play music even if set to mute.
Upgraded settings gradle: https://github.com/react-native-community/react-native-video/issues/1201#issuecomment-561159924

We upgraded react-native-video to 4.4.5
Got an error regarding Lottie. Fixed it by adding:

```
implementation 'com.android.support:support-v13:26.0.2'
```

https://stackoverflow.com/questions/51207566/cannot-resolve-symbol-viewcompat

Run `.gradlew clean`
 