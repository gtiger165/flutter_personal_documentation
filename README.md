# flutter_personal_documentation
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
