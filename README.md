# CISample [![Build Status](https://travis-ci.com/efrenospino/CI-Demo.svg?branch=master)](https://travis-ci.com/efrenospino/CI-Demo)

This repository is a sample android project which holds continuous integration with Travis CI to keep track of testing and deployment. 

`.travis.yaml`
```yaml
language: android
sudo: false
before_install:
  - chmod +x gradlew
  - yes | sdkmanager "platforms;android-27"
before_script:
  - android list targets
  - echo no | android create avd --force -n test -t android-22 --abi armeabi-v7a
  - emulator -avd test -no-audio -no-window &
  - android-wait-for-emulator
  - adb shell input keyevent 82 &
android:
  components:
    - build-tools-27.0.3
    - android-22
    - addon-google_apis-google-27
    - extra-android-m2repository
    - extra-android-support
    - sys-img-armeabi-v7a-android-22
```
