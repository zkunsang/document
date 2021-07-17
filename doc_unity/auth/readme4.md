# Authentication(Apple) on Android

<img src="img/readme4/appleloginSetting01.png"/>
<img src="img/readme4/appleloginSetting02.png"/>
<img src="img/readme4/appleloginSetting03.png"/>
<img src="img/readme4/appleloginSetting04.png"/>
<img src="img/readme4/appleloginSetting05.png"/>
<img src="img/readme4/appleloginSetting06.png"/>

1. 애플 앱 생성
2. 애플 서비스 생성

해당 주소를 호스팅 서비스 해야한다.

애플 Services 에서  
Return URLs  
https://loginsample-6b700.firebaseapp.com/__/auth/handler

subdomain
loginsample-6b700.firebaseapp.com

http://monibu1548.github.io/2019/11/18/signin-apple/

2021-04-04 23:43:36.905 9086 9086 Error AndroidRuntime java.lang.NoClassDefFoundError: Failed resolution of: Landroidx/browser/customtabs/CustomTabsIntent$Builder;

appDependencies.xml에 추가하자

```xml
<androidPackage spec="androidx.browser:browser:1.2.0">
</androidPackage>
```

그리고 유니티에서 안드로이드 리졸브를 해주면 된다.

Apple 팀 ID
키 ID를 생성해 줘야 한다. **_끗_**
<img src="img/readme4/appleloginSetting07.png"/>
