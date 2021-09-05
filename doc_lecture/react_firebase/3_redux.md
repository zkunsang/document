# John Ahn redux 강좌
## 설치
npm install redux react-redux redux-promise redux-thunk --save

```js
import { Provider } from 'react-redux';
import { createStore, applyMiddleware } from 'react';
import promiseMiddleware from 'redux-promise';
import ReduxThunk from 'redux-thunk';
import Reducer from './redux/reducers';
// redux를 사용하기 위해서
// Provider로 App을 감싸주고
// 미들 웨어를 저장해준다.

const createStoreWithMiddleware = applyMiddleware(promiseMiddleware, ReduxThunk)(createStore);

ReactDOM.render(
  <React.StrictMode>
    <Provider store={createStoreWithMiddleware(Reducer, window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__())}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);

```