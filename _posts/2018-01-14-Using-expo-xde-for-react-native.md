---

layout: post
title:  "Using expo xde for react native"
subtitle: 'It help you start with expo for develop web application using the react native.'
date:   2018-01-14
categories: react-native
cover: 
tags: react-native expo
---


## expo는 무엇인가
react native로 개발할 때 테스트 및 배포를 쉽게 해주는 툴이다. 홈페이지를 가보면 내용들이 굉장히 많이 있지만 내가 본 중요한 기능은 아래와 같다. 

* 에뮬레이터 실행 (ios, android)
* 네이티브 API 호출
* 로그 확인
* 빌드 (ipa, apk 파일)
* 원격 앱 업데이트 


## What is the expo.
It help you do test and build using react native. Although there are many things in official homepage, From what I saw, it is important features below.

* Launch both IOS and Android emulator.
* Call the native API.
* Log Monitoring.
* Make ipa and apk easily.
* Remote app update.

## 들어가기 전에...
 당연한 이야기지만 ios와 관련된 개발을 하려면 mac이 있어야 한다. 오늘은 설치 후 에뮬레이터 실행, 테스트하는 방법까지만 알아보려고 한다. 나는 mac과 아이폰을 사용하고 있기 때문에 android를 위한 방법은 설명하지 않을것이다. 하지만 에뮬레이터 차이이기 때문에 IOS와 크게 다르지 않을것이다.

## Before starting...
  If you want to develop IOS, Of course, you must have a Mac. Today, We are going to launch a emulator and monitor log. This post for IOS because I use both mac and iphone. But also android will be not much different.
 
## expo xde 설치방법
 [홈페이지](https://expo.io)에 접속해서 tools 메뉴에 들어간다. 페이지 하단에 보면 expo xde가 있는데 링크로 들어가서 자신의 OS에 맞는 설치파일을 다운로드 받자. 메뉴를 찾기 어렵다면 [링크](https://github.com/expo/xde)로 바로 접속해보자.

## setting up expo xde
 Click [Hompage](https://expo.io) and move to tools in menu. There are link for expo xde below hompage. click the link and download setup file. If you don't know what i said, just [Click](https://github.com/expo/xde) and download file.


## 사용방법

## How to use

**프로젝트 시작하기.**  
 설치를 끝내고 실행해보면 굉장히 쉽게 프로젝트를 만들 수 있다. 먼저 프로그램을 실행하면 로그인을 하라고 나오는데 깃허브와 연동해서 회원가입을 해도 되고 일반 이메일로 가입해도 된다.  

 **Starting project.**  
 It is very easy to make react native project. After installing apllication, open the program. If you don't have id, sign up. It dosen't matter using github or other email.

![로그인(login)]({{site.url}}/assets/post/20180114/login.png)

 로그인 후 'Create new project...' 버튼을 클릭하면 blank 프로젝트로 시작할지 네비게이션 버튼이 있는 프로젝트로 시작할지 선택할 수 있는데, 여기선 blank 형식으로 시작했다. 각각 프로젝트를 설치할 경로와 프로젝트 이름을 설정하고 create 버튼을 누르기만 하면 기본적인 프로젝트 설치가 마무리 된다.  

 After login, you have to click button 'Create new project...' then pop up the dialog for choosing blank or navigate project. In my case, I chose blank project. Setting the project name and location. It will be made after clicking create button 

![메인화면(main)]({{site.url}}/assets/post/20180114/main.png)

![생성(create)]({{site.url}}/assets/post/20180114/create.png)

**에뮬레이터 실행방법**  
 처음에 react native와 관련된 설정이 끝나면 오른쪽 위에 device 라는 버튼이 있다. 각각 IOS와 Android 에뮬레이터를 실행할 수 있으며 혹시 IOS 시뮬레이터를 실행시켰을때 오류가 난다면 xcode를 실행해서 추가로 받아야 될 컴포넌트들이 있는지 확인한다. 오류가 나지 않는다면 시뮬레이터가 실행되면서 자동으로 실행될 것이다.  

**How to run emulator.**  
there are device button on the right header. You could run IOS emulator and Android emulator. Do you by any chance see a error message after run IOS emulator? you have to run xcode and check if it is latest version or not. If you don't see it, it will open the emulator.

![기본화면(default)]({{site.url}}/assets/post/20180114/default.png)


 이제 sublime text나 intellij와 같은 다른 IDE에서 이 프로젝트를 불러와서 App.js를 수정해 보자. 그러면 expo에서 파일이 바뀐걸 감지해서 에뮬레이터 화면이 자동으로 바뀌는걸 볼수 있을것이다. 기본적으로 Live Reload 기능이 켜져 있는데 이 기능을 끄거나 다른 설정을 하고 싶다면 자신에게 맞게 설정해 보자. 이번엔 간단하게 Hot Reloading과 Live Reload에 차이점을 비교해 보겠다.
 
  - Live Reload : 수정된게 확인 되면 페이지를 새로고침한다. (F5를 누른것과 같은 효과)
  - Hot Reloading : 수정된 파일만 다시 불러온다. (AJAX로 페이지를 가져와서 다시 보여지게 하는것과 같은 효과)
 

Now, Let's modify App.js in IDE like submlime text and intellij. you can see to change the view automatically. Basically, it enabled live reload. If you want to disable it or change other config, you could change that. I think it is important to know between Live Reload and Hot Reloading.

  - Live Reload : Reload the page if js was changed. (it is similor to pressing the F5). 
  - Hot Reloading : Change the file what was changed. (it is similor to call the ajax and replace page)


![에뮬레이터(emulator)]({{site.url}}/assets/post/20180114/emulator.png)

![설정(config)]({{site.url}}/assets/post/20180114/config.png)


**핸드폰에서 확인하는 방법**  
 진동이나 카메라와 같이 에뮬레이터가 아닌 기기에서 확인하고 싶은 기능이 있다면 핸드폰에서도 테스트할 수 있다.  
 먼저 핸드폰 앱스토어에 접속 후 expo client 앱을 설치해보자. 
 그러면 QR코드를 스캔할수 있는 버튼이 보일텐데 이걸 누른 후 이제 expo xde에 있는 share버튼을 눌러서 나오는 qr코드를 핸드폰으로 찍어보자. 그러면 핸드폰으로 내가 만든 프로젝트에 접속할 수 있게 된다. 물론 아까 설명한 Live Reload 기능까지 사용 가능하며 로그까지 제대로 찍혀서 나오는 것을 확인할 수 있을것이다.

**Connection with your phone**  
you also do a test like vibration and camera using your phone.  
First of all, install a expo client app in app store.  
Secondly, you could see a butoon for scanning QR code after running application.  
Finally, you should click the share button in expo xde before pushing the button, then scan the QR code using your phone. you must have connected your project.  
Also you could use the Live Reload and see a log.

## 마치며...
이 것으로 expo를 사용하여 React Native를 테스트하는 방법을 알아보았다. 아직 어떤 기능들이 있는데 전부 파악하지는 못했지만 충분히 메리트가 있다고 생각한다. xcode와 android studio를 동시에 사용하면서 에뮬레이터를 돌릴 필요도 없고 따로따로 빌드를 할 필요도 없으니까 말이다. 혹시 내용중에 잘못된게 있다면 피드백을 부탁한다.

## Completing the post.
We learned how to test for react native using expo. I don't know features at all. But it is worth the time to learn. We don't have to spend time to run emulator using xcode and android.  
Please give me feedback if something goes wrong above.