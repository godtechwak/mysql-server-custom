## MySQL Custom Command Line Interface
### CLI 프롬프트
#### 서버 정보 식별
```
[mysql]
prompt="\\u@\\X(\\Z):[\\d] \\R:\\m:\\s>"
```
* `\\X` Proxy mode로 접속시, 로컬 디스크의 파일에서 서버 호스트 정보 가져와서 표시
	* 지정된 디렉토리(아래 2개)에 `port_host_map.list` 파일 준비 필요
		* `~/.mysqlrc/` 기본 디렉토리
		* `MYSQL_SCRIPTDIR` 환경 변수에 설정된 디렉토리
	* `port_host_map.list` 파일은 호스트당 1 라인씩, `port_no hostname` 쌍으로 작성 (space로 분리)
	* `port_host_map.list` 파일에서 해당 port를 찾지 못하면, `\\h`와 동일하게 작동
	* Aurora MySQL 서버의 경우, `port_host_map.list` 파일 참조 없이 자동 인식됨 (서버 쿼리 이용)
```
99901   myhost-0.com
99902   myhost-1.com
```

* `\\Y` MySQL 서버의 Replication role 표시
	* Origianl MySQL & Non-Aurora RDS
		* `SHOW SLAVE STATUS` 결과가 있으면, `Replica`로 인식
		* 결과가 없으면, `Primary`로 인식
	* Aurora MySQL 서버의 경우, `information_schema.replica_host_status` 테이블 참고하여 `Primary | Replica` 인식 

#### 컬러
```
[mysql]
prompt_color_primary=magenta
prompt_color_replica=yellow
```
* `prompt_color_primary` Primary 서버의 prompt 컬러 설정
![Primary prompt 예제](./README.screenshots/prompt-primary.png)
* `prompt_color_replica` Replica 서버의 prompt 컬러 설정
![Replica prompt 예제](./README.screenshots/prompt-replica.png)
* 설정 가능 컬러 : `black | red | green | yellow | blue | magenta | cyan | white`
