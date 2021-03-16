# NativeScript-Vue Application

> A native application built with NativeScript-Vue

### Problems with Navigation and Memory Leaks

Solutions Tried and Reviewed: 

1. Memory Leak on 7.2.0
https://github.com/NativeScript/ns-v8ios-runtime/issues/105

2. Memory Leak 2018
https://github.com/NativeScript/nativescript-angular/issues/1215
EnableProdMode: Is there something similar to enable prod mode on vuejs
Markingmode: https://nativescript.org/blog/markingmode-none-is-official-boost-android-performance-while-avoiding-memory-issues/

3. Downgraded Nativescript Core to 6.5.4 (with old JS engine)

4. Manually destroying the component
   https://github.com/nstudio/nativescript-videoplayer/issues/129

5. Trying with Angular

6. Trying with the demo project with 6.5.4 - @jose

7. Setting the V8flags in the config for IOS

## Usage

``` bash
# Install dependencies
npm install

# Preview on device
tns preview

# Build, watch for changes and run the application
tns run

# Build, watch for changes and debug the application
tns debug <platform>

# Build for production
tns build <platform> --env.production

```
