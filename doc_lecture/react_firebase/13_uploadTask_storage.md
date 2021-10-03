# 파일 업로드 상황
```js
let uploadTask = storageRef.child(filePath).put(file, metadata);

uploadTask.on("state_changed", UploadTaskSnapshot => {
    console.log(UploadTaskSnapshot);
    const percentage = Math.round((UploadTaskSnapshot.bytesTransferred / UploadTaskSnapshot.totalBytes) * 100)
    setPercentage(percentage);
},
    err => {
        console.error(err)
        setLoading(false);
    },
    () => {
        //저장이 다 된후에 파일 메시지 전송(데이터베이스에 저장)
        //저장된 파일을 다운로드 받을 수 있는 URL가져오기
        uploadTask.snapshot.ref.getDownloadURL().then(downloadURL => {
            // download url을 확인할 수 있다.
            // console.log("downloadURL", downloadURL);
            messageRef.child(chatRoom.id).push().set(createMessage(downloadURL));
            setLoading(false);
        });
    })
```
