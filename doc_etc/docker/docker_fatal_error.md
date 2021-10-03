# docker로 몽고를 띄웠는데 27017 socket error
socket이 미리 열린 상태로 docker가 내려갔는지 더 이상 docker start를 할 수가 없는 상황이 왔다.


``` sh
docker commit $STOPPED_CONTAINER user/test_image
docker run -ti --entrypoint=sh user/test_image
```

를 통해서 기존 컨테이너를 복사 한 후에
docker inspect 로 멈춰 있던 docker의 볼륨을 찾고
새로 만든 container의 docker/data에 다가 파일들을 복사해서 넣어주면 정상적으로 데이터를 가져올 수 있다.

