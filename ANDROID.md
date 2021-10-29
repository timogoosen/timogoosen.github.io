### Android

General page for Android stuff. Mostly related to android builds happening on CI.


### Gradle:

* [Using environment variables in gradle](https://ubuntudroid.medium.com/handling-environment-variables-in-gradle-fb1b8bb6c758)


### Plugins

* [Configure Gradle Play Publish Plugin](https://plugins.gradle.org/plugin/com.github.triplet.play/3.6.0)

### Keystore

*[Create a quick keystore file on the fly](https://github.com/facebook/react-native/issues/25629#issuecomment-513049442)

TLDR:

```

$ keytool -genkey -v -keystore debug.keystore -storepass android -alias androiddebugkey -keypass android -keyalg RSA -keysize 2048 -validity 10000


```