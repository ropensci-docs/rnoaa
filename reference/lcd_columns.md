# Specify Variable Types in Local Climatological Data from NOAA

Use this function to specify what variable types will be returned by
[lcd](https://docs.ropensci.org/rnoaa/reference/lcd.md). The function
returns a named vector with specified column classes. The defaults are
specified in the argument descriptions below.

## Usage

``` r
lcd_columns(
  STATION = "character",
  DATE = "POSIXct",
  LATITUDE = "numeric",
  LONGITUDE = "numeric",
  ELEVATION = "numeric",
  NAME = "character",
  REPORT_TYPE = "character",
  SOURCE = "character",
  HourlyAltimeterSetting = "character",
  HourlyDewPointTemperature = "character",
  HourlyDryBulbTemperature = "character",
  HourlyPrecipitation = "character",
  HourlyPresentWeatherType = "character",
  HourlyPressureChange = "character",
  HourlyPressureTendency = "integer",
  HourlyRelativeHumidity = "character",
  HourlySkyConditions = "character",
  HourlySeaLevelPressure = "character",
  HourlyStationPressure = "character",
  HourlyVisibility = "character",
  HourlyWetBulbTemperature = "character",
  HourlyWindDirection = "character",
  HourlyWindGustSpeed = "character",
  HourlyWindSpeed = "character",
  Sunrise = "numeric",
  Sunset = "numeric",
  DailyAverageDewPointTemperature = "character",
  DailyAverageDryBulbTemperature = "character",
  DailyAverageRelativeHumidity = "character",
  DailyAverageSeaLevelPressure = "character",
  DailyAverageStationPressure = "character",
  DailyAverageWetBulbTemperature = "character",
  DailyAverageWindSpeed = "character",
  DailyCoolingDegreeDays = "numeric",
  DailyDepartureFromNormalAverageTemperature = "numeric",
  DailyHeatingDegreeDays = "numeric",
  DailyMaximumDryBulbTemperature = "numeric",
  DailyMinimumDryBulbTemperature = "numeric",
  DailyPeakWindDirection = "numeric",
  DailyPeakWindSpeed = "numeric",
  DailyPrecipitation = "character",
  DailySnowDepth = "character",
  DailySnowfall = "character",
  DailySustainedWindDirection = "numeric",
  DailySustainedWindSpeed = "numeric",
  DailyWeather = "character",
  MonthlyAverageRH = "numeric",
  MonthlyDaysWithGT001Precip = "numeric",
  MonthlyDaysWithGT010Precip = "numeric",
  MonthlyDaysWithGT32Temp = "numeric",
  MonthlyDaysWithGT90Temp = "numeric",
  MonthlyDaysWithLT0Temp = "numeric",
  MonthlyDaysWithLT32Temp = "numeric",
  MonthlyDepartureFromNormalAverageTemperature = "numeric",
  MonthlyDepartureFromNormalCoolingDegreeDays = "numeric",
  MonthlyDepartureFromNormalHeatingDegreeDays = "numeric",
  MonthlyDepartureFromNormalMaximumTemperature = "numeric",
  MonthlyDepartureFromNormalMinimumTemperature = "numeric",
  MonthlyDepartureFromNormalPrecipitation = "numeric",
  MonthlyDewpointTemperature = "numeric",
  MonthlyGreatestPrecip = "numeric",
  MonthlyGreatestPrecipDate = "character",
  MonthlyGreatestSnowDepth = "numeric",
  MonthlyGreatestSnowDepthDate = "character",
  MonthlyGreatestSnowfall = "numeric",
  MonthlyGreatestSnowfallDate = "character",
  MonthlyMaxSeaLevelPressureValue = "numeric",
  MonthlyMaxSeaLevelPressureValueDate = "character",
  MonthlyMaxSeaLevelPressureValueTime = "character",
  MonthlyMaximumTemperature = "numeric",
  MonthlyMeanTemperature = "numeric",
  MonthlyMinSeaLevelPressureValue = "numeric",
  MonthlyMinSeaLevelPressureValueDate = "character",
  MonthlyMinSeaLevelPressureValueTime = "character",
  MonthlyMinimumTemperature = "numeric",
  MonthlySeaLevelPressure = "numeric",
  MonthlyStationPressure = "numeric",
  MonthlyTotalLiquidPrecipitation = "numeric",
  MonthlyTotalSnowfall = "numeric",
  MonthlyWetBulb = "numeric",
  AWND = "numeric",
  CDSD = "numeric",
  CLDD = "numeric",
  DSNW = "numeric",
  HDSD = "numeric",
  HTDD = "numeric",
  NormalsCoolingDegreeDay = "numeric",
  NormalsHeatingDegreeDay = "numeric",
  ShortDurationEndDate005 = "character",
  ShortDurationEndDate010 = "character",
  ShortDurationEndDate015 = "character",
  ShortDurationEndDate020 = "character",
  ShortDurationEndDate030 = "character",
  ShortDurationEndDate045 = "character",
  ShortDurationEndDate060 = "character",
  ShortDurationEndDate080 = "character",
  ShortDurationEndDate100 = "character",
  ShortDurationEndDate120 = "character",
  ShortDurationEndDate150 = "character",
  ShortDurationEndDate180 = "character",
  ShortDurationPrecipitationValue005 = "numeric",
  ShortDurationPrecipitationValue010 = "numeric",
  ShortDurationPrecipitationValue015 = "numeric",
  ShortDurationPrecipitationValue020 = "numeric",
  ShortDurationPrecipitationValue030 = "numeric",
  ShortDurationPrecipitationValue045 = "numeric",
  ShortDurationPrecipitationValue060 = "numeric",
  ShortDurationPrecipitationValue080 = "numeric",
  ShortDurationPrecipitationValue100 = "numeric",
  ShortDurationPrecipitationValue120 = "numeric",
  ShortDurationPrecipitationValue150 = "numeric",
  ShortDurationPrecipitationValue180 = "numeric",
  REM = "character",
  BackupDirection = "character",
  BackupDistance = "character",
  BackupDistanceUnit = "character",
  BackupElements = "character",
  BackupElevation = "character",
  BackupEquipment = "character",
  BackupLatitude = "character",
  BackupLongitude = "character",
  BackupName = "character",
  WindEquipmentChangeDate = "character"
)
```

## Arguments

- STATION:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- LATITUDE:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- LONGITUDE:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ELEVATION:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- NAME:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- REPORT_TYPE:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- SOURCE:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyAltimeterSetting:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyDewPointTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyDryBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyPrecipitation:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyPresentWeatherType:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyPressureChange:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyPressureTendency:

  (character) string indicating variable or column type that is
  returned, default is "integer". optional

- HourlyRelativeHumidity:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlySkyConditions:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlySeaLevelPressure:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyStationPressure:

  (character)string indicating variable or column type that is returned,
  default is "character". optional

- HourlyVisibility:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyWetBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyWindDirection:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyWindGustSpeed:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- HourlyWindSpeed:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- Sunrise:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- Sunset:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyAverageDewPointTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageDryBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageRelativeHumidity:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageSeaLevelPressure:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageStationPressure:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageWetBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyAverageWindSpeed:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailyCoolingDegreeDays:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyDepartureFromNormalAverageTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyHeatingDegreeDays:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyMaximumDryBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyMinimumDryBulbTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyPeakWindDirection:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyPeakWindSpeed:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyPrecipitation:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailySnowDepth:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailySnowfall:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- DailySustainedWindDirection:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailySustainedWindSpeed:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DailyWeather:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyAverageRH:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithGT001Precip:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithGT010Precip:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithGT32Temp:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithGT90Temp:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithLT0Temp:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDaysWithLT32Temp:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalAverageTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalCoolingDegreeDays:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalHeatingDegreeDays:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalMaximumTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalMinimumTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDepartureFromNormalPrecipitation:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyDewpointTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyGreatestPrecip:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyGreatestPrecipDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyGreatestSnowDepth:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyGreatestSnowDepthDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyGreatestSnowfall:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyGreatestSnowfallDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyMaxSeaLevelPressureValue:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyMaxSeaLevelPressureValueDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyMaxSeaLevelPressureValueTime:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyMaximumTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyMeanTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyMinSeaLevelPressureValue:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyMinSeaLevelPressureValueDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyMinSeaLevelPressureValueTime:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- MonthlyMinimumTemperature:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlySeaLevelPressure:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyStationPressure:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyTotalLiquidPrecipitation:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyTotalSnowfall:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- MonthlyWetBulb:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- AWND:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- CDSD:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- CLDD:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- DSNW:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- HDSD:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- HTDD:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- NormalsCoolingDegreeDay:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- NormalsHeatingDegreeDay:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationEndDate005:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate010:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate015:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate020:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate030:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate045:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate060:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate080:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate100:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate120:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate150:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationEndDate180:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- ShortDurationPrecipitationValue005:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue010:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue015:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue020:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue030:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue045:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue060:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue080:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue100:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue120:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue150:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- ShortDurationPrecipitationValue180:

  (character) string indicating variable or column type that is
  returned, default is "numeric". optional

- REM:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupDirection:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupDistance:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupDistanceUnit:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupElements:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupElevation:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupEquipment:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupLatitude:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupLongitude:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- BackupName:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

- WindEquipmentChangeDate:

  (character) string indicating variable or column type that is
  returned, default is "character". optional

## Value

a vector indicating column classes types

## Note

if the column type is not compatible,
[lcd](https://docs.ropensci.org/rnoaa/reference/lcd.md) will return a
dataframe with the most appropriate column type and a message indicating
the column was not changed to the specified type.
