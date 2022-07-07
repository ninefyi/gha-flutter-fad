# How to deploy Flutter to Google Firebase Distribution

## References

- [guillaume.bernos.dev](https://guillaume.bernos.dev/how-to-deploy-to-firebase-app-distribution/)
- [docs.flutter.dev#deployment](https://docs.flutter.dev/deployment/android#building-the-app-for-release)
- [team-rockstars-it](https://medium.com/team-rockstars-it/the-easiest-way-to-build-a-flutter-ios-app-using-github-actions-plus-a-key-takeaway-for-developers-48cf2ad7c72a)

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

- Convert to base64

```BASH
base64 app.keystore | pbcopy
```

- Create Secrets on GitHub Settings.
  1. ANDROID_KEYSTORE
  2. ANDROID_KEYSTORE_ALIAS
  3. ANDROID_KEYSTORE_FILENAME
  4. ANDROID_KEYSTORE_PASSWORD
  5. ANDROID_KEYSTORE_PRIVATE_KEY_PASSWORD
  6. FIREBASE_TOKEN
  7. FIREBASE_ANDROID_APP_ID

## Prepare for iOS

- [Create CSR](https://help.apple.com/developer-account/#/devbfa00fef7)
- Export.P12 file using .CSR file
- Create iOS Distribution certificate
- Create Ad-hoc provisioning profile
- [Create exportOptions.plist](https://dev.to/gualtierofr/ad-hoc-distribution-for-ios-1524)
- Create Secrets on GitHub Settings
  1. FIREBASE_IOS_APP_ID
  2. FIREBASE_TOKEN
  3. BUILD_CERTIFICATE_BASE64
  4. P12_PASSWORD
  5. BUILD_PROVISION_PROFILE_BASE64
  6. KEYCHAIN_PASSWORD
