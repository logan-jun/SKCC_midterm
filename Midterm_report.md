## Question 1
#### Map of restaurants across the United States
```sql
select * from team5_restaurants_df limit 5
```

![Image of map](/images/map.png)

## Question 2
#### Which cities have the highest number of restaurants?
```sql
select * from (select state, count(business_id) as cnt_r from team5_restaurants_df group by state order by count(business_id) desc ) limit 1
```

![Image of map](/images/num2.png)

## Question 3

```sql
select * from team5_restaurants_df limit 5
```

![Image of map](/images/map.png)

## Question 4

```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)

## Question 5

```sql
SELECT r.business_id, b.name, stddev_pop(r.stars) stddev FROM team5_review r JOIN team5_business b ON (r.business_id = b.business_id)  group by r.business_id, b.name LIMIT 10
```
![Image of map](/images/num5.png)

## Question 6

```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)

## Question 7
#### Which restaurants have the most reviews?
```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)

## Question 8

```sql
select * from team5_restaurants_df limit 5
```

![Image of map](/images/map.png)
