---
create date: 2024-06-25
modification date: 
tags: 
type: NomalNotes
---
# Part I
Yelp User (<u>yid: Integer</u>, Age: Integer, FirstName: String, LastName: String, Gender: String, BirthDate: Date, BirthPlace: Sting, Profile: String, Email: String)

Business (<u>bid: Integer</u>, DaysOfOperation: Integer, HoursOfOperation: TimeStamp, Street: String, State: String, ZipCode: Integer, Longitude: Number, Latitude: Number, Star: Integer, bc_id: Integer )
- Business: bc_id is foreign key of Business Category: bc_id 

Business Category (<u>bc_id: Integer</u>, name: String)

Hotel & Travel (<u>bc_id: Integer</u>)
- Hotel & Travel: bc_id is foreign key of Business Category
Restaurant (<u>bc_id: Integer</u>)
- Restaurant: bc_id is foreign key of Business Category

Scale (yid: Integer, <u>bid: Integer</u>, rate: Integer)
- Scale: yid is foreign key of Yelp User: yid 
- Scale: bid is foreign key of Business: bid 

Parking Type (bid: Integer, <u>type: String</u>)
- Parking Type: bid is foreign key of Business: bid 

Ambience Type (bid: Integer, <u>type: String</u>)
- Ambience Type: bid is foreign key of Business: bid 

Check In (<u>cid: Integer</u>, Info: String, bid: Integer) 
- Check In: bid is foreign key of Business: bid 

Business Photo (<u>pid: Integer</u>, bid: Integer, Author: String, Description: String, Location: String)
- Business Photo: bid is foreign key of Business: bid 

Personal Photo (<u>pid: Integer</u>, yid: Integer, Author: String, Description: String, Location: String)
- Personal Photo: yid is foreign key of Yelp User: yid 

Activity Wall (<u>aw_id: Integer</u>, yid: Integer)
- Activity Wall: yid is foreign key of Yelp User: yid

Review (<u>rid: Integer</u>, aw_id: Integer, bid: Integer ,content: String, Profile: String, Age: Integer, PublishDate: Date, Starts: Integer)
- Review: aw_id is foreign key of Activity Wall: aw_id 

Comment (<u>Author: String</u>, Content: String, Date: Date, rid: Integer)
- Comment: rid is foreign key of Review: rid 
Useful Vote (<u>vid: Integer</u>, yid: Integer, rid: Integer)
- Useful Vote: yid is foreign key of Yelp User: yid 

Non-Useful Vote (<u>vid: Integer</u>, yid: Integer, rid: Integer)
- Non-Useful Vote: yid is foreign key of Yelp User: yid 



---
# Part II
CREATE TABLE YelpUser (
	Yelp_id INTEGER,
	Age INTEGER,
	FName VARCHAR 2 (20),
	LName VARCHAR 2 (20),
	Gender VARCHAR 2 (20),
	BirthDate DATE,
	BirthPlace VARCHAR 2 (50),
	Profile VARCHAR 2 (200),
	Email VARCHAR 2 (20),
	PRIMARY KEY (Yelp_id)
);

CREATE TABLE Business (
	bid INTEGER,
	DaysOfOperation INTEGER,
	HoursOfOperation TimeStamp,
	Street VARCHAR 2 (20),
	State VARCHAR 2 (20),
	ZipCode INTEGER,
	Longitude NUMBER,
	Latitude NUMBER,
	Star INTEGER,
	yid INTEGER,
	bc_id INTEGER NOT NULL,
	PRIMARY KEY (bid),
	FOREIGN KEY (bc_id) REFERENCES Business_Category
	);
CREATE TABLE Business_Category (
	bc_id INTEGER,
	Name CHAR (20),
	PRIMARY KEY (bc_id)
);
CREATE TABLE Hotel & Travel (
	bc_id INTEGER,
	PRIMARY KEY (bc_id),
	FOREIGN KEY (bc_id) REFERENCES Business_Category
);
CREATE TABLE Restaurant (
	Bc_id INTEGER,
	PRIMARY KEY (bc_id),
	FOREIGN KEY (bc_id) REFERENCES Business_Category
);

CREATE TABLE Scale (
	yid INTEGER NOT NULL,
	bid INTEGER,
	Rate INTEGER,
	PRIMARY KEY (bid),
	FOREIGN KEY (yid) REFERENCES YelpUser,
	FOREIGN KEY (bid) REFERENCES Business
);

CREATE TABLE Parking_Type (
	Type CHAR(20),
	bid INTEGER NOT NULL,
	PRIMARY KEY (Type),
	FOREIGN KEY (bid) REFERENCES Business
);

CREATE TABLE Ambience_Type (
	Type CHAR (20),
	bid INTEGER NOT NULL,
	PRIMARY KEY (Type),
	FOREIGN KEY (bid) REFERENCES Business
);

CREATE TABLE Check_In (
	cid INTEGER,
	info CHAR(100),
	bid INTEGER NOT NULL,
	PRIMARY KEY (cid),
	FOREIGN KEY (bid) REFERENCES Business
);

CREATE TABLE Business_Photo (
	pid INTEGER,
	Author CHAR (50),
	Description VARCHAR 2 (200),
	Location CHAR (50),
	bid INTEGER NOT NULL,
	PRIMARY KEY (pid),
	FOREIGN KEY (bid) REFERENCES Business
);

CREATE TABLE Personal_Photo (
	Pid INTEGER,
	Author VARCHAR 2 (50),
	Description VARCHAR 2 (200),
	Location VARCHAR 2 (50),
	yid INTEGER NOT NULL,
	PRIMARY KEY (pid),
	FOREIGN KEY (yid) REFERENCES YelpUser
);

CREATE TABLE Activity_Wall (
	aw_id INTEGER,
	yid INTEGER NOT NULL,
	PRIMARY KEY (aw_id),
	FOREIGN KEY (yid) REFERENCES YelpUser
);

CREATE TABLE Review (
	rid INTEGER,
	Content , VARCHAR 2 (200),
	Age INTEGER,
	PublishDate DATE,
	Stars INTEGER,
	aw_id INTEGER NOT NULL,
	PRIMARY KEY (rid),
	FOREIGN KEY (aw_id) REFERENCES Activity_Wall
);

CREATE TABLE Comment (
	Author CHAR (20),
	Content VARCHAR 2 (100),
	Date DATE,
	rid INTEGER NOT NULL,
	PRIMARY KEY (Author),
	FOREIGN KEY (rid) REFERENCES Review
);

CREATE TABLE Useful_Vote (
	vid INTEGER,
	yid INTEGER NOT NULL,
	PRIMARY KEY (vid),
	FOREIGN KEY (yid) REFERENCES YelpUser
);
CREATE TABLE Non-Useful_Vote (
	vid INTEGER,
	yid INTEGER NOT NULL,
	PRIMARY KEY (vid),
	FOREIGN KEY (yid) REFERENCES YelpUser
);