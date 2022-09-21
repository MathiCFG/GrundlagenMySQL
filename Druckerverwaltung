Drop database if exists foi11_druckerverwaltung;
CREATE DATABASE foi11_druckerverwaltung;

use foi11_druckerverwaltung;

create table Raum(
ID int primary key,
Bezeichnung varchar(50),
Ansprechpartner varchar(50)
);


Create table Verbrauchsmaterial(
id int primary key,
Type varchar(50),
Farbe varchar(50)
);

create table Druckermodell(
id int primary key,
Bezeichnung varchar(50),
Hersteller varchar(50),
Typ varchar(50),
Rebuild varchar(50)
);

create table Druckermodell_Verbrauchsmaterial(
Druckermodell int,
Verbrauchsmaterial int,
Primary key (Druckermodell,Verbrauchsmaterial),
Foreign key (Druckermodell) references Druckermodell(id),
Foreign key (Verbrauchsmaterial) references Verbrauchsmaterial(id)
);

create table Druckerexemplar(
Raum int,
Druckermodell int,
Priorität varchar(50),
Beschaffungsdatum date,
Primary key (Raum,Druckermodell),
foreign key (Raum) references Raum(id),
foreign key (Druckermodell) references Druckermodell(id)
);

create table Anforderungen(
ID int primary key,
Druckermodell int,
Raum int,
Verbrauchsmaterial int,
Anzahl int,
Datum date,
Hinweise varchar(50),
Foreign key (Verbrauchsmaterial) references Verbrauchsmaterial(id),
Foreign key (Druckermodell,Raum) references Druckerexemplar (Druckermodell,Raum)
);


insert into Raum(ID,Bezeichnung,Ansprechpartner) values
(10,'Verwaltung','Herr Schneider'),
(20,'Seminarraum','Frau Kramer'),
(30,'Kantine','Herr Auster'),
(40,'IT-Labor','Herr Schumacher'),
(50,'Büro','Frau  Jellen');


insert into Verbrauchsmaterial(id,Type,Farbe) values
(1,'Toner','schwarz'),
(2,'Toner','cyan'),
(3,'Tinte','color'),
(4,'Bildtrommel','yellow'),
(5,'toner','magenta');


insert into Druckermodell(id,Bezeichnung,Typ,Hersteller,Rebuild) values
(100,'BROTHER HL 2150','Laserdrucker','Brother','ja'),
(200,'BROTHER HL 2170','Laserdrucker','Brother','ja'),
(300,'CANON Fax-l 200 (fx 3)','Faxgerät','Canon','nein'),
(400,'OKI C 810','Laserdrucker(Farbe)','OKI','ja'),
(500,'BROTHER HL 2250','Farbdrucker','Brother','ja');


insert into Druckermodell_Verbrauchsmaterial(Druckermodell,Verbrauchsmaterial) values
(100,1),
(500,2),
(500,3),
(400,4);


insert into Druckerexemplar(Raum,Druckermodell,Priorität,Beschaffungsdatum) values
(10,500,'hoch','2016-05-01'),
(30,100,'hoch','2012-06-10'),
(40,300,'hoch','2012-06-10'),
(20,200,'hoch','2012-06-10');


insert into Anforderungen(ID,Raum,Druckermodell,Verbrauchsmaterial,Anzahl,Datum,Hinweise) values
(1,10,500,1,1,'2005-10-10',""),
(2,30,100,4,4,'2005-10-10',""),
(3,20,200,5,3,'2005-10-10',"");

#------
set sql_safe_updates = 0;
Alter table Druckerexemplar drop foreign key druckerexemplar_ibfk_1;
Alter table Anforderungen drop foreign key anforderungen_ibfk_2;
Alter table Raum modify id varchar(50);
Alter table Druckerexemplar modify Raum varchar(50);
Alter table Anforderungen modify Raum varchar(50);
#select * from anforderung where Raum like ("1%");


alter table Druckerexemplar add foreign key (Raum) references Raum(Id) on update Cascade on Delete Cascade;
alter table Druckerexemplar add foreign key (Druckermodell) references Druckermodell(id) on update Cascade on Delete Cascade;

alter table Anforderungen add Foreign key (Verbrauchsmaterial) references Verbrauchsmaterial(id) on update Cascade on Delete Cascade;
alter table Anforderungen add Foreign key (Druckermodell,Raum) references Druckerexemplar (Druckermodell,Raum) on update Cascade on Delete Cascade;

Update Raum set ID = CONCAT("B",ID);

Delete from Raum where ID = "B20";

Select * from Druckerexemplar;
Select * from Anforderungen;
