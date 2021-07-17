# (dump)덤프하기

mongodump --out ~/mongo_backup --db story  
--out: out폴더
--db: 원하는 디비

# (import)임포트하기

mongorestore --db [db명] [파일 폴더 위치]
mongorestore --db quest ~/mongo_backup/quest/
--db: 원하는 디비


