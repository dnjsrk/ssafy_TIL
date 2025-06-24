# Mysql 프로시저

## 1. 저장 프로시저란?

### 저장 프로시저란?

- 일련의 SQL 문장을 선언해서 MYSQL에 저장하고, 해당 SQL문을 함수처럼 사용하는 것
- 만들어 두기만 하면 함수처럼 호출하여 편하게 사용할 수 있다.

### 왜 저장 프로시저를 사용하는가?

- 저장 프로시저는 사용자들에게 데이터에 대한 제한적인 접근을 허용케하는 전통적인 수단
- 사용자들은 SELECT, INSERT, UPDATE, DELEETE 같은 문장을 직접 실행할 수 있는 권한을 가져서는 안됨
- 성능을 향상시키기 위함.
- 실행계획이 캐쉬에 저장
- 복잡한 문장을 저장 프로시저에 넣을 경우, 네트워크를 통해 전달되는 데이터 소통량이 상당히 감소하게 되며, 해당 프로시저가 자주 실행될 수록 성능향상 효과가 증대된다
- 성능이 월등한 출력 매개변수의 사용이 가능

## 2. 과제 코드

```
CREATE TABLE ssafy_user (
    id VARCHAR(45),
    name VARCHAR(45),
    campus VARCHAR(45),
    class VARCHAR(45),
    gi VARCHAR(45)
);
DELIMITER $$

CREATE PROCEDURE `proc_user_insert` (
	user_id VARCHAR(20),
    user_name VARCHAR(20),
    user_campus VARCHAR(20),
    user_class VARCHAR(20),
    user_gi VARCHAR(20)
)
BEGIN
	INSERT INTO ssafy_user(id, name, campus, class, gi)
		VALUES(user_id, user_name, user_campus, user_class, user_gi);
END$$

DELIMITER ;

CALL proc_user_insert('ssafy', '변가원', '서울', '9반', '13기');

SELECT * FROM ssafy_user;
```
