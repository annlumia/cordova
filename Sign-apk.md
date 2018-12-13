# Sign the apk file
After running the build command, we will get a build file named app-realease-unsigned.apk.
This file cannot be installed directly on the device because it has not been signed.

To sign, follow the steps below:

### Create a keystore
Run following command:
```
$ keytool -genkey -v -keystore <keystore_file.keystore> -alias <keystore_alias> -keyalg RSA -keysize 2048 -validity <valid_day>
```


example:
```
$ keytool -genkey -v -keystore hotmanjw.keystore -alias hotmanjw -keyalg RSA -keysize 2048 -validity 1000
```
then fill in every question that appears.

### Sign the apk with keystore
After the keystore has been successfully created, then use the keystore to sign the apk file.

The command is:

```
$ jarsigner -sigalg SHA1withRSA -digestalg SHA1 -keystore <keystore_file.keystore> <apk_path> <keystore_alias>
```
example:
```
$ jarsigner -sigalg SHA1withRSA -digestalg SHA1 -keystore ./hotmanjw.keystore ./platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk hotmanjw
