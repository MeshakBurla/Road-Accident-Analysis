# Road-Accidents-Analysis
 
# Project overview

## Title: Road Accidents Analysis

## Level: Beginner

## Database: Road Accident

# Excel Dashboard:

https://1drv.ms/x/c/d45e15bd8bed1566/ETYegFDmaolPmbar7Ixc0K4BVrOXDSIwV0PRjFadU0UABQ?e=SKve0r

# Power bi dashboard:

https://app.powerbi.com/reportEmbed?reportId=dc33f87a-5489-4792-958fec297e7059ef&autoAuth=true&ctid=51302999-bb18-4fba-98bf-3a7ab3f07f13 

# Objectives:

1. Identify Causes and Risk Factors – Analyze accident data to determine primary causes such as speeding, drunk driving, weather conditions, or infrastructure issues.
   
2. Improve Road Safety Measures – Develop strategies like better road designs, traffic regulations, and awareness campaigns to reduce accidents.
   
3. Enhance Emergency Response – Assess accident patterns to improve emergency medical services and response times for accident victims.
   
4.Support Policy and Legislation – Provide data-driven insights for implementing or refining traffic laws, such as seatbelt enforcement and speed limits.

5.Reduce Economic and Social Impact – Minimize financial losses from accidents (medical costs, property damage) and reduce emotional distress by preventing injuries and fatalities.

# Project Structure:

## 1.Database Setup

**Database Creation**: The project starts by creating named `Road Accident`.

**Table Creation**: 
A table named `[Road Accidents]` is created to store the players data. The table structure includes
Columns for Accident_Index, Accident_Date, Day_of_Week, Junction_Control, Junction_Detail, Accident_Severity, Latitude, Light_Conditions, Local_Authority_District, Carriageway_Hazards, Longitude, Number_of_Casualties, 
Number_of_Vehicles, Police_Force , Road_Surface_Conditions,Road_Type ,Speed_Limit,Time,Urban_or_Rural_Area,
Weather_Conditions , Vehicle_Type.

```sql
CREATE TABLE [Road_Accidents] (
Accident_Index NVARCHAR(80),
 Accident_Date DATE, 
Day_of_Week VARCHAR(20), 
Junction_Control VARCHAR(50), 
Junction_Detail VARCHAR(100), 
Accident_Severity INT, 
Latitude DECIMAL(9,6), 
Light_Conditions VARCHAR(50), 
Local_Authority_District VARCHAR(100),
 Carriageway_Hazards VARCHAR(100), 
Longitude DECIMAL(9,6), 
Number_of_Casualties INT, 
Number_of_Vehicles INT,
 Police_Force INT, 
Road_Surface_Conditions VARCHAR(50),
 Road_Type VARCHAR(50),
 Speed_Limit INT, 
Time TIME, 
Urban_or_Rural_Area VARCHAR(50),
 Weather_Conditions VARCHAR(50), 
Vehicle_Type VARCHAR(100) );

SELECT * FROM ROAD ACCIDENTS; 
```
### CY_Casualties of Road Accidents

```sql
SELECT SUM(number_of_casualties) as CY_Casualties 
FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date)= '2022';
```

Link: ![Image](https://github.com/user-attachments/assets/3d5ae10f-2427-4fdc-8c39-7629c690cfcd) 

### CY_Accident of Road Accidents

```sql
SELECT SUM(number_of_casualties) as CY_Accident 
FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date)= '2022';
```
Link: ![Image](https://github.com/user-attachments/assets/01a25d97-bcd7-4cd1-8649-b7f3191b1ed7) 

### CY_Casualties of Road Accidents of Road Accidents

```sql
SELECT SUM(number_of_casualties) AS CY_Slight_Casualties 
FROM [ROAD ACCIDENTS] 
WHERE accident_severity = 'Slight' AND YEAR(accident_date) = '2022';
```
![Image](https://github.com/user-attachments/assets/1df45575-c4b8-4684-ba84-b7736b05b616)

### CY_Fatal_Casualties of Road Accidents

```sql 
SELECT SUM(number_of_casualties) AS CY_Fatal_Casualties 
FROM [ROAD ACCIDENTS] 
WHERE accident_severity = 'Serious' AND YEAR(accident_date) = '2022';
```
![Image](https://github.com/user-attachments/assets/0c980466-63e5-4d96-8de5-61ce4bd20788) 

###  CY_Casulaties  of Road Accidents

```sql
SELECT  
    CASE 
 	    WHEN vehicle_type IN ('Agricultural vehical') THEN 'Agricultural' 
 	 	WHEN vehicle_type IN ('Car','Taxi/Private hire car') THEN 'Cars' 
 	 	WHEN vehicle_type IN ('Motorcycle 125cc and under ','Motorcycle 50cc  and under', 'Motorcycle 125cc and up to 500cc','Motorcycle over 500cc','Pedal cycle') THEN 'Bike' 
  WHEN vehicle_type IN('Bus or coach (17 or more pass seats)','Minibus(8-16 passenger seats') THEN 'Bus' 
 	 	WHEN vehicle_type IN('Goods 7.5 tonnes mgw and over','Goods over 3.5t. and under 7.5t','Van/Goods 3.5 tonnes mgw or under') THEN 'Van' 
 	 	ELSE 'Other' 
    END AS vehicle_group, 
 	 SUM(number_of_casualties) as CY_Casulaties 
FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date) = '2022' 
GROUP BY  
    CASE 
 	    WHEN vehicle_type IN ('Agricultural vehical') THEN 'Agricultural' 
 	 	WHEN vehicle_type IN ('Car','Taxi/Private hire car') THEN 'Cars' 
	 	WHEN vehicle_type IN ('Motorcycle 125cc and under ','Motorcycle 50cc  and under', 
'Motorcycle 125cc and up to 500cc','Motorcycle over 500cc','Pedal cycle') THEN 'Bike' 
  WHEN vehicle_type IN('Bus or coach (17 or more pass seats)','Minibus(8-16 passenger seats') THEN 'Bus' 
 	 	WHEN vehicle_type IN('Goods 7.5 tonnes mgw and over','Goods over 3.5t. and under 7.5t','Van/Goods 3.5 tonnes mgw or under') THEN 'Van' 
 	 	ELSE 'Other' 
    END
```
![Image](https://github.com/user-attachments/assets/49c6db16-d19b-44cc-9a89-0a2dcf198d4f) 

###  Month_Name and  Month_Name of Road Accidents

```sql
SELECT DATENAME(MONTH, accident_date) AS Month_Name, SUM(number_of_casualties) AS 
 Month_Name 
FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date) = '2022' 
GROUP BY DATENAME(MONTH,accident_date);
```
 
![Image](https://github.com/user-attachments/assets/02b9f58a-991c-468f-b1bb-ed97bc52ea3a) 

###  road_type CY_Casualties  of Road Accidents

```sql
SELECT road_type, SUM(number_of_casualties) AS CY_Casualties FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date) = '2022' 
GROUP BY road_type;
```

![Image](https://github.com/user-attachments/assets/ecc0c95a-dc28-4c3e-91d0-e211509bf954) 

### urban_or_rural_area PCT of Road Accidents

```sql
SELECT urban_or_rural_area,CAST(SUM(number_of_casualties) as DECIMAL(10,2)) *100/ 
(SELECT CAST(SUM(number_of_casualties) AS DECIMAL(10,2)) FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date) = '2022') AS PCT 
FROM [ROAD ACCIDENTS] 
WHERE YEAR(accident_date) = '2022' 
GROUP BY urban_or_rural_area;
```

![Image](https://github.com/user-attachments/assets/3b450815-b3de-4309-acb6-837a3247263a)


```sql
SELECT  
       CASE 
 	       WHEN light_conditions IN ('Daylight') THEN 'Day' 
 	       WHEN light_conditions IN ('Darkness - lighting unknown','Darkness - lights lit ','Darkness - lights unlit','Darkness - no lighting') THEN 'Night' 
       END AS Light_Condition, 
   CAST(CAST(SUM(number_of_casualties) AS DECIMAL(10,2)) * 100/ 
    (SELECT CAST(SUM(number_of_casualties) AS DECIMAL(10,2)) FROM [ROAD ACCIDENTS] WHERE YEAR(accident_date) = '2022') 
 	   AS DECIMAL(10,2)) AS CY_Casualties_PCT 
   FROM [ROAD ACCIDENTS] 
   WHERE YEAR(accident_date) = '2022' 
   GROUP BY 
   CASE 
         WHEN light_conditions IN ('Daylight') THEN 'Day' 
 	       WHEN light_conditions IN ('Darkness - lighting unknown','Darkness - lights lit ','Darkness - lights unlit','Darkness - no lighting') THEN 'Night' 
END; 
![Image](https://github.com/user-attachments/assets/ef7e31c4-b041-414a-ad65-500da69462c3)
SELECT TOP 10 local_authority,SUM(number_of_casualties) AS Total_Casualties 
FROM [ROAD ACCIDENTS] 
GROUP BY local_authority 
ORDER BY Total_Casualties DESC;
```

![Image](https://github.com/user-attachments/assets/dae232c8-b2a4-4ec8-ba2a-abf0b7907d9a)

Power Bi Dashboard snapshot:

![Image](https://github.com/user-attachments/assets/9ca33b83-d722-4976-864a-56e6109b412b)

Excel dashboard Snapshot:

![Image](https://github.com/user-attachments/assets/891462a5-d25d-4fe5-9644-b4b3da256ec0)

Publish To Power BI

![Image](https://github.com/user-attachments/assets/57c4bc79-76f7-4f0d-89ec-17e5c5d2dc67)

### Creating a new column following DAX expression was write.

**YEAR**:
         YEAR = YEAR('Calendar'[Data])
         
**Month**:
          Month = FORMAT('Calendar'[Data],"mmm")
         
 
### Following DAX expression was written to find Measures.

**CY Casualties**:
         CY Casualties = TOTALYTD(SUM(Road_accident[Number_of_Casualties]),'Calendar'[Data])

**PY Casualties**:
         PY Casualties = CALCULATE(SUM(Road_accidents[Number_of_casualties]),SAMEPERIODLASTYEAR('Calendar'[Data]))
**YOY Casualties**:      
         YOY Casualties = ([CY Csaulaties]-[PY Casualties])/[PY Casualties]
**CY Accidents**:
         CY Accidents = TOTALYTD(COUNT(Road_accident[Accident_index],'Calendar'[Data])
**PY Accidents**:
         PY Accidents = CALCULATE(COUNT(Road_accident[Accident_index],'Calendar'[Data]),SAMEPERIODLASTYEAR('Calendar'[Data]))


# Conclusion:
Road accident analysis helps identify key risk factors such as poor road conditions, weather impacts, driver behavior, and vehicle-related issues. By analyzing accident severity, casualty numbers, and environmental conditions, authorities can implement better safety measures, improve infrastructure, and enforce regulations. Data-driven insights from accident trends aid in reducing fatalities, enhancing emergency response, and minimizing economic losses. Ultimately, continuous monitoring and strategic interventions are crucial for improving road safety and saving lives
# How to use:

1.**clone the Repository**: Clone this project repository from GitHub.

2.**Set Up the Database**: Run the SQL scripts provided in the database_setup.sql file to create and populate the database.

3.**Run the Queries**: Use the SQL queries provided in the analysis_queries.sql file to perform your analysis.

4.**Explore and Modify**:Feel free to modify the queries to explore different aspect of the dataset or answer

snapshot:

![Image](https://github.com/user-attachments/assets/9ca33b83-d722-4976-864a-56e6109b412b)

Excel dashboard:

![Image](https://github.com/user-attachments/assets/891462a5-d25d-4fe5-9644-b4b3da256ec0)

Publish To Power BI

![Image](https://github.com/user-attachments/assets/57c4bc79-76f7-4f0d-89ec-17e5c5d2dc67)

Creating a new column following DAX expression was write.
**YEAR**:
         YEAR = YEAR('Calendar'[Data])
         
**Month**:
          Month = FORMAT('Calendar'[Data],"mmm")
         
 
Following DAX expression was written to find Measures.

**CY Casualties**:
         CY Casualties = TOTALYTD(SUM(Road_accident[Number_of_Casualties]),'Calendar'[Data])

**PY Casualties**:
         PY Casualties = CALCULATE(SUM(Road_accidents[Number_of_casualties]),SAMEPERIODLASTYEAR('Calendar'[Data]))
**YOY Casualties**:      
         YOY Casualties = ([CY Csaulaties]-[PY Casualties])/[PY Casualties]
**CY Accidents**:
         CY Accidents = TOTALYTD(COUNT(Road_accident[Accident_index],'Calendar'[Data])
**PY Accidents**:
         PY Accidents = CALCULATE(COUNT(Road_accident[Accident_index],'Calendar'[Data]),SAMEPERIODLASTYEAR('Calendar'[Data]))

