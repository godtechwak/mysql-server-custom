## 압축 해제
```
tar xvf mysql_custom_cmd_mac.tar.gz
```

## 기존 mysql 바이너리 파일 이름 변경
```
sudo cp /opt/homebrew/opt/mysql-client/bin/mysql /opt/homebrew/opt/mysql-client/bin/mysql_origin
```

## 압축 해제한 바이너리 파일을 실행 경로로 이동
```
sudo mv ./mysql /opt/homebrew/opt/mysql-client/bin/
```
