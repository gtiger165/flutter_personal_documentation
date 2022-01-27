# personal_documentation
Personal notes about flutter 

## Coding Documentation

### SharedPrefUtil
Example helper class for shared preferences library (For android)

```dart
import "../utils/shared_pref_util.dart"

// class helper untuk local cache / SharedPreferences
class SharedPrefUtil {
  // Contoh inisiasi key untuk shared preferences 
  static const String _keyPrefs = "key_preference";

  ....

  // keyword Params bisa berupa tipe data, model/data class, dan lain-lain 
  static Future<void> setPreferencesValue(Params params) async {
    // Setiap pembuatan method helper diperlukan line berikut
    final SharedPreferences _prefs = await SharedPreferences.getInstance();
    // fungsi setter preferences dari bawaan library shared preferences
    _prefs.setParams(_keyPrefs, params);
  }

  static Future<Params> getPreferencesValue() async {
    final SharedPreferences _prefs = await SharedPreferences.getInstance();
    // fungsi setter preferences dari bawaan library shared preferences
    return await _prefs.getType(_keyPrefs);
  }

  ....
}

// sample usage
// set value
SharedPrefUtil.setPreferencesValue(Params);

// get value
SharedPrefUtil.getPreferencesValue().then((value) {
   // lakukan apa yang diperlukan seperti inisiasi ke
   // tipe data yang diinginkan dan lain-lain
   ....
});
```

### Flutter Build Apk 
Add this parameter when build apk/appbundle to reduce it size.<br>
source: https://stackoverflow.com/questions/55536637/how-to-build-signed-apk-from-android-studio-for-flutter <br>
```bash
flutter build apk --target-platform android-arm,android-arm64,android-x64 --split-per-abi
```

### FlutterFire Problem
On firebase documentation flutter, recommended installation using firebase cli (flutterfire). There gonna be problem on permission, so when you want to configure firebase on flutter project, use this command: <br>
```bash
sudo flutterfire configure
```
source: https://stackoverflow.com/questions/38067572/firebase-tools-error-eacces-permission-denied <br>
https://github.com/invertase/flutterfire_cli/issues/27#issuecomment-1002965081 <br>

### Android 12 Exported Policy
New policy from google play store, on android 12 required exported on activity, receiver, service, and provider in AndroidManifest.xml. <br>
source : <br>
- https://stackoverflow.com/questions/69287478/androidexported-added-but-still-getting-error-apps-targeting-android-12-and-hig <br>
- https://stackoverflow.com/questions/68554294/androidexported-needs-to-be-explicitly-specified-for-activity-apps-targeting<br>
