/****** Script for SelectTopNRows command from SSMS  ******/
SELECT TOP (1000) [ID]
      ,[Gender]
      ,[Sleep duration]
      ,[Sleep efficiency]
      ,[REM sleep percentage]
      ,[Deep sleep percentage]
      ,[Light sleep percentage]
      ,[Awakenings]
      ,[Caffeine consumption]
      ,[Alcohol consumption]
      ,[Smoking status]
      ,[Exercise frequency]
  FROM [Sleep Project].[dbo].[Sleep_EfficiencyProject$]

  --Sleep statistics:various sleep statistics such as average sleep duration, average sleep efficiency, average percentages of different types of sleep (REM, deep, light), and number of awakenings.
 
 SELECT AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([REM sleep percentage]) AS AvgREMSleepPercentage,
       AVG([Deep sleep percentage]) AS AvgDeepSleepPercentage,
       AVG([Light sleep percentage]) AS AvgLightSleepPercentage,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]

--Gender Difference

SELECT [Gender],
       AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([REM sleep percentage]) AS AvgREMSleepPercentage,
       AVG([Deep sleep percentage]) AS AvgDeepSleepPercentage,
       AVG([Light sleep percentage]) AS AvgLightSleepPercentage,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
GROUP BY [Gender]

--Lifestyle Factors 

SELECT [Caffeine consumption],
       AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
WHERE [Caffeine consumption] is not null
GROUP BY [Caffeine consumption]

SELECT [Alcohol consumption],
       AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
WHERE [Alcohol consumption] is not null
GROUP BY [Alcohol consumption]

SELECT [Smoking status],
       AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
WHERE [Smoking status] is not null
GROUP BY [Smoking status]

SELECT [Exercise frequency],
       AVG([Sleep duration]) AS AvgSleepDuration,
       AVG([Sleep efficiency]) AS AvgSleepEfficiency,
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
WHERE [Exercise frequency] is not null
GROUP BY [Exercise frequency]

--Correlations

SELECT [Caffeine consumption], 
       AVG([Awakenings]) AS AvgAwakenings
FROM [Sleep_EfficiencyProject$]
WHERE [Caffeine consumption] is not null
GROUP BY [Caffeine consumption]

SELECT [Exercise frequency], 
       AVG([Sleep efficiency]) AS AvgSleepEfficiency
FROM [Sleep_EfficiencyProject$]
WHERE [Exercise frequency] is not null
GROUP BY [Exercise frequency]

--distribution of sleep duration or the frequency of different levels of caffeine consumption

SELECT [Caffeine consumption], 
       COUNT(*) AS Count
FROM [Sleep_EfficiencyProject$]
WHERE [Caffeine consumption] is not null
GROUP BY [Caffeine consumption]

SELECT [Sleep duration], 
       COUNT(*) AS Count
FROM [Sleep_EfficiencyProject$]
WHERE [Sleep duration] is not null
GROUP BY [Sleep duration]
