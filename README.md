# FLaNK-IrelandTransit
Transit in Ireland



#### Flink SQL

````

CREATE TABLE `ssb`.`Meetups`.`irelandvehicle` (
  `recordid` VARCHAR(2147483647),
  `route_id` VARCHAR(2147483647),
  `directionid` VARCHAR(2147483647),
  `latitude` VARCHAR(2147483647),
  `tripid` VARCHAR(2147483647),
  `starttime` VARCHAR(2147483647),
  `vehicleid` VARCHAR(2147483647),
  `startdate` VARCHAR(2147483647),
  `uuid` VARCHAR(2147483647),
  `longitude` VARCHAR(2147483647),
  `timestamp` VARCHAR(2147483647),
  `ts` VARCHAR(2147483647),
  `route_long_name` VARCHAR(2147483647),
  `trip_short_name` VARCHAR(2147483647),
  `trip_headsign` VARCHAR(2147483647),
  `eventTimeStamp` TIMESTAMP(3) WITH LOCAL TIME ZONE METADATA FROM 'timestamp',
  WATERMARK FOR `eventTimeStamp` AS `eventTimeStamp` - INTERVAL '3' SECOND
) WITH (
  'scan.startup.mode' = 'group-offsets',
  'deserialization.failure.policy' = 'ignore_and_log',
  'properties.request.timeout.ms' = '120000',
  'properties.auto.offset.reset' = 'earliest',
  'format' = 'json',
  'properties.bootstrap.servers' = 'kafka:9092',
  'connector' = 'kafka',
  'properties.transaction.timeout.ms' = '900000',
  'topic' = 'irelandvehicle',
  'properties.group.id' = 'irelandconsumersbb1'
)

````

````
