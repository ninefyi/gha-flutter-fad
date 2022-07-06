# How to deploy Flutter to Google Firebase Distribution

## References

- [guillaume.bernos.dev](https://guillaume.bernos.dev/how-to-deploy-to-firebase-app-distribution/)
- [docs.flutter.dev#deployment](https://docs.flutter.dev/deployment/android#building-the-app-for-release)

## Prepare for Flutter (Tested on Mac)

- [Install Firebase CLI](https://firebase.google.com/docs/cli)
- Get Firebase Token

```BASH
firebase login:ci
```

## Prepare for Android

- Create .jks file

```BASH
  keytool -genkey -v -keystore ~/upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

- Create Secrets on GitHub Settings.
  1. ANDROID_KEYSTORE
  2. ANDROID_KEYSTORE_ALIAS
  3. ANDROID_KEYSTORE_FILENAME
  4. ANDROID_KEYSTORE_PASSWORD
  5. ANDROID_KEYSTORE_PRIVATE_KEY_PASSWORD
  6. FIREBASE_TOKEN

## Prepare for iOS