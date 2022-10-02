# This is an Android override

See the original Geolocator plugin [at Baseflow](https://github.com/Baseflow/flutter-geolocator).

This repo is needed only when publishing at F-Droid, because it contains an untouched `geolocator_android`
plugin without the Google API. To use it, simply include this section into your `pubspec.yaml`:

```yaml
dependency_overrides:
  geolocator_android:
    git:
      url: https://github.com/Zverik/flutter-geolocator.git
      ref: floss
      path: geolocator_android
```

For an example of how it's done, see the commented out dependency override in
[this pubspec](https://github.com/Zverik/every_door/blob/main/pubspec.yaml)
and the `sed` command uncommenting in at [f-droid](https://gitlab.com/fdroid/fdroiddata/-/blob/master/metadata/info.zverev.ilya.every_door.yml).

Note that this plugin is updated by rebasing it onto the latest version from the upstream repo.
Meaning, your system may not catch up on the upstream being updated. In that case, you might need
to clean up your `.pub-cache`.

# Flutter geolocator plugin

The Flutter geolocator plugin is built following the federated plugin architecture. A detailed explanation of the federated plugin concept can be found in the [Flutter documentation](https://flutter.dev/docs/development/packages-and-plugins/developing-packages#federated-plugins). This means the geolocator plugin is separated into the following packages:

1. [`geolocator`][1]: the app facing package. This is the package users depend on to use the plugin in their project. For details on how to use the [`geolocator`][1] plugin you can refer to its [README.md][2] file.
2. [`geolocator_android`][3]: this package contains the endorsed Android implementation of the geolocator_platform_interface and adds Android support to the [`geolocator`][1] app facing package. More information can be found in its [README.md][4] file;
3. [`geolocator_apple`][5]: this package contains the endorsed iOS and macOS implementations of the geolocator_platform_interface and adds iOS and macOS support to the [`geolocator`][1] app facing package. More information can be found in its [README.md][6] file;
4. [`geolocator_web`][7]: this package contains the endorsed web implementation of the geolocator_platform_interface and adds web support to the [`geolocator`][1] app facing package. More information can be found in its [README.md][8] file;
5. [`geolocator_windows`][9]: this package contains the endorsed Windows implementation of the geolocator_platform_interface and adds Windows support to the [`geolocator`][1] app facing package. More information can be found in its [README.md][10] file;
6. [`geolocator_platform_interface`][11]: this package declares the interface which all platform packages must implement to support the app-facing package. Instructions on how to implement a platform package can be found in the [README.md][12] of the [`geolocator_platform_interface`][11] package.

[1]: ./geolocator
[2]: ./geolocator/README.md
[3]: ./geolocator_android
[4]: ./geolocator_android/README.md
[5]: ./geolocator_apple
[6]: ./geolocator_apple/README.md
[7]: ./geolocator_web
[8]: ./geolocator_web/README.md
[9]: ./geolocator_windows
[10]: ./geolocator_windows/README.md
[11]: ./geolocator_platform_interface
[12]: ./geolocator_platform_interface/README.md
