

# get_Recent_Requests

```txt
This allows a project manager to find the recent requests made by passengers by entering the number of the request he want to look up  
will show the passenger information associated with request details.
```

```SQL
CREATE DEFINER=`mm_cpsc502101team10`@`%` PROCEDURE `get_Recent_Requests`(IN req INT)
BEGIN
SELECT 
	Request_ID, 
	Passenger_ID,
	Request_Pickup_Location,
	Request_Drop_Off_Location,
	Request_Time
FROM 
	Request 
LIMIT 
	req;
END
```

 Invoke the procedure:

```SQL
CALL get_Recent_Requests(5);
```

![image-20210516140215316](https://raw.githubusercontent.com/Youjin6/pic/master/img/20210516140216.png)

# get_Passenger_Info

```txt
This allows a project manager to find the information of a certain passenger by entering the passenger ID and the information fields he want to check
will show the Passenger_ID,Passenger_First_Name,Passenger_Last_Name and Passenger_Phone.
```

```SQL
CREATE DEFINER=`mm_cpsc502101team10`@`%` PROCEDURE `get_Passenger_Info`(
	IN pID int,
    OUT ppid int,
    OUT pfname VARCHAR(45),
    OUT plname VARCHAR(45),
    OUT pphone varchar(45)
    
)
BEGIN
	select 
		Passenger_ID,
        Passenger_First_Name,
        Passenger_Last_Name,
		Passenger_Phone
	FROM 
		Passenger 
    WHERE 
		Passenger_ID = pID
    INTO 
    ppid,
	pfname,
    plname,
    pphone;
END
```

 Invoke the procedure:

```sql
CALL get_Passenger_Info(1, @Passenger_ID,
        @Passenger_First_Name,
        @Passenger_Last_Name,
		@Passenger_Phone);
select @Passenger_ID,
        @Passenger_First_Name,
        @Passenger_Last_Name,
		@Passenger_Phone;
```

![image-20210516140527377](https://raw.githubusercontent.com/Youjin6/pic/master/img/20210516140531.png)

# update_Table_Passenger

```
This allows a project manager to insert new data into the passenger table by entering the Passenger_ID,Passenger_First_Name,Passenger_Last_Name,Passenger_Phone,
Passenger_Request,Trip_ID and SRCar_ID.
```



```SQL
CREATE DEFINER=`mm_cpsc502101team10`@`%` PROCEDURE `update_Table_Passenger`(
IN Passenger_ID VARCHAR(45),
IN Passenger_First_Name VARCHAR(45),
IN Passenger_Last_Name  VARCHAR(45),
IN Passenger_Phone VARCHAR(45),
IN Passenger_Request VARCHAR(45),
IN Trip_ID INT,
IN SRCar_ID INT
)
BEGIN
INSERT INTO Passenger(
	Passenger_ID,
    Passenger_First_Name,
    Passenger_Last_Name,
    Passenger_Phone,
    Passenger_Request,
    Trip_ID,
    SRCar_ID)
VALUES(
	Passenger_ID,
	Passenger_First_Name,
    Passenger_Last_Name,
    Passenger_Phone,
    Passenger_Request,
    Trip_ID,
    SRCar_ID);
ENDone;
END
```

 Invoke the procedure:

```sql
    CALL update_Table_Passenger(15,'Cindy','Stewart','206-565-8984','Comfirmed',225,136);    CALL update_Table_Passenger(16,'Judy','Scott','226-535-4943','Comfirmed',226,134);    CALL update_Table_Passenger(17,'Alex','George','234-545-2342','Comfirmed',227,125);    CALL update_Table_Passenger(18,'Smith','Kathy','223-323-4323','Comfirmed',228,134);
```

![image-20210516144143108](https://raw.githubusercontent.com/Youjin6/pic/master/img/20210516144144.png)

