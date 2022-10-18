# wehelp-week_5

**要求⼆：建立資料庫和資料表**

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

**要求三：SQL CRUD**

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

*3. 取得所有在 member 資料表中的會員資料，並按照 time 欄位，由近到遠排序。*

```
SELECT * FROM member ORDER BY time DESC;
```
![image](https://user-images.githubusercontent.com/111167537/196401591-2ca0a253-99cb-48bb-9ac1-13bae3485ba9.png)

*4. 取得 member 資料表中第 2 ~ 4 共三筆資料，並按照 time 欄位，由近到遠排序。*
```
SELECT * FROM member ORDER BY time DESC LIMIT 1,3;
```
![image](https://user-images.githubusercontent.com/111167537/196402873-e57775b4-e2d7-45bf-97bc-721951f4da96.png)

*5. 取得欄位 username 是 test 的會員資料*
```
SELECT * FROM member WHERE username = 'test';
```
![image](https://user-images.githubusercontent.com/111167537/196403454-4994ad1c-b219-488b-8d3f-bb5ca639e789.png)

*6. 取得欄位 username 是 test、且欄位 password 也是 test 的資料*
```
SELECT * FROM member WHERE username = 'test' && password = 'test';
```
![image](https://user-images.githubusercontent.com/111167537/196403454-4994ad1c-b219-488b-8d3f-bb5ca639e789.png)

*7. 更新欄位 username 是 test 的會員資料，將資料中的 name 欄位改成 test2。*
```
UPDATE member
SET name = 'test2'
WHERE username = 'test';
```
![image](https://user-images.githubusercontent.com/111167537/196404812-2b463903-d92f-4e18-9e41-814d76c3f030.png)
![image](https://user-images.githubusercontent.com/111167537/196404703-ee43b500-38df-4872-8142-77adfe32921a.png)

**要求四：SQL Aggregate Functions**

*1. 查詢有幾位會員。*

```
SELECT COUNT(*) AS Total Of Member FROM member;
```
![image](https://user-images.githubusercontent.com/111167537/196405760-d54f6de7-fdf3-4b44-aa1b-c6d4ede41919.png)


*2. follower_count的總和。*

```
SELECT SUM(follower_count) AS Sum_Of_Follower From member;
```
![image](https://user-images.githubusercontent.com/111167537/196406916-e7dc6422-3d23-4729-9fa3-faa1a59747bf.png)

*3. follower_count的平均數。*

```
SELECT AVG(follower_count) AS AvgCount From member;
```
![image](https://user-images.githubusercontent.com/111167537/196407935-50867268-ef42-4c08-ba2d-f4a2bc0c4721.png)


**要求五：SQL JOIN (Optional)**

*1. 建立新資料表(message)*
```
CREATE TABLE message(id BIGINT PRIMARY KEY AUTO_INCREMENT,
      member_id BIGINT NOT NULL,
      content VARCHAR(255) NOT NULL,
      like_count INT UNSIGNED DEFAULT 0 NOT NULL,
      time DATETIME DEFAULT CURRENT_TIMESTAMP NOT NULL,
      FOREIGN KEY (member_id) REFERENCES member(id));
```

![image](https://user-images.githubusercontent.com/111167537/196413185-1ba77a80-a11d-4d20-b6ac-21244f5fe347.png)
![image](https://user-images.githubusercontent.com/111167537/196413791-9e92967d-27c5-480d-8006-d89060df5741.png)

*2. 新增資料在message資料庫*

```
insert into message (member_id, content, like_count)
values ('1','Good Morning',19),
       ('2','You are wonderful.','20'),
       ('3','Good afternoon', '15'),
       ('4','Lucky', '180'),
       ('5','Nice', '22'),
       ('6','Love you all', '620'),
       ('7','Amazing', '80'),
       ('3','Sweet Home',50),
       ('2','Hello World','20'),
       ('3','Cool', '430'),
       ('4','Bye', '10'),
       ('3','Good', '120'),
       ('6','I appreciate you.','420'),
       ('7','See you', '8');
```
![image](https://user-images.githubusercontent.com/111167537/196434399-db7dcf53-4a42-44d2-b147-51baf08b9d01.png)

*3. 取得所有留⾔，結果須包含留⾔者會員的姓名*
```
SELECT info.username, mess.content FROM member info
	LEFT JOIN message mess ON info.id = mess.member_id;
```
![image](https://user-images.githubusercontent.com/111167537/196434787-8b4698bb-9975-46d7-a312-1523df06e964.png)

*4. 先增加幾項test會員資料，取得 member 資料表中欄位 username 是 test 的所有留⾔，資料中須包含留⾔者會員的姓名。*
```
INSERT INTO message (member_id, content, like_count)
values ('1','hahaha',230),
       ('1','off-topic comment','88'),
       ('1','You look good', '125'),
       ('1','Yoyoyo', '415');

SELECT info.username, mess.content FROM member info
LEFT JOIN message mess ON info.id = mess.member_id
WHERE info.username = 'test';
```
![image](https://user-images.githubusercontent.com/111167537/196445503-734473b7-1105-452f-8dd8-40460e4f6067.png)
![image](https://user-images.githubusercontent.com/111167537/196445981-30cd3a29-8e15-4011-94a0-c98f8a2ec99a.png)

*4. 取得 member 資料表中欄位 username 是 test 的所有留⾔平均按讚數。*
```
SELECT info.username, AVG(mess.like_count) AS LikeAvg FROM member info
LEFT JOIN message mess ON info.id = mess.member_id
WHERE info.username = 'test'
Group by info.username;
```
![image](https://user-images.githubusercontent.com/111167537/196469417-357a116b-948a-4608-aca4-d6b24b6818f7.png)


