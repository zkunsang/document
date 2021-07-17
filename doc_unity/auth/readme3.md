# Authentication(Google) on Ios

<img src="img/readme3/builderror01.png"/>

unity Cannot find protocol declaration for 'GIDSignInUIDelegate'; did you mean 'GIDSignInDelegate'?

https://github.com/googlesamples/google-signin-unity/issues/102
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<dependencies>
  <!-- See https://github.com/googlesamples/unity-jar-resolver#usage for
    how to configure dependencies -->
  <androidPackages>
    <androidPackage spec="com.google.android.gms:play-services-auth:16+">
      <androidSdkPackageIds>
        <androidSdkPackageId>extra-google-m2repository</androidSdkPackageId>
      </androidSdkPackageIds>
    </androidPackage>
  </androidPackages>

  <!-- iOS Cocoapod dependencies can be specified by each iosPod element. -->
  <iosPods>
    <iosPod name="GoogleSignIn" version="&lt; 5.0.0" bitcodeEnabled="false"
        minTargetSdk="6.0">
    </iosPod>
  </iosPods>
</dependencies>

```
<img src="img/readme3/builderror02.png"/>

GKLocalPlayer

<img src="img/readme3/builderror03.png"/>
UnityFramework에 GameKit.framework추가해 주면 간단히 해결!
<img src="img/readme3/builderror04.png"/>
