```sql
select * from spatial_ref_sys
limit 50;

select count(*) from spatial_ref_sys;

select * from topology.layer;
select * from topology.topology;


select * from gps_observation_points;


select * from sat_data limit 100000;

select * from sat_data_rcvr_clock;



```


```
# convert to timestamp
SELECT id, "GPSTime", "Speed", TO_CHAR(TO_TIMESTAMP("GPSTime"/1000), 'DD/MM/YYYY HH24:MI:SS')
	FROM public.gps_observation_points

    limit 100;
```

SELECT id, geom, "sysTime", "Lat", "Long", "Alt", "Provider", "GPSTime", "FixSatCount", "HasRadialAccuracy", "HasVerticalAccuracy", "ElapsedRealtimeNanos", "HasSpeed", "HasSpeedAccuracy", "Speed", "SpeedAccuracy", "HasBearing", "HasBearingAccuracy", "Bearing", "BearingAccuracy", data_dump, n, src_path, src_file
	FROM public.gps_observation_points;




SELECT
 gps_observation_points.id,
 gps_observation_points.n,
 gps_observation_points."GPSTime" as time,
 sat_data.id,
 sat_data.agc,
 sat_data.cn0,
 gps_observation_points.Lat,
 gps_observation_points.Alt,
 sat_data.sat_time_lsigma_nanos,
 sat_data.pseudorange_rate_lsigma,
 sat_data.evavation_deg,
 sat_data.azimuth_deg,
 sat_data.azimuth_deg,
 sat_data.constellation,
 sat_data.sync_state_flags


FROM gps_observation_points
INNER JOIN gps_observation_points_sat_data ON gps_observation_points_sat_data.base_id = gps_observation_points.id
INNER JOIN sat_data on gps_observation_points_sat_data.related_id = sat_data.id
where gps_observation_points."GPSTime" >= 1538523240000 and gps_observation_points."GPSTime" < 1538782440000
LIMIT 100;
