---
layout: single
title: "[XCode] xcframework 생성"
---

Step 1
- 프로젝트 경로 이동

```
cd path/to/Sample
```

Step 2
- 아카이브

```
xcodebuild archive -scheme Sample -archivePath ./Builds/iOS.xcarchive -sdk iphoneos SKIP_INSTALL=NO BUILD_LIBRARY_FOR_DISTRIBUTION=YES

```

Step 3
- xcframework 변환

```
xcodebuild -create-xcframework \
-framework ./Builds/iOS.xcarchive/Products/Library/Frameworks/OCRFramework.framework \
-output ./Builds/Sample.xcframework
```
