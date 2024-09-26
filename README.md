# Domestic-violence-cases-against-women-in-Nigeria_Sql_project
![closedmouth](https://github.com/bellaudeh/Domestic-violence-cases-against-women-in-Nigeria_Sql_project/blob/main/closed%20mouth.png)

## Overview
This project focuses on the analysis of domestic violence against womwnt in Nigeria using primary data collected by the data analyst from womenn affected by domestic violence. The dataset covers information on victim demographics, reported cases and support gotten by the victim. The goal behind this analysis is to better understand the scope of domestic violence in Nigeria and its impact on the lives of women from different background.

## Data Sources:
**Domestic violence incident table:** Contains information about reported incident, loaction, age, support-service, type of violence and relationship with perpetrator.

**Victim demographic table:** Captures data on the personal demographics of the women involved, such as age group, marital status, education level, and occupation.

## Objectives
The primary objective of this project is to perform an SQL analysis to: <br/>
1.Understand the support system gotten by these women after a violent occurence.<br/>
2.Understand the relationship between victim demographics (e.g., age, marital status, education) and the frequency or severity of domestic violence incidents.<br/>
3.Present insights that can support organizations and policymakers in designing targeted interventions and providing support to affected women.<br/>
4. Raise awareness about domestic violence issues in Nigeria.

## Schema
**Domestic Violence Table**
```sql
CREATE TABLE DOMESTIC_VIOLENCE
(
  `ID` int,
  `date`  date,
  `location` varchar (100),
  `age` int,
  `marital_status` varchar(100),
  `perpetrator_relationship` varchar(300),
  `violence` varchar (300),
  `severity` varchar (500),
  `reported` bit,
  `legal_action` varchar (300),
  `outcome` varchar (300),
  `support_service` varchar (300)
);
insert into domestic_violence 
(`id`,`date`,`location`,`age`,`marital_status`,`perpetrator_relationship`,`violence`,`severity`,`reported`,`legal_action`,`outcome`,`support_service`) values
('1','2018-10-09','abuja',32,'married','husband','physical','severe','1','none','none','family'),
(2,'2022-06-11','lagos',24,'single','boyfriend','psychological','minor',0,'none','none','none'),
(3,'2024-01-22','delta',20,'single','boyfriend','physical','minor',0,'none','none','friends'),
(4,'2021-06-15','enugu',30,'widow','family','psychological','severe',1,'court-case','none','religious-counseling'),
(5,'2023-07-30','abuja',45,'single','family','psycological','minor', 0, 'none','none','none'),
(6,'2024-09-16','nasarawa',25,'married','husband','physical','severe',0,'none','none','religious-counseling'),
(7,'2019-10-30','kogi',25,'single','boyfriend','physical','severe',1,'none','none','friend'),
(8,'2019-10-15','abuja',30,'married','husband','physical','severe',1,'court-case','divorce','counseling'),
(9,'2018-10-15','jos',50,'single','family','psycological','severe',0,'none','none','religious-counseling'),
(10,'2020-11-05','abuja',31,'married','husband','physical','minor',0,'none','none','family'),
(11,'2018-02-19','enugu',40,'single','family','psychological','severe',0,'none','none','none'),
(12,'2020-12-14','benue',31,'married','stranger','physical','severe',1,'arrested','convicted','counseling'),
(13,'2021-07-17','abuja',19,'married','family','physical','severe',0,'none','none','none'),
(14,'2022-05-18','kaduna',18,'married','husband','sexual','severe',1,'court-case','in-process','family'),
(15,'2021-02-16','abuja', 30,'married','husband','psychological','severe',1,'none','none','none'),
(16,'2023-07-23','nasarawa',22,'single','stranger','sexual','severe',1,'arrested','convicted','family'),
(17,'2022-04-25','abuja',19,'single','family','sexual','severe',1,'arrested','none','religious-counseling'),
(18,'2020-09-30','delta',50,'single','family','psychological','minor',0,'none','none','none'), 
(19,'2019-04-23','abuja',30,'married','husband','physical','severe',1,'court-case','divorce','religiou-counseling'),
(20,'2020-05-22','lagos',24,'single','boyfriend','psychological','minor',0,'none','none','friends');
```
**Victim Demographic Table**
```sql
create table victim_demographics( 
  `ID` int primary key,
  `victim_name` text (500),
  `age_group` text (500),
  `marital_status` text (500),
  `educational_level` text (500),
  `employment_status` text (500),
  `income_level` text (500),
  `location` text (500)
);
insert into victim_demographics (`ID`,`victim_name`,`age_group`,`marital_status`,`educational_level`,`employment_status`,
									`income_level`,`location`)
values(1,'dayo','30-35','married','university','employed','low','abuja'),
(2,'seun','20-25','single','university','employed', 'low','lagos'),
(3,'mara','20-25','single','university','unemployed','very low','delta'),
(4,'judith','30-35','widow','secondary','umemployed','very low','enugu'),
(5,'jummai','40-45','single','university','employed','high','abuja'),
(6,'aisha','20-25','married','secondary','petty_trader','low','nasarawa'),
(7,'josephine','20-25','single','university','unemployed','very low','kogi'),
(8,'cynthia','30-35','married','university', 'employed','high','abuja'),
(9,'faith','50-55','single','university','employed','very high','jos'),
(10,'mary','30-31','married','secondary','entreprenuer','high','abuja'),
(11,'ijeoma','40-45','single','university','employed','very high','enugu'),
(12,'dera','30-35','married','university','employed', 'high','benue'),
(13,'amina','15-20','married','primary','unemployed','very low','abuja'),
(14,'joyce','18-20','married','primary','unemployed','low','kaduna'),
(15,'fummi','30-35','married','university', 'employed','high','abuja'),
(16,'amina','20-25','single','university','unemployed','low','nasarawa'),
(17,'jessica','15-20','single','secondary','unemployed','low','abuja'),
(18,'bella','45-50','single','university','employed','very high','delta'),
(19,'tania','30-35','married','university','entreprenuer','very high','abuja'),
(20,'shade','25-30','single','university','employed','high','lagos');
```
##Problems and solution based on the dataset
**1. what are the most common types of violence?**
```sql
select violence,
	count(*) as violence_count from domestic_violence
		group by violence;
```
