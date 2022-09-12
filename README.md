
Cordova LibCXX Plugin
=========================

This plugin is intended to be used as a peer dependency, for android cordova plugins that includes or uses C++ libraries.

There must be exactly one copy of the `libc++_shared.so` in the application, otherwise undefined behaviour may occur. For this reason, plugins cannot provide their own copy of the native library, and is why this plugin exists.

This plugin includes a prebuilt android archive that includes the `libc++_shared.so` library for the following architectures:

- arm64-v8a
- armeabi-v7a
- x86
- x86_64

The `libc++_shared.so` files was taken from the NDK installation and is taken as is, without modification. The NDK version will be found inside the filename, etc `libcxx-<version>.aar`

## Version Schema

TBD

<!--
I think what is best is to mimic the Major & Minor version of NDK. So our major & minor always represents the underlying version of NDK's major/minor. Patches will always be reserved for own builds. The issue with this, is NDK seems to use <major>.0.<build> and I assume the build number is equally important to match.
-->

## Usage

Applications should not install this package themselves. It is intended to be a dependency of other cordova plugins, that needs to have
a single copy of the libc++ shared library.

Include `<dependency id="@totalpave/cordova-plugin-libcxx" version="0.x" />`

Note: Specifying exact versions is not recommended because it may limit capability of other third-party plugins that also depend on this package.

## Android Notes

The binary is compiled with API 24, therefore the application min SDK must be 24 or later.

## License

This plugin is provided under the [Apache 2.0](./LICENSE) license. The native binaries provided in the libcxx AAR file is provided under their own respective [licenses](https://github.com/totalpaveinc/android-libcxx/blob/master/LICENSE).

## Total Pave Committers

To update this package, pull the AAR file from [android-libcxx-bin](https://github.com/totalpaveinc/android-libcxx-bin) repository.

To build a new libcxx archive, see [android-libcxx](https://github.com/totalpaveinc/android-libcxx) repository.
