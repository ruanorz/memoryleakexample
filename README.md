# NS memory leak on navigations

### Enviroment

"@nativescript/core": "7.3.0"

"nativescript-vue": "^2.8.1"

"@nativescript/ios": "7.2.0"

✔ Component nativescript has 7.2.1 version and is up to date.

✔ Component @nativescript/core has 7.3.0 version and is up to date.

✔ Component @nativescript/ios has 7.2.0 version and is up to date.


### Describe the bug

NS is not freeing memory on page navigations on iOS. When profilinign, on each page navigation, the memory is increasing, app is getting slower and at some point the OS terminates the app. This behaviour is restricted to IOS, we have profiled with the Android Runtime (https://github.com/NativeScript/android-runtime) and the garbage collection works as expected.  

### Solutions Tried and Reviewed
1. Memory Leak on 7.2.0 with (https://github.com/NativeScript/ns-v8ios-runtime)
https://github.com/NativeScript/ns-v8ios-runtime/issues/105
When profiling, this seems to be the same issue that we have experience.

	@@ -14,33 +22,37 @@ https://github.com/NativeScript/nativescript-angular/issues/1215
EnableProdMode: Is there something similar to enable prod mode on vuejs
Markingmode: https://nativescript.org/blog/markingmode-none-is-official-boost-android-performance-while-avoiding-memory-issues/

3. Downgraded Nativescript iOSCore to 6.5.4 (https://github.com/NativeScript/ios-runtime)
   We experience the same issues with the older runtime. 

5. Manually destroying the component
   https://github.com/nstudio/nativescript-videoplayer/issues/129

6. Trying with Angular(its happening even on the creation project templates)

7. Trying with the templates project with 6.5.4

8. Setting the V8flags in the config for IOS

9. Trying with clearHistory flag and navigateBack method = same result

10. Tested on simulators and real iPhones. (iOS 12.4.8, iOS 13.1, 13.3.1)

11. Tested with different Layouts (complex and simples)

12. Manually calling the GC

13. It works on Android
![android memory metrics](https://i.ibb.co/nrF6Ltj/image.png)

### Project Examples

NS7: https://github.com/alkimiiapps/memoryleakexample

NS6: https://github.com/alkimiiapps/ns6test

### Metrics

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/oHAyKfUyq6M/0.jpg)](https://www.youtube.com/watch?v=oHAyKfUyq6M)

