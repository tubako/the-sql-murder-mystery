# 🔫 The SQL Murder Mystery

## A short description
[The SQL murder mystery](https://mystery.knightlab.com/) is a website where you can solve an intriguing murder by analyzing the database that is given.
<p align="center">
  <img src="https://user-images.githubusercontent.com/70372302/232320630-bd5efbce-91eb-41c1-97a5-8454adb13a23.jpg">
</p>

## Let's get to the murder
    "A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. 
    You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​." 
    
```sql
SELECT *
FROM crime_scene_report
where date = 20180115 and type = "murder" and city = "SQL City"
```

![image](https://user-images.githubusercontent.com/70372302/232322255-2036d3b9-6928-417d-ba28-336a15b778c5.png)


```sql
SELECT *
FROM person
where address_street_name = "Northwestern Dr"
order by address_number desc
``` 

![image](https://user-images.githubusercontent.com/70372302/232322154-5709b97b-ba48-4e62-aa4f-91bbb217750b.png)


```sql
SELECT *
FROM person
where address_street_name = "Franklin Ave" and name like "Annabel %"
```

![image](https://user-images.githubusercontent.com/70372302/232322194-2ab46dea-3a14-4d2a-9246-07f0f7202fe6.png)


```sql
SELECT *
FROM interview
where person_id in (14887, 16371)
```
![image](https://user-images.githubusercontent.com/70372302/232322486-31901986-27b7-4cb4-ad63-1bb766b390eb.png)

```sql
SELECT id, name, membership_status, membership_start_date, get_fit_now_check_in.check_in_date
FROM get_fit_now_member
left join get_fit_now_check_in
on id = membership_id
where check_in_date = 20180109 
```
![image](https://user-images.githubusercontent.com/70372302/232323290-328789f5-9cd3-4c9f-a655-4fdce1c8cc70.png)

```sql
SELECT person_id, id, name, membership_status, membership_start_date, get_fit_now_check_in.check_in_date
FROM get_fit_now_member
left join get_fit_now_check_in
on id = membership_id
where check_in_date = 20180109 and membership_status = "gold"  and id like "48Z%" 
```
![image](https://user-images.githubusercontent.com/70372302/232323467-d47692fb-1870-41a8-a04d-822b7e459f0d.png)

```sql
SELECT person.id, license_id, name, drivers_license.plate_number
FROM person
join drivers_license
on license_id = drivers_license.id
where person.id in (28819, 67318) and drivers_license.plate_number like "%H42W%"
```
![image](https://user-images.githubusercontent.com/70372302/232323873-9d8bd6de-aa4d-4ffa-9f46-4a7032a5b9cd.png)

    "Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the interview 
    transcript of the murderer to find the real villain behind this crime. If you feel especially confident in your SQL skills, 
    try to complete this final step with no more than 2 queries."


```sql
SELECT *
FROM interview
where person_id = 67318
```
![image](https://user-images.githubusercontent.com/70372302/232324103-3906e9c1-9d12-4c46-b918-3fee47e84ad7.png)

```sql
SELECT person.id, height, hair_color, gender, plate_number, car_make, car_model
FROM drivers_license
left join person
on drivers_license.id = person.license_id
where hair_color = "red" and gender= "female" and car_make = "Tesla" and car_model= "Model S"
```
![image](https://user-images.githubusercontent.com/70372302/232324540-11e28c5c-a6ca-4cc0-9a0c-2b94537f74f5.png)

```sql
SELECT person.name, event_id, event_name, date
FROM facebook_event_checkin
join person
on person_id = id
where person_id in (99716, 90700, 78881)
```
![image](https://user-images.githubusercontent.com/70372302/232324737-212f0d4d-5118-43a0-a9e5-01ef6f768f7d.png)


    "Congrats, you found the brains behind the murder! Everyone in SQL City hails you as the greatest SQL detective of all time. 
    Time to break out the champagne!"
