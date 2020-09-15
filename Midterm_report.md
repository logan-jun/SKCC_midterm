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
#### Which are the top 15 subcategories in Restaurants?

```sql
select * from team5_restaurants_df limit 5
```

![Image of map](/images/map.png)

## Question 4
#### What ratings do the majority of restaurants have?

```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)

## Question 5
#### What is rating distribution in the restaurant reviews?

```sql
SELECT r.business_id, b.name, stddev_pop(r.stars) stddev FROM team5_review r JOIN team5_business b ON (r.business_id = b.business_id)  group by r.business_id, b.name LIMIT 10
```
![Image of map](/images/num5.png)

## Question 6
#### Which type of restaurants get good reviews? How about bad reviews?
##### a. This will depend on what you consider a good rating. Above 4 star perhaps? You choose.

```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)
##### b. Similarly, for bad reviews. What would be considered a bad review?

```sql
select * from team5_restaurants_df limit 5
```
![Image of map](/images/map.png)

## Question 7
#### Which restaurants have the most reviews?

```sql
select name, review_count from team5_restaurants_df order by review_count desc limit 1
```
![Image of map](/images/num7.png)

## Question 8
#### What number of yelp users are elite users? Do they rate differently than non-elite users?

```sql
select * from team5_restaurants_df limit 5
```

![Image of map](/images/map.png)
