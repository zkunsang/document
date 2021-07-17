# 유니티 Android, iOS, 파이어베이스를 이용한 애플, 구글 로그인 구현

- 구글 플레이 콘솔
- 구글 클라우드 플랫폼이 존재
- 파이어 베이스

## - 구글 플레이 콘솔

1. 앱 만들기
2. 새 버전 만들기 > 인증 키 생성에 관한 질문에 구글
   <img src="img/readme1/AppSign1.png"/>

- 구글에서 관리를 선택하면
- 앱 무결성에서 앱 서명 키 인증서를 생성해 준다.
  <img src="img/readme1/AppSign2.png"/>

3. 앱 키를 만들기 위해서 빌드를 한번 실행

- 앱 빌드 실행
- 서명 필요
  <img src="img/readme1/AppBuild1.png"/>
- 서명한 빌드는 업로드 키 인증서가 생성된다.
  <img src="img/readme1/AppBuild2.png"/>

---

## - 파이어베이스

- 프로젝트 생성
  <img src="img/readme1/Firebase1.png"/>
- 구글 애널리틱스 구성
  <img src="img/readme1/Firebase2.png"/>

---

## - 구글 클라우드 플랫폼

- 파이어 베이스 프로젝트와 구글 클라우드 플랫폼의 프로젝트 확인
  <img src="img/readme1/Firebase3.png"/>
  <img src="img/readme1/GoogleCloudPlatform1.png"/>

---

## - 파이어 베이스

- 프로젝트 앱 등록 > 유니티 선택
  <img src="img/readme1/Firebase4.png"/>
- 패키지 이름 등록
- 구성 파일 다운로드(json, plist) > 유니티 assets에 복사
- 파이어 베이스 SDK추가(Auth/analytics)

`- google-services.json`

```json
{
  "project_info": {
    "project_number": "140717200891",
    "project_id": "loginsample-6b700",
    "storage_bucket": "loginsample-6b700.appspot.com"
  },
  "client": [
    {
      "client_info": {
        "mobilesdk_app_id": "1:140717200891:android:cc3201b0a91789e0f2675e",
        "android_client_info": {
          "package_name": "com.zkunsang.LoginSample"
        }
      },
      "oauth_client": [
        {
          "client_id": "140717200891-8hoeqhb0r46ap649j99rjgi6qq05pick.apps.googleusercontent.com",
          "client_type": 3
        }
      ],
      "api_key": [
        {
          "current_key": "AIzaSyCL0C4aGgN6YZTpX2TMfMuwpZLnrAL0QQE"
        }
      ],
      "services": {
        "appinvite_service": {
          "other_platform_oauth_client": [
            {
              "client_id": "140717200891-8hoeqhb0r46ap649j99rjgi6qq05pick.apps.googleusercontent.com",
              "client_type": 3
            },
            {
              "client_id": "140717200891-t2uhbttao9de1vj6hk2n5qtoiia5q2ic.apps.googleusercontent.com",
              "client_type": 2,
              "ios_info": {
                "bundle_id": "com.zkunsang.LoginSample"
              }
            }
          ]
        }
      }
    }
  ],
  "configuration_version": "1"
}
```

`- GoogleService-Info.plist`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>CLIENT_ID</key>
	<string>140717200891-t2uhbttao9de1vj6hk2n5qtoiia5q2ic.apps.googleusercontent.com</string>
	<key>REVERSED_CLIENT_ID</key>
	<string>com.googleusercontent.apps.140717200891-t2uhbttao9de1vj6hk2n5qtoiia5q2ic</string>
	<key>API_KEY</key>
	<string>AIzaSyBSneJVOFgXZxRsE_WSByBUVOx7PQ0e0GM</string>
	<key>GCM_SENDER_ID</key>
	<string>140717200891</string>
	<key>PLIST_VERSION</key>
	<string>1</string>
	<key>BUNDLE_ID</key>
	<string>com.zkunsang.LoginSample</string>
	<key>PROJECT_ID</key>
	<string>loginsample-6b700</string>
	<key>STORAGE_BUCKET</key>
	<string>loginsample-6b700.appspot.com</string>
	<key>IS_ADS_ENABLED</key>
	<false></false>
	<key>IS_ANALYTICS_ENABLED</key>
	<false></false>
	<key>IS_APPINVITE_ENABLED</key>
	<true></true>
	<key>IS_GCM_ENABLED</key>
	<true></true>
	<key>IS_SIGNIN_ENABLED</key>
	<true></true>
	<key>GOOGLE_APP_ID</key>
	<string>1:140717200891:ios:82fce74b5e10dabaf2675e</string>
</dict>
</plist>
```

---

## - 구글 클라우드 플랫폼

Api 및 서비스 > 사용자 인증 정보를 확인하면 `firebase`에서 생성된 것과 `google service`에서 생성된 것이 있다.

<img src="img/readme1/GoogleCloudPlatform2.png"/>

`- google-services.json`의 apiKey와 `Android key` 의 apiKey가 동일하다

`- GoogleService-Info.plist`의 apiKey와 `iOS key` 의 apiKey가 동일하다

<img src="img/readme1/GoogleCloudPlatform4.png"/>

---

**iOS 클라이언트 아이디**  
`t2uhbttao9de1vj6hk2n5qtoiia5q2ic`

`- GoogleService-Info.plist`

```xml
    <key>CLIENT_ID</key>
	<string>140717200891-t2uhbttao9de1vj6hk2n5qtoiia5q2ic.apps.googleusercontent.com</string>
```

`- google-services.json`

```json
"services": {
        "appinvite_service": {
          "other_platform_oauth_client": [
            ...,
            {
              "client_id": "140717200891-t2uhbttao9de1vj6hk2n5qtoiia5q2ic.apps.googleusercontent.com",
              "client_type": 2,
              "ios_info": {
                "bundle_id": "com.zkunsang.LoginSample"
              }
            }
          ]
        }
```

이렇게 일치하고

**웹 애플리케이션의 클라이언트 id**
`8hoeqhb0r46ap649j99rjgi6qq05pick`  
`- google-services.json`의 oAuth clientId와

```json
"oauth_client": [
    {
        "client_id": "140717200891-8hoeqhb0r46ap649j99rjgi6qq05pick.apps.googleusercontent.com",
        "client_type": 3
    }],
    "services": {
        "appinvite_service": {
          "other_platform_oauth_client": [
            {
              "client_id": "140717200891-8hoeqhb0r46ap649j99rjgi6qq05pick.apps.googleusercontent.com",
              "client_type": 3
            },
          ]
        }
      }
```

이렇게 일치한다.
