# wehelp-week_5

*要求⼆：建立資料庫和資料表*

```
CREATE DATABASE website;
```

![image](https://user-images.githubusercontent.com/111167537/196379800-3f7d3468-32fb-4ca9-ae74-e60fdfd68fb7.png)

```
   CREATE TABLE member(id BIGINT PRIMARY KEY AUTO_INCREMENT, 
   name VARCHAR(255) NOT NULL, username VARCHAR(255) NOT NULL, 
   password VARCHAR(255) NOT NULL, follower_count INT UNSIGNED DEFAULT 0 NOT NULL, 
   time DATETIME DEFAULT CURRENT_TIMESTAMP NOT NULL);
```
![image](https://user-images.githubusercontent.com/111167537/196380163-a5d661fc-3128-45d4-a448-1df16657aa9f.png)
![image](https://user-images.githubusercontent.com/111167537/196380182-9617f5c1-cf14-4c43-9f23-232e1c8c23a2.png)

*要求三：SQL CRUD*

*1. 新增資料*

```
INSERT INTO member (name, username, password, follower_count)
VALUES ('tesla' ,'test','test',10),
      ('ben', 'superben','benben','20'),
      ('mary','beautifulmary','marymary', '150'),
      ('may','may123','maymay', '150'),
	  ('tree','treegun','guntree', '220'),
      ('orange','vitaminC','orange123', '320'),
      ('pie','applepie','pi3.14159', '80');
```
![image](https://user-images.githubusercontent.com/111167537/196380539-6c5525d7-7e3f-45a8-b91c-431957f2f456.png)
![image](https://user-images.githubusercontent.com/111167537/196380562-589eb47a-1843-49ff-9621-07c333218b89.png)

*2. 取得所有在 member 資料表中的會員資料。*
```
SELECT * FROM member;
```
![image](https://user-images.githubusercontent.com/111167537/196385198-78ff85a5-2fa6-4163-bdcc-560c0234a129.png)
