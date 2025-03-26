# Power BI Measures, Columns, and Tables

## Lio Cinema

### Measures

1. **Total Content Items**
   ```DAX
   Total content items_lc = DISTINCTCOUNT('liocinema_db contents'[content_id])
   ```
   - Counts the unique content available on the Lio Cinema platform.

2. **Total Users**
   ```DAX
   Total users_lc cm = DISTINCTCOUNT('liocinema_db subscribers'[user_id])
   ```
   - Counts all unique users/subscribers on the platform.
  
3. **Total Users (Previous Month)**
   ```Dax
   Total Users lc pm = CALCULATE([Total users_lc cm], DATEADD('Calendar'[Date], -1, MONTH) -- Shifts date back by 1 month
   ```
   - Counts all unique users/subscribers on the platform in previous month.

4. **Paid Users (Two Methods)**
   a. **Method 1:**
   ```DAX
   Paid users_lc sp = CALCULATE([Total users_lc], 'liocinema_db subscribers'[subscription_plan] IN {"Basic", "Premium"})
   ```
   b. **Method 2:**
   ```DAX
   Paid users_lc using filter sp = COUNTX(
      FILTER('liocinema_db subscribers', 'liocinema_db subscribers'[subscription_plan] IN {"Basic", "Premium"}),
             liocinema_db subscribers'[user_id]
   )
   ```
   - Calculates paid users considering only `subscription_plan`, not `new_subscription_plan`.

5. **Paid Users Considering Subscription Plan and New Subscription Plan**
   ```DAX
   Paid users considering sp and nsp lc = COUNTX(
       FILTER('liocinema_db subscribers',
              'liocinema_db subscribers'[subscription_plan] IN {"Basic", "Premium"} &&
              'liocinema_db subscribers'[new_subscription_plan] IN {"Basic", "Premium"}),
       'liocinema_db subscribers'[user_id]
   )
   ```
   - Includes users with a paid plan in both `subscription_plan` and `new_subscription_plan`.

6. **Paid Users % Based on Subscription Plan**
   ```DAX
   Paid users % lc sp = DIVIDE([Paid users_lc], [Total users_lc], 0)
   ```
   - Percentage of paid users from `subscription_plan`.

7. **Paid Users % Considering Subscription Plan and New Subscription Plan**
   ```DAX
   Paid users % considering sp and nsp lc = DIVIDE([Paid users considering sp and nsp lc], [Total users_lc], 0)
   ```
   - Percentage of paid users considering both `subscription_plan` and `new_subscription_plan`.

8. **Paid Users Based on New Subscription Plan**
   ```DAX
   Paid users_lc nsp = CALCULATE([Total users_lc], 'liocinema_db subscribers'[new_subscription_plan] IN {"Basic", "Premium"})
   ```
   - Calculates paid users from `new_subscription_plan`.

9. **Paid Users % Based on New Subscription Plan**
   ```DAX
   Paid users % lc nsp = DIVIDE([Paid users_lc nsp], [Total users_lc], 0)
   ```
   - Percentage of paid users based on `new_subscription_plan`.

10. **Average Runtime of Content**
   ```DAX
   Avg Runtime lc = AVERAGE('liocinema_db contents'[run_time]) / 60
   ```
   - Converts average runtime from minutes to hours.

11. **Total Watch Time**
    ```DAX
    Total watch time lc = SUM('liocinema_db content_consumption'[total_watch_time_mins])
    ```
    - Sums up all users' total watch time in minutes.

12. **Average Watch Time**
    ```DAX
    Avg watch time lc = AVERAGE('liocinema_db content_consumption'[total_watch_time_mins]) / 60
    ```
    - Converts average watch time from minutes to hours.

13. **Active Users**
    ```DAX
    Active users lc = COUNTROWS(FILTER('liocinema_db subscribers', 'liocinema_db subscribers'[last_active_date] = BLANK()))
    ```
    - Users are considered active if `last_active_date` is blank.

14. **Inactive Users**
    ```DAX
    Inactive users lc = COUNTROWS(FILTER('liocinema_db subscribers', 'liocinema_db subscribers'[last_active_date] <> BLANK()))
    ```
    - Users are inactive if `last_active_date` is not blank.

15. **Active Users %**
    ```DAX
    Active user % lc = DIVIDE([Active users lc], [Total users_lc], 0)
    ```
    - Percentage of active users.

16. **Inactive Users %**
    ```DAX
    Inactive users % lc = DIVIDE([Inactive users lc], [Total users_lc], 0)
    ```
    - Percentage of inactive users.

17. **User Share by Plan**
    ```DAX
    User Share by Plan lc = DIVIDE(
        [Total users_lc cm],
        CALCULATE([Total users_lc cm], ALLEXCEPT('liocinema_db subscribers', 'liocinema_db subscribers'[subscription_plan])),
        BLANK()
    )
    ```
    - Calculates the percentage of users in each subscription plan.

18. **Upgraded Users**
    ```DAX
    CALCULATE(
    DISTINCTCOUNT('liocinema_db subscribers'[user_id]), 
    NOT(ISBLANK('liocinema_db subscribers'[new_subscription_plan])) &&  -- Excluding blanks considering no change of plan happened
    'liocinema_db subscribers'[subscription_plan] <> 'liocinema_db subscribers'[new_subscription_plan] &&
    ('liocinema_db subscribers'[new_subscription_plan] = "Premium" ||
    ('liocinema_db subscribers'[subscription_plan] = "Basic" && 'liocinema_db subscribers'[new_subscription_plan] = "Premium"))
    )
    ```
    - Counts the number of distinct users who have upgraded their subscription plans. The logic ensures that the new_subscription_plan column is not blank (indicating a change) and that the old and new subscription plans are different. An upgrade occurs when a user moves from Free to Basic or Premium, or from Basic to Premium.
   
19. **Downgraded Users**
    ```DAX
    CALCULATE(
    DISTINCTCOUNT('liocinema_db subscribers'[user_id]), 
    NOT(ISBLANK('liocinema_db subscribers'[new_subscription_plan])) &&  -- Excluding blanks considering no change of plan happened
    'liocinema_db subscribers'[subscription_plan] <> 'liocinema_db subscribers'[new_subscription_plan] &&
    ('liocinema_db subscribers'[new_subscription_plan] = "Free" || 
     ('liocinema_db subscribers'[subscription_plan] = "Premium" && 'liocinema_db subscribers'[new_subscription_plan] = "Basic"))
    )
    ```
    - Counts the number of downgraded users. A downgrade occurs when a user moves from Premium to Basic or Free or from Basic to Free. The calculation excludes blanks in the new_subscription_plan column, as blanks indicate no change.
   
20. **Unchanged Users**
    ```DAX
    CALCULATE(
    DISTINCTCOUNT('liocinema_db subscribers'[user_id]), 
    ISBLANK('liocinema_db subscribers'[new_subscription_plan]) || 
    'liocinema_db subscribers'[subscription_plan] = 'liocinema_db subscribers'[new_subscription_plan]
    )

    ```
    - Counts users whose subscription plan remained unchanged. This includes users where the new_subscription_plan is blank or where the old and new subscription plan values are the same.
   
21. **Downgrade rate**
    ```DAX
    DIVIDE([Downgraded Users lc],[Total users_lc],0)
    ```
    - Calculates the percentage of users who have downgraded their subscription plan.
   
22. **Upgrade Rate**
    ```DAX
    DIVIDE([Upgraded Users lc],[Total users_lc],0)
    ```
    - Calculates the percentage of users who have upgraded their subscription plan.
   
23. **Users Monthly Growth Rate**
    ```DAX
    IF(
    ISFILTERED('Calendar'[Month]), -- Ensures a month is selected
    DIVIDE([Total users_lc cm] - [Total Users lc pm], [Total Users lc pm], BLANK()),
    "--"
    )

    ```
    -Calculates the net increase in users compared to the previous month.

### Revenue Measures

24. **Revenue**
    ```DAX
    Revenue lc = SUM('liocinema_db subscribers'[price_subscription_plan])
    ```
    - Calculates revenue generated on the platform.

---

## Jot Star

### Measures (Similar to Lio Cinema)

1. **Total Content Items**
2. **Total Users**
3. **Paid Users (Subscription Plan)**
4. **Paid Users (Subscription Plan & New Subscription Plan)**
5. **Paid Users (New Subscription Plan)**
6. **Paid Users % (Subscription Plan)**
7. **Paid Users % (Subscription Plan & New Subscription Plan)**
8. **Paid Users % (New Subscription Plan)**
9. **Average Runtime**
10. **Total Watch Time**
11. **Average Watch Time**
12. **Active Users**
13. **Inactive Users**
14. **Active Users %**
15. **Inactive Users %**
16. **Upgrade & Downgrade Rates**
17. **Revenue**
18. **User Share by Plan**
19. **Upgraded Users**
20. **Downgraded Users**
21. **Downgrade Rate**
22. **Upgrade Rate**
23. **Total Users (pervious month)**
24. **Users monthly growth rate**

---

## Other Measures

1. **Base Zero**
   ```DAX
   Base Zero = 0
   ```
   - Dynamic measure for modifying charts.

2. **Whole**
   ```DAX
   Whole = 1
   ```
   - Created for modifying chart appearance.

---

## Tables

### Dimension Tables:
1. City Tier
2. Age Group
3. Content
4. Device
5. Genre
6. Language

### Other Tables:
1. **Calendar Tables:** Subscription Date & Plan Renew Date
2. **Measure Tables:** LioCinema & JotStar
3. **Subscription Plan Tables:** LioCinema & JotStar

### Parameter:
- Used for switching between Language and Content Type when comparing across platforms.

---

## Columns Created in `jotstar_db_subscribers`:

1. **Upgrade Category** - Categorizes users as "No Change," "Downgrade," "Free to VIP," "Free to Premium," "VIP to Premium."
2. **New Subscription Plan Update** - Updates new subscription plan values.
3. **Revenue Calculation Column** -

   ```DAX
   Revenue =
   VAR lastdateconsider = DATE(2024,12,31)
   
   // Old subscription plan Price (Monthly)
   VAR sp = 
       SWITCH(
           'jotstar_db subscribers'[subscription_plan],
           "Premium", 359,
           "VIP", 159,
           0
       )
   
   // New subscription plan Price (Monthly)
   VAR nsp = 
       SWITCH(
           'jotstar_db subscribers'[new_subscription_plan_update],
           "Premium", 359,
           "VIP", 159,
           0
       )
   
   // Duration Calculation for Old Plan (Months)
   VAR d1 = 
       SWITCH(
           TRUE(), 
           ISBLANK('jotstar_db subscribers'[plan_change_date]) && ISBLANK('jotstar_db subscribers'[last_active_date]), 
               DATEDIFF('jotstar_db subscribers'[subscription_date], lastdateconsider, DAY),
           
           ISBLANK('jotstar_db subscribers'[plan_change_date]) && NOT(ISBLANK('jotstar_db subscribers'[last_active_date])), 
               DATEDIFF('jotstar_db subscribers'[subscription_date], 'jotstar_db subscribers'[last_active_date], DAY),
           
           NOT(ISBLANK('jotstar_db subscribers'[plan_change_date])) && NOT(ISBLANK('jotstar_db subscribers'[last_active_date])), 
               DATEDIFF('jotstar_db subscribers'[subscription_date], 'jotstar_db subscribers'[plan_change_date], DAY),
           
           NOT(ISBLANK('jotstar_db subscribers'[plan_change_date])) && ISBLANK('jotstar_db subscribers'[last_active_date]), 
               DATEDIFF('jotstar_db subscribers'[subscription_date], 'jotstar_db subscribers'[plan_change_date], DAY)
       )
   
   // Duration Calculation for New Plan (Months)
   VAR d2 = 
       SWITCH(
           TRUE(), 
           ISBLANK('jotstar_db subscribers'[plan_change_date]) && ISBLANK('jotstar_db subscribers'[last_active_date]), 
               0,
           
           ISBLANK('jotstar_db subscribers'[plan_change_date]) && NOT(ISBLANK('jotstar_db subscribers'[last_active_date])), 
               0,
           
           NOT(ISBLANK('jotstar_db subscribers'[plan_change_date])) && NOT(ISBLANK('jotstar_db subscribers'[last_active_date])), 
               DATEDIFF('jotstar_db subscribers'[plan_change_date], 'jotstar_db subscribers'[last_active_date], DAY),
           
           NOT(ISBLANK('jotstar_db subscribers'[plan_change_date])) && ISBLANK('jotstar_db subscribers'[last_active_date]), 
               DATEDIFF('jotstar_db subscribers'[plan_change_date], lastdateconsider, DAY)
       )
   
   RETURN 
       (d1/30 * sp) + (d2/30 * nsp)
   
   ```


