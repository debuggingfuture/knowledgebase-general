### Old School Way
- Order by + Limit + OFFSET
- it works
- bad performance
  - if no index for order by
  - case of first fetch:   performance worsen with rows# matching where
  - case of subsequent pages: Need to sort all rows
  - ![image](https://cloud.githubusercontent.com/assets/1883877/15132973/489da5da-1691-11e6-8d10-543f1174797a.png)

#### syntac sugar since SQL-2008
- `fetch first 10 rows only`

### Seek Method 
- by cursor, comparing with what you returned last time
- "Row Value"/Composite values - (x,y) > (a,b) iff (x>a || x=a && y>b)


### Reference
- https://wiki.postgresql.org/images/3/35/Pagination_Done_the_PostgreSQL_Way.pdf


##### Working against empty timestamp in text 
```
 (CASE (updated_at is null) 
 WHEN true THEN timestamp 'epoch'
 ELSE updated_at
 END) desc limit 100;
 ```
