# dispatch를 하는데 원하는 상태로 동작하지 않음

```js
dispatch(setPhotoUrl(downloadURL));

case types.SET_PHOTO_URL:
    return {
        ...state,
        currentUser: { ...state.currentUser, photoURL: action.payload }
    }
    
```

위와 같이 처리되는 코드가 있는데
...state.currentUser를 했을때   
[after]currentUser에 _delegate, multifactor가 붙으면서 
currentUser에 있는 정보가 사라져 버려 제대로 갱신되지 않는 문제가 발생한다.
dispatch, store에서 사용되는 내용을 한 번 확인해 봐야겠다.

```js
console.log(`before state: ${JSON.stringify(state)}`);
console.log(`before state2: ${JSON.stringify({ ...state })}`);
console.log(`before state currentUser: ${JSON.stringify(state.currentUser)}`);
console.log(`before state currentUser2: ${JSON.stringify({ ...state.currentUser })}`);
```

위의 분해 구조를 하고 나면 _delegate, multifactor가 발생되서 위와같이 수정하면 이상한 값이 들어가게 된다.

...state는 state가 분해구조 되지만. currentUser는 _delegate와 multifactor가 생겨버린다. 