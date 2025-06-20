**Michigan UP Adventure Map - Android Project Setup Guide**

---

### Project Structure

Create these files in your Windsurf project

```
pgsql
CopyEdit
UPAdventureMap/
+-- app/
¦   +-- java/com/uptrip/adventuremap/
¦   ¦   +-- MainActivity.kt
¦   +-- res/
¦       +-- layout/
¦       +-- values/
¦       ¦   +-- strings.xml
¦       +-- mipmap/
¦   +-- AndroidManifest.xml
+-- build.gradle
+-- settings.gradle

```

---

### File Contents

### 1. `settings.gradle` (Project root)

```groovy
groovy
CopyEdit
include ':app'

```

---

### 2. `build.gradle` (Project root)

```groovy
groovy
CopyEdit
buildscript {
    ext.kotlin_version = '1.6.10'
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:7.0.4'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
allprojects {
    repositories {
        google()
        mavenCentral()
    }
}

```

---

### 3. `build.gradle` (App-level)

```groovy
groovy
CopyEdit
plugins {
    id 'com.android.application'
    id 'kotlin-android'
}

android {
    compileSdk 31

    defaultConfig {
        applicationId "com.uptrip.adventuremap"
        minSdk 21
        targetSdk 31
        versionCode 1
        versionName "1.0"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    buildFeatures {
        viewBinding true
    }
}

dependencies {
    implementation "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
    implementation 'androidx.core:core-ktx:1.7.0'
    implementation 'androidx.appcompat:appcompat:1.4.1'
    implementation 'com.google.android.material:material:1.5.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.3'
}

```

---

### 4. `AndroidManifest.xml`

```xml
xml
CopyEdit
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.uptrip.adventuremap">

    <applicationandroid:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.UPAdventureMap">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```

---

### 5. `strings.xml`

```xml
xml
CopyEdit
<resources>
    <string name="app_name">UPAdventureMap</string>
</resources>

```