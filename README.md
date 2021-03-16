# IOS NS memory leak on navigation

### NS7 Enviroment

"@nativescript/core": "7.3.0"

"nativescript-vue": "^2.8.1"

"@nativescript/ios": "7.2.0"

✔ Component nativescript has 7.2.1 version and is up to date.

✔ Component @nativescript/core has 7.3.0 version and is up to date.

✔ Component @nativescript/ios has 7.2.0 version and is up to date.

### NS6 Enviroment

"tns-core-modules": "6.5.25"

"nativescript-vue": "2.4.0"

"tns-io": "6.5.4"

### Describe the bug

NS is not freeing memory on page navigations on iOS. When profiling, on each page navigation, the memory increases and app gets slower until, at some point, the app freezes or the OS terminates the app. This behaviour is restricted to IOS, we have profiled with the Android Runtime (https://github.com/NativeScript/android-runtime) and the garbage collection works as expected.  

On a very simple application, two included below, each page navigation increases the memory footprint of the app by 60 - 80 megs until the app reaches 1 - 2 Gigs and stops working. If we have a complex page, with some images, and scroll on a list then the memory increases in small iterations but once we navigate to a new page, the memory jumps byt 60 - 80 megs.

We have created several test apps with Vue and Angular and the memory leack occurs irrespective of the JS framework.  

### Solutions Tried and Reviewed
1. The smae issues has been posted previously - Memory Leak on 7.2.0 with (https://github.com/NativeScript/ns-v8ios-runtime)
   https://github.com/NativeScript/ns-v8ios-runtime/issues/105

    EnableProdMode: Is there something similar to enable prod mode on vuejs
    https://github.com/NativeScript/nativescript-angular/issues/1215
    Markingmode: https://nativescript.org/blog/markingmode-none-is-official-boost-android-performance-while-avoiding-memory-issues/

3. Downgraded Nativescript iOSCore to 6.5.4 (https://github.com/NativeScript/ios-runtime)
   We experience the same issues with the older runtime. 

5. Manually destroyed the component
   https://github.com/nstudio/nativescript-videoplayer/issues/129

6. Tried with Angular (its happening even on the creation project templates)

7. Tried with the templates project with 6.5.4

8. Set the V8flags in the config for IOS (on the V8 Runtime https://github.com/NativeScript/ns-v8ios-runtime)

9. Navigating with the clearHistory flag (set to true) and navigateBack method = same result

10. Tested on simulators and real iPhones. (iOS 12.4.8, iOS 13.1, 13.3.1)

11. Tested with different Layouts (complex and simple)

12. Manually calling the GC in the navigate back method reduces the memory by a small percentage (0.1% - 0.3%). 

13. As mentioned, it works on Android, see the profiling from below.
![android memory metrics](https://i.ibb.co/nrF6Ltj/image.png)

### Project Examples

We include two sample projects, the first is NS7 and the second NS6, both exhibt the same memory leaks.

NS7: https://github.com/alkimiiapps/memoryleakexample

NS6: https://github.com/alkimiiapps/ns6test

### Example Video of the memory reaching 0.5 Gig

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/oHAyKfUyq6M/0.jpg)](https://www.youtube.com/watch?v=oHAyKfUyq6M)

