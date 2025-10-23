# Making an ATAK Plugin — Quick Start Guide

This short guide walks through the minimal steps to build and install a simple **HelloWorld** ATAK plugin using the **ATAK-CIV SDK**.  
It assumes you have a working development machine and some basic Android Studio experience.

---

## 🧰 Requirements

Before starting, make sure you have:

- **Android Studio** (latest stable version)  
  👉 [Download from developer.android.com/studio](https://developer.android.com/studio)  
- **Android SDK Platform 21** (Android 5.0 / Lollipop)  
  ATAK requires **API level 21** or higher.  
- **ATAK-CIV SDK**  
  👉 [GitHub – deptofdefense/AndroidTacticalAssaultKit-CIV](https://github.com/deptofdefense/AndroidTacticalAssaultKit-CIV)

---

## 1. Install Android Studio

Download and install Android Studio using the default installer for your OS.  
Then open the **SDK Manager** and ensure that **API level 21** (Android 5.0) is installed.

> 💡 Even if you already have newer SDKs, API 21 is required for ATAK builds.

---
![flow](atak01/atak.png)

## 2. Clone the ATAK SDK

Clone or download the official ATAK-CIV repository:

```bash
git clone https://github.com/deptofdefense/AndroidTacticalAssaultKit-CIV.git
```
Inside this repo, locate the plugin-examples folder — it includes several working examples, including HelloWorld.

## 3. Copy the HelloWorld Example

Copy the helloworld example from the SDK into your working plugins folder, or open it directly in Android Studio.

The HelloWorld plugin is a good starting point because it demonstrates the basic structure of an ATAK plugin project.

## 4. Generate a Signing Key (Keystore)

ATAK plugins must be signed before installation.
Create a debug keystore using the keytool command (included with the JDK):

```bash
keytool -genkeypair \
  -alias androiddebugkey \
  -keyalg RSA \
  -keysize 2048 \
  -validity 9999 \
  -keystore debug.keystore \
  -storepass android \
  -keypass android \
  -dname "CN=Android Debug,O=Android,C=US"
```

## 5. Update the key locations

```bash
sdk.dir=/home/aviondock/Android/Sdk
takDebugKeyFile=<your location>/plugins/helloworld/debug.keystore
takDebugKeyFilePassword=android
takDebugAlias=androiddebugkey
takDebugKeyPassword=android

takReleaseKeyFile=<your location>/plugins/helloworld/release.keystore
takReleaseKeyFilePassword=android
takReleaseAlias=androidreleasekey
takDebugKeyPassword=android
```
## 6. Select the Correct Build Variant

In Android Studio, open the Build Variants panel (bottom-left corner).
Select the variant civDebug — this matches the developer ATAK build shipped in the SDK.

🚫 The Google Play ATAK app will not load custom plugins.
Use the developer ATAK APK from the SDK instead.
