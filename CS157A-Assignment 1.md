---
create date: 2024-09-11
modification date: 
tags:
  - "#fleeting"
type: NomalNotes
---
```mysql
create database cs157a_hw1;
use cs157a_hw1;
CREATE TABLE IF NOT EXISTS Suppliers(sNumber INT, sName VARCHAR(20),sStatus INT,sCity VARCHAR(15), PRIMARY KEY(sNumber));
CREATE TABLE IF NOT EXISTS Parts(pNumber INT, pName VARCHAR(20),color VARCHAR(10),weight INT,pCity VARCHAR(15), PRIMARY KEY(pNumber));
CREATE TABLE IF NOT EXISTS Projects(jNumber INT,jName VARCHAR(20), jCity VARCHAR(15), PRIMARY KEY(jNumber)); 
CREATE TABLE IF NOT EXISTS SPJ(sNumber INT,pNumber INT,jNumber INT,quality INT,PRIMARY KEY(sNumber,pNumber,jNumber));
desc Suppliers;
desc Parts;
desc Projects;
desc SPJ;

INSERT INTO Suppliers(sNumber,sName,sStatus,sCity) VALUES(1,"Smith",20,"London");
INSERT INTO Suppliers(sNumber,sName,sStatus,sCity) VALUES(2,"Jones",10,"Paris");
INSERT INTO Suppliers(sNumber,sName,sStatus,sCity) VALUES(3,"Blake",30,"Paris");
INSERT INTO Suppliers(sNumber,sName,sStatus,sCity) VALUES(4,"Clark",20,"London");
INSERT INTO Suppliers(sNumber,sName,sStatus,sCity) VALUES(5,"Adams",30,"Athens");

INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(1,"Nut","Red",12,"London");
INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(2,"Bolt","Green",17,"Paris");
INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(3,"Screw","Blue",17,"Rome");
INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(4,"Screw","Red",14,"London");
INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(5,"Cam","Blue",12,"Paris");
INSERT INTO Parts(pNumber,pName,color,weight,pCity) VALUES(6,"Cog","Red",19,"London");

INSERT INTO Projects(jNumber,jName,jCity) VALUES(1,"Sorter","Paris");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(2,"Punch","Rome");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(3,"Reader","Athens");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(4,"Console","Athens");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(5,"Collator","London");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(6,"Terminal","Oslo");
INSERT INTO Projects(jNumber,jName,jCity) VALUES(7,"Tape","London");

INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(1,1,1,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(1,1,4,700);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,1,400);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,2,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,3,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,4,500);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,5,600);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,6,400);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,3,7,800);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(2,5,2,100);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(3,3,1,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(3,4,2,500);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(4,6,3,300);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(4,6,7,300);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,2,2,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,2,4,100);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,5,5,500);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,5,7,100);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,6,2,200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,1,4,1000);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,3,4,1200);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,4,4,800);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,5,4,400);
INSERT INTO SPJ(sNumber,pNumber,jNumber,quality) VALUES(5,6,4,500);

```