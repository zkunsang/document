```js 
// 이부분 중요
const mapStateToProps = state => {
    console.log(state);
    return {
        user: state.user.currentUser
    }
}

export default connect(mapStateToProps)(ChatRooms)
```

redux의 스토어 정보를 사용하려면 state를 사용해야 한다.

```js
chatRooms.map(room => (
            <li key={room.id}># {room.name}</li>
        ))
```
# pub/sub같은 느낌
```js
chatRoomsRef: firebase.database().ref("chatRooms"),

AddChatRoomsListeners = () => {
        let chatRoomsArray = [];
        this.state.chatRoomsRef.on("child_added", DataSnapShot => {
            chatRoomsArray.push(DataSnapShot.val());
            this.setState({ chatRooms: chatRoomsArray });
        })
    }
    const key = this.state.chatRoomsRef.push().key;
```

# 함수형 리턴과 함수의 차이가 있을까?
```js
<li
    key={room.id}
    onClick={this.changeChatRoom(room)}
    style={{ backgroundColor: room.id === this.state.activeChatRoomId && "#ffffff45" }}
># {room.name}</li>

changeChatRoom = (room) => () => {
    this.props.dispatch(setCurrentChatRoom(room));
    this.setState({ activeChatRoomId: room.id });
}
```
위의 것과 아래의 것과의 차이가 있을까??


```js
<li
    key={room.id}
    onClick={() => this.changeChatRoom(room)}
    style={{ backgroundColor: room.id === this.state.activeChatRoomId && "#ffffff45" }}
># {room.name}</li>

changeChatRoom = (room) => {
    this.props.dispatch(setCurrentChatRoom(room));
    this.setState({ activeChatRoomId: room.id });
}
```

# css before
http://blog.hivelab.co.kr/%EA%B3%B5%EC%9C%A0before%EC%99%80after-%EA%B7%B8%EB%93%A4%EC%9D%98-%EC%A0%95%EC%B2%B4%EB%8A%94/

# 배열로 된 setContents
setErrors(prev => prev.concat("Type contents first"))  
요렇게 처리 하는거