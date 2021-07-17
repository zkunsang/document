ios에 archive를 하고 나서 리젝이 되었다.
리젝 사유는

> Dear Developer,
> We identified one or more issues with a recent delivery for your app, "StorySelfDev" 1.0.2 (0). Please correct the following issues, then upload again.
>
> **ITMS-90809: Deprecated API Usage** - New apps that use UIWebView are no longer accepted. Instead, use WKWebView for improved security and reliability. Learn more (https://developer.apple.com/documentation/uikit/uiwebview).
> Though you are not required to fix the following issues, we wanted to make you aware of them:
>
> **ITMS-90078: Missing Push Notification Entitlement** - Your app appears to register with the Apple Push Notification service, but the app signature's entitlements do not include the 'aps-environment' entitlement. If your app uses the Apple Push Notification service, make sure your App ID is enabled for Push Notification in the Provisioning Portal, and resubmit after signing your app with a Distribution provisioning profile that includes the 'aps-environment' entitlement. Xcode does not automatically copy the aps-environment entitlement from provisioning profiles at build time. This behavior is intentional. To use this entitlement, either enable Push Notifications in the project editor's Capabilities pane, or manually add the entitlement to your entitlements file. For more information, see https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/HandlingRemoteNotifications.html#//apple_ref/doc/uid/TP40008194-CH6-SW1.
> Best regards,
> The App Store Team

Deprecated API Usage UIWebView 는 더 이상 사용할 수 없다.  
예전에 에러가 나서 manifest에서 google signin $lt;이런식으로 작성한 내용이 있는데 5.0.2

`GoogleSignInDependencies.xml`

```xml
<iosPod name="GoogleSignIn" version="&lt; 5.0.0" bitcodeEnabled="false"
minTargetSdk="6.0">
```

해당 내용을 가장 최신 5.0.2로 수정 해 줘야 한다.

```xml
<iosPod name="GoogleSignIn" version="5.0.2" bitcodeEnabled="false"
minTargetSdk="6.0">
```

`GoogleSignIn.mm`에서 여전히 에러가 발생한다.

깃허브 google-signin-unity pull request에

https://github.com/googlesamples/google-signin-unity/pull/126

Update iOS pod to >= 5.0.0 and apply migrations for native plugin code. 에서 commits를 보면서 mm파일들을 수정하면 된다.

`GoogleSignIn.h`

```objc
#import <GoogleSignIn/GIDSignIn.h>
 @interface GoogleSignInHandler
     : UIViewController <GIDSignInDelegate>

 @end
```

`GoogleSignIn.mm`

```objc
void *GoogleSignIn_SignInSilently() {
   SignInResult *result = startSignIn();
   if (!result) {
     [[GIDSignIn sharedInstance] restorePreviousSignIn];
     result = currentResult_.get();
   }
   return result;
```

```objc
case kGIDSignInErrorCodeKeychain:
         currentResult_->result_code = kStatusCodeInternalError;
         break;
//          case kGIDSignInErrorCodeNoSignInHandlersInstalled:
//          currentResult_->result_code = kStatusCodeDeveloperError;
//          break;
       case kGIDSignInErrorCodeHasNoAuthInKeychain:
         currentResult_->result_code = kStatusCodeError;
         break;
```

`GoogleSignInAppController.mm`

```objc
//line 78
GIDSignIn *signIn = [GIDSignIn sharedInstance];
   signIn.clientID = clientId;
   signIn.presentingViewController = gsiHandler;
   signIn.delegate = gsiHandler;
```

```objc
//line 99
return [[GIDSignIn sharedInstance] handleURL:url] || handled;
```

```objc
//line 113
return [[GIDSignIn sharedInstance] handleURL:url] || handled;
```

이렇게 처리하면 문제없이 돌아가나 구글 로그인을 시도 하면 바로 창이 사라지게 된다.

`google sign in unity didSignInForUser: The user canceled the sign-in flow.`

Issue 169: fix for presentingViewController crash
https://github.com/googlesamples/google-signin-unity/pull/180/commits

`GoogleSignIn.mm`

```objc
void *GoogleSignIn_SignIn() {
   [GIDSignIn sharedInstance].presentingViewController = UnityGetGLViewController();
   SignInResult *result = startSignIn();
   if (!result) {
     [[GIDSignIn sharedInstance] signIn];
```

**[GIDSignIn sharedInstance].presentingViewController = UnityGetGLViewController();**
추가해주면 된다.
