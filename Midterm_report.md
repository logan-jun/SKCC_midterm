## Question 1
#### Map of restaurants across the United States

```sql
select * from team5_restaurants_df
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
select cat_exploded, count(*) as categorie_count from team5_exploded_df where business_id in ( select distinct business_id from team5_restaurants_df ) and cat_exploded != 'Restaurants'  group by cat_exploded order by categorie_count desc limit 15
```
![Image of map](/images/num3-2.png)
![Image of map](/images/num3-1.png)

## Question 4
#### What ratings do the majority of restaurants have?

```sql
select stars, count(*) from team5_restaurants_df group by stars
```
![Image of map](/images/num4-1.png)
![Image of map](/images/num4-2.png)
![Image of map](/images/num4-3.png)

## Question 5
#### What is rating distribution in the restaurant reviews?

```sql
SELECT r.business_id, b.name, stddev_pop(r.stars) stddev FROM team5_review r JOIN team5_business b ON (r.business_id = b.business_id)  group by r.business_id, b.name LIMIT 10
```
![Image of map](/images/num5.png)

## Question 6
#### Which type of restaurants get good reviews? How about bad reviews?
##### a. This will depend on what you consider a good rating. Above 4 star perhaps? You choose.
```'good review' means restrurant's stars >= 3.5 and tip's likes >= 1
Number 1 ranked 'Food' category is skipped because of normality
```
```sql
select cat_exploded, count(*) from team5_exploded_df where business_id in (select business_id from team5_restaurants_df where where stars >= 3.5 and review_count > 5 ) and cat_exploded not in ('Restaurants', 'Food') group by cat_exploded order by count(*) desc limit 1
```

![Image of map](/images/num6-1.png)
##### b. Similarly, for bad reviews. What would be considered a bad review?

```sql
select cat_exploded, count(*) from team5_exploded_df where business_id in (select business_id from team5_restaurants_df where where stars >= 3.5 and review_count > 5 ) and cat_exploded not in ('Restaurants', 'Food') group by cat_exploded order by count(*) desc limit 1
```
![Image of map](/images/num6-2.png)
## Question 7
#### Which restaurants have the most reviews?

```sql
select name, review_count from team5_restaurants_df order by review_count desc limit 1
```
![Image of map](/images/num7.png)

## Question 8
#### What number of yelp users are elite users?

```sql
SELECT count(*) count FROM team5_elite_df where elite_year > 0
```
![Image of map](/images/num8-1.png)

#### Do they rate differently than non-elite users?
```sql
SELECT user_id,stars FROM team5_review where user_id not in (SELECT user_id FROM team5_elite_df where elite_year > 0)
```
![Image of map](/images/num8-2.png)
