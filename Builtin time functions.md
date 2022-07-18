# Builtin time functions

These functions are especially useful for creating time interval values to group data with.

### Date trunc

Syntax:

```sql
date_trunc(field, source [, time_zone ])
```

Source is a value expression of type timestamp, timestamp with time zone, or interval. (values of type date and time are cast automatically to timestamp or interval, respectively) Field selects to which precision to truncate the input value. The return value is likewise of type timestamp, timestamp with time zone, or interval, and it has all fields that are less significant than the selected one set to zero (or one, for day and month).
Valid values for field are:

- microseconds,
- milliseconds, 
- second, 
- minute, 
- hour, 
- day, 
- week, 
- month, 
- quarter,
- year, 
- decade, 
- century,
- millennium.


Basic usage: 

```sql
SELECT date_trunc('hour', time_col) AS interval;
```

### Date bin

The function date_bin “bins” the input timestamp into the specified interval (the stride) aligned with a specified origin.

```sql
date_bin(stride, source, origin)
```

Source is a value expression of type timestamp or timestamp with time zone. (values of type date are cast automatically to timestamp) Stride is a value expression of type interval. The return value is likewise of type timestamp or timestamp with time zone, and it marks the beginning of the bin into which the source is placed.

Basic usage:

```sql
SELECT date_bin('15 minutes', TIMESTAMP '2020-02-11 15:44:17', TIMESTAMP '2001-01-01');
```

Result: 2020-02-11 15:30:00