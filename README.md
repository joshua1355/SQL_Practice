# SQL_Practice

#Create Table
'''
CREATE TABLE STADIUM (
STADIUM_ID    CHAR(3) NOT NULL,
STADIUM_NAME  VARCHAR2(40) NOT NULL,
HOMETEAM_ID   CHAR(3), /*char 캐릭터 입력*/
SEAT_COUNT    NUMBER,/*number */
ADDRESS       VARCHAR2(60), /*varchart string data type*/
DDD           VARCHAR2(3),
TEL           VARCHAR2(10),
CONSTRAINT STADIUM_PK PRIMARY KEY (STADIUM_ID) /*primary key 주민번호 처럼 제일 중유한 번호 */
);

CREATE TABLE TEAM ( 
TEAM_ID CHAR(3) NOT NULL, 
REGION_NAME VARCHAR2(8) NOT NULL,
TEAM_NAME VARCHAR2(40) NOT NULL, 
E_TEAM_NAME VARCHAR2(50), 
ORIG_YYYY CHAR(4), 
STADIUM_ID CHAR(3) NOT NULL,
ZIP_CODE1 CHAR(3), 
ZIP_CODE2 CHAR(3), 
ADDRESS VARCHAR2(80), 
DDD VARCHAR2(3),
TEL VARCHAR2(10), 
FAX VARCHAR2(10), 
HOMEPAGE VARCHAR2(50), 
OWNER VARCHAR2(10), 
CONSTRAINT TEAM_PK PRIMARY KEY (TEAM_ID),/*primary key */
CONSTRAINT TEAM_FK FOREIGN KEY (STADIUM_ID) /*references */REFERENCES STADIUM(STADIUM_ID) );

CREATE TABLE PLAYER ( 
PLAYER_ID CHAR(7) NOT NULL, 
PLAYER_NAME VARCHAR2(20) NOT NULL, 
TEAM_ID CHAR(3) NOT NULL, 
E_PLAYER_NAME VARCHAR2(40),
NICKNAME VARCHAR2(30), 
JOIN_YYYY CHAR(4), 
POSITION VARCHAR2(10), 
BACK_NO NUMBER(2),
NATION VARCHAR2(20), 
BIRTH_DATE DATE,
SOLAR CHAR(1), 
HEIGHT NUMBER(3), 
WEIGHT NUMBER(3), 
CONSTRAINT PLAYER_PK PRIMARY KEY (PLAYER_ID), 
CONSTRAINT PLAYER_FK FOREIGN KEY (TEAM_ID) REFERENCES TEAM(TEAM_ID) );

ALTER TABLE Stadium ADD /*add하나 테이블 더만들기*/
Test1 VARCHAR2(10) not null; /*not null 똑같은 번호나 이름 방지 하기 위해서*/
ALTER TABLE Stadium DROP COLUMN Test1; 
ALTER TABLE Stadium rename COLUMN Test1 to test2; /*rename 이름 바꾸기*/
ALTER TABLE Stadium MODIFY (Test1 VARCHAR2(10) not null);

drop table Player2; /*drop테이블 전채삭제*/
rename player to player2; /*rename 이름 바꾸기*/

ALTER TABLE PLAYER DROP CONSTRAINT PLAYER_FK;

ALTER TABLE PLAYER ADD CONSTRAINT PLAYER_FK2 FOREIGN KEY (TEAM_ID) 
REFERENCES TEAM(TEAM_ID);

select * from Stadium;

'''



