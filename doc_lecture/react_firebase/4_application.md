# 어플리케이션
통상적으로 (웹소켓)socket.io를 통해서 만들지만

# Rest VS websockets
Rest한방향 통신  
websocket 양방향 통신

# Firebase에 관해
RTSP Real Time Stream Protocol 방식을 지원

# Firebase 설치
npm install firebase --save

``` js
import firebase from 'firebase/app';
import 'firebase/auth';
import 'firebase/database';
import 'firebase/storage';


const firebaseConfig = {
    apiKey: "****",
    authDomain: "****",
    projectId: "****",
    storageBucket: "****",
    messagingSenderId: "****",
    appId: "****",
    measurementId: "****"
};

firebase.initializeApp(firebaseConfig);
```