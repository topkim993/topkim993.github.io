---
layout: single
title: "[XCode] Wrapping Objc Static Library(`*.a` File) to Framework"
---

## Step 1
- 프레임워크 프로젝트 생성
    - 테스트를 위해 2개 생성 했음 (Swift Base, Objc Base)
    
## Step 2
- 프레임워크 프로젝트에 스테틱 라이브러리 넣기 
    - `.a` 파일 및 헤더 파일 프로젝트에 넣기
    - Build Setting의 Library Search Paths 확인

## Step 3
- Mach-O Type 변경
    - Static Library로 변경

## Step 4
- 외부에 공개할 Header 정보 등록
    - Build Phases Header의 Project -> Public으로 변경
    - 프로젝트 Header 파일에 외부에 공개할 헤더 정보 import

## Step 5
- 프로젝트 경로 이동
```
cd path/to/Sample
```

## Step 6
- 아카이브
```
xcodebuild archive -scheme OCRManager -archivePath ./Builds/iOS.xcarchive -sdk iphoneos SKIP_INSTALL=NO BUILD_LIBRARY_FOR_DISTRIBUTION=YES
```

## Step 7
- xcframework 변환
```
xcodebuild -create-xcframework \
-framework ./Builds/iOS.xcarchive/Products/Library/Frameworks/OCRManager.framework \
-output ./Builds/OCRManager.xcframework
```

## Step 8
- 앱 타겟에 추가
    - 프레임워크 앱타겟에 추가
    - 프레임워크 Embed 타임 Do not Embed로 변경
    - Static lib 인식을 위한 더미 objc 파일 추가  
    
## Step 9
- 스위프트 소스에서 import 해서 사용
