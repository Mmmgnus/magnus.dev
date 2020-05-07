---
title: "Android development"
date: 2020-05-05T17:00:00+02:00
draft: false
---

# Open Android project from terminal
`android-studio .` to open folder in Android studio

# Gradle error: IllegalStateException: No value has been specified for this provider
Seems to be because the cradle file is unsync, because we have generate it with different version of gradle.

We tried to clean the gradle with `./gradlew clean` in the android folder of the project.

# Check that you have accepted all licenses
If not all licenses is accepted you will not be able to clean gradle or build android.

__To accept all do the following:__

Go to the folder were the sdkmanager is.
`cd ~/Library/Android/sdk/tools/bin/`

__Then run:__
`./sdkmanager --licenses`

__On windows you do:__
`cd /d "%ANDROID_SDK_ROOT%/tools/bin"`
`sdkmanager --licenses`
