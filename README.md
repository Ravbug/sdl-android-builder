# SDL Android Builder
This is a proof-of-concept wrapper repo that makes building SDL projects for Android with CMake easier.

## How To Use:
1. Place the source code for your game inside `to-build`. This repo contains an optional submodule as an example.
	- Your game source code must also configure SDL at some point. See the optional submodule for an example. 
    - Your game should call `add_library` instead of `add_execuable`, and the library must be named `main`, when building for Android.  
2. Open the root folder of this repository in Android Studio
3. Build and run!

## Getting the full commands that Gradle is running
Gradle hides this information by default. Both steps are required:
1. Add `android.native.buildOutput=verbose` to `gradle.properties`
2. Add `"-DCMAKE_VERBOSE_MAKEFILE=ON"` to `externalNativeBuild -> cmake -> arguments` in `app/build.gradle`
```gradle
android {
// ...
	externalNativeBuild {
		cmake {
			arguments "-DANDROID_STL=c++_static", "-DCMAKE_VERBOSE_MAKEFILE=ON"
	}
// ...
}
```
