# firebase 버젼 문제
`강의를 작성하게 되면 항상 버전 문제를 생각하자!`

import firebase from 'firebase/compat/app';  
import 'firebase/compat/auth';  
import 'firebase/compat/database';  
import 'firebase/compat/storage';  

# photoUrl만들기
# gravatar + md5
`http://gravatar.com/avatar/${md5(createdUser.user.email)}?d=identicon`