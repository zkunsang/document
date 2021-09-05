npm install react-hook-form

Link를 사용하는 위치가 다른 컴포넌트에서 
import {Link} from 'react-router-dom';
<Link>

```js
import React from 'react'
import "./RegisterPage.css"
import { Link } from 'react-router-dom';

function RegisterPage() {
    return (
        <div className="auth-wrapper">
            <div style={{ textAlign: 'center' }}>
                <h3>Register</h3>
            </div>

            <form>
                <label>Email</label>
                <input name="email" type="email" defaultValue="test" />
                <label>Name</label>
                <input name="name" defaultValue="test" />
                <label>Password</label>
                <input name="password" type="password" defaultValue="test" />
                <label>Password Confirm</label>
                <input name="passwordConfirm" type="password" />
                <input type="submit" />
                <Link style={{ color: 'gray', textDecoration: 'none' }} to="/login">이미 아이디가 있다면</Link>
            </form>

        </div>
    )
}

export default RegisterPage

```

# 유효성 체크
## 설치
npm install react-hook-form --save  
form의 유효성을 체크해 준다.

강좌에는 ref= {register...}이렇게 하지만
```js
{...register("email", { required: true, maxLength: 10 })}
```
## useForm({mode: onChange})
onChange로 하면 변화 될때마다 검사를 하게 된다  
빼면 submit이 발생될 때만 실행
```
const { register, watch, formState: { errors } } = useForm({ mode: "onChange" });
```

## useRef를 왜 사용하는가

쿼리 셀렉터
element by Id와 같은 domSelector를 사용하는데
리액트에서는 ref라는 것을 사용한다.

1. 엘리먼트 크기를 가져와야 할 때
2. 스크롤바 위치를 가져와야 할 때
3. 엘리먼트에 포커스를 설정 해줘야 할 때
``` js
const password = useRef();
password.current = watch("password");
```

```
[value, setValue] = useState()
const handleChange = () => {
    setValue()
}
onChange={handlChange}
```