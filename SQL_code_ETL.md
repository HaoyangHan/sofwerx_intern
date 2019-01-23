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