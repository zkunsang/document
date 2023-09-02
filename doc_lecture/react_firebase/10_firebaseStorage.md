# firebase STorage

# useRef
특정한 DOM을 선택하기 위해 사용

```jsx
<input style={{ display: 'none' }} type="file" />
```

diplay를 none로 해주고

```jsx
const inputOpenImageRef = useRef();
<input style={{ display: 'none' }} type="file" />
```

옵션을 통해서

# mime-types
파일이름을 통해서 metaddata('/data')를 가져와 줌
npm install mime-types --save