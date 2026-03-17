`vacuum verbose analyze logline_identifier_row;`

```
vacuuming "crossdevice.public.logline_identifier_row"
launched 2 parallel vacuum workers for index vacuuming (planned: 2)
finished vacuuming "crossdevice.public.logline_identifier_row": index scans: 1
pages: 0 removed, 181447500 remain, 26017511 scanned (14.34% of total)
tuples: 22025402 removed, 12326589282 remain, 0 are dead but not yet removable
removable cutoff: 72917514, which was 217278 XIDs old when operation ended
index scan needed: 329007 pages from table (0.18% of total) had 22051817 dead item identifiers removed
index "logline_identifier_row_identifier_type_row_id_logline_type_key": pages: 236380197 in total, 0 newly deleted, 0 currently deleted, 0 reusable
index "logline_identifier_row_logline_type_row_type_identifier_index": pages: 236038759 in total, 0 newly deleted, 14 currently deleted, 14 reusable
index "logline_identifier_row_loglinetype_type_lower_identifier": pages: 77121566 in total, 0 newly deleted, 19 currently deleted, 19 reusable
I/O timings: read: 10772443.803 ms, write: 0.000 ms
avg read rate: 0.070 MB/s, avg write rate: 0.000 MB/s
buffer usage: 289011938 hits, 102913 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 2829.11 s, system: 85.26 s, elapsed: 11485.26 s
aggressively vacuuming "crossdevice.pg_toast.pg_toast_5500955"
finished vacuuming "crossdevice.pg_toast.pg_toast_5500955": index scans: 0
pages: 0 removed, 0 remain, 0 scanned (100.00% of total)
tuples: 0 removed, 0 remain, 0 are dead but not yet removable
removable cutoff: 72917514, which was 217278 XIDs old when operation ended
new relfrozenxid: 72917514, which is 185858723 XIDs ahead of previous value
new relminmxid: 221134, which is 221133 MXIDs ahead of previous value
index scan not needed: 0 pages from table (100.00% of total) had 0 dead item identifiers removed
I/O timings: read: 0.770 ms, write: 0.000 ms
avg read rate: 8.005 MB/s, avg write rate: 0.000 MB/s
buffer usage: 87 hits, 1 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 0.00 s, system: 0.00 s, elapsed: 0.00 s
analyzing "public.logline_identifier_row"
"logline_identifier_row": scanned 30000 of 181447500 pages, containing 2040864 live rows and 0 dead rows; 30000 rows in sample, 12343655688 estimated total rows
[2024-08-22 15:59:37] completed in 3 h 11 m 58 s 532 ms
```

```
crossdevice.public> vacuum verbose analyze liveramp_cookie
vacuuming "crossdevice.public.liveramp_cookie"
launched 2 parallel vacuum workers for index vacuuming (planned: 2)
finished vacuuming "crossdevice.public.liveramp_cookie": index scans: 1
pages: 0 removed, 13178500 remain, 3307191 scanned (25.10% of total)
tuples: 624406 removed, 757381846 remain, 82873 are dead but not yet removable
removable cutoff: 72917514, which was 223099 XIDs old when operation ended
index scan needed: 628649 pages from table (4.77% of total) had 691916 dead item identifiers removed
index "liveramp_cookie_new_pkey": pages: 7481750 in total, 0 newly deleted, 0 currently deleted, 0 reusable
index "liveramp_cookie_new_cookie_cluster_idx": pages: 14755440 in total, 0 newly deleted, 0 currently deleted, 0 reusable
index "liveramp_cookie_created": pages: 2912640 in total, 0 newly deleted, 57001 currently deleted, 57001 reusable
index "liveramp_cookie_cluster": pages: 4372439 in total, 0 newly deleted, 0 currently deleted, 0 reusable
I/O timings: read: 402201.676 ms, write: 0.000 ms
avg read rate: 0.043 MB/s, avg write rate: 0.000 MB/s
buffer usage: 14739950 hits, 3616 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 230.97 s, system: 9.02 s, elapsed: 660.98 s
aggressively vacuuming "crossdevice.pg_toast.pg_toast_207378"
finished vacuuming "crossdevice.pg_toast.pg_toast_207378": index scans: 0
pages: 0 removed, 0 remain, 0 scanned (100.00% of total)
tuples: 0 removed, 0 remain, 0 are dead but not yet removable
removable cutoff: 72917514, which was 223099 XIDs old when operation ended
new relfrozenxid: 72917514, which is 172353731 XIDs ahead of previous value
new relminmxid: 221232, which is 221231 MXIDs ahead of previous value
index scan not needed: 0 pages from table (100.00% of total) had 0 dead item identifiers removed
I/O timings: read: 2.103 ms, write: 0.000 ms
avg read rate: 3.425 MB/s, avg write rate: 0.000 MB/s
buffer usage: 79 hits, 1 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 0.00 s, system: 0.00 s, elapsed: 0.00 s
analyzing "public.liveramp_cookie"
"liveramp_cookie": scanned 30000 of 13178500 pages, containing 1750509 live rows and 200 dead rows; 30000 rows in sample, 768969429 estimated total rows
[2024-08-22 16:19:34] completed in 11 m 32 s 218 ms

```

```
crossdevice.public> vacuum verbose analyze liveramp_aaid
vacuuming "crossdevice.public.liveramp_aaid"
launched 2 parallel vacuum workers for index cleanup (planned: 2)
finished vacuuming "crossdevice.public.liveramp_aaid": index scans: 0
pages: 0 removed, 30731899 remain, 15868360 scanned (51.63% of total)
tuples: 0 removed, 1247643772 remain, 40967068 are dead but not yet removable
removable cutoff: 72917514, which was 232431 XIDs old when operation ended
index scan not needed: 0 pages from table (0.00% of total) had 0 dead item identifiers removed
I/O timings: read: 269181.200 ms, write: 0.000 ms
avg read rate: 0.000 MB/s, avg write rate: 0.000 MB/s
buffer usage: 31810911 hits, 0 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 149.05 s, system: 2.98 s, elapsed: 411.62 s
aggressively vacuuming "crossdevice.pg_toast.pg_toast_207394"
finished vacuuming "crossdevice.pg_toast.pg_toast_207394": index scans: 0
pages: 0 removed, 0 remain, 0 scanned (100.00% of total)
tuples: 0 removed, 0 remain, 0 are dead but not yet removable
removable cutoff: 72917514, which was 232431 XIDs old when operation ended
new relfrozenxid: 72917514, which is 172353731 XIDs ahead of previous value
new relminmxid: 221400, which is 221399 MXIDs ahead of previous value
index scan not needed: 0 pages from table (100.00% of total) had 0 dead item identifiers removed
I/O timings: read: 1.296 ms, write: 0.000 ms
avg read rate: 5.205 MB/s, avg write rate: 0.000 MB/s
buffer usage: 93 hits, 1 misses, 0 dirtied
WAL usage: 0 records, 0 full page images, 0 bytes
system usage: CPU: user: 0.00 s, system: 0.00 s, elapsed: 0.00 s
analyzing "public.liveramp_aaid"
"liveramp_aaid": scanned 30000 of 30731899 pages, containing 1063909 live rows and 40122 dead rows; 30000 rows in sample, 1089864798 estimated total rows
[2024-08-22 16:45:12] completed in 7 m 22 s 651 ms
```