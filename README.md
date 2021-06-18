# demo1
Demo I


SELECT * FROM [INSERT TABLE] 
WHERE customers_table IS NOT NULL AND user_id IN 
  (SELECT user_id FROM customers);


#standardSQL
SELECT
  Serial,
  MAX(createdAt) AS Latest_Use,
  ROUND(SUM(ConnectionTime/3600),2) AS Total_Hours,
  COUNT(DISTINCT DeviceID) AS Devices_Connected
FROM `dataworks-356fa.FirebaseArchive.Firebase_ConnectionInfo`
WHERE PeripheralType = 1 OR PeripheralType = 2 OR PeripheralType = 12
GROUP BY Serial
ORDER BY Latest_Use DESC


CREATE TABLE #YourTable ([ID] INT, [Name] CHAR(1), [Value] INT)

INSERT INTO #YourTable ([ID],[Name],[Value]) VALUES (1,'A',4)
INSERT INTO #YourTable ([ID],[Name],[Value]) VALUES (1,'B',8)
INSERT INTO #YourTable ([ID],[Name],[Value]) VALUES (2,'C',9)

SELECT 
  [ID],
  STUFF((
    SELECT ', ' + [Name] + ':' + CAST([Value] AS VARCHAR(MAX)) 
    FROM #YourTable 
    WHERE (ID = Results.ID) 
    FOR XML PATH(''),TYPE).value('(./text())[1]','VARCHAR(MAX)')
  ,1,2,'') AS NameValues
FROM #YourTable Results
GROUP BY ID

DROP TABLE #YourTable
