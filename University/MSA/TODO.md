Implement 5 triggers

##### 1. User activity
Track users step count
##### 2. Mealtimes
Notify user at configurable mealtimes (Breakfast, Lunch, Dinner)
1. Have drop down menus for each mealtime in composable
2. Have a viewmodel to handle logic
3. Create a workmanager to notify the user at specified times to prompt them to eat
4. Customise notification 
##### 3. Encouragement
Notify user encouraging message when doing well 
1. Create a workmanager to track user progress from Hydration and 5/day DBs
2. if 2/5 for either notify("You are almost half way with your cups of water/portions of fruitVeg"). 
3. If 4/5 ("Well done! Just one more and you have reached your target!")
##### 4. Hydration
1. ~~Allow user to log cups of water~~
2. Move UI to separate Screen composable
3. Link totals with data layer
##### 5. 5-a-day
1. ~~Allow user to log portions of veg/fruit consumed~~
2. Move UI to separate Screen composable
3. Link totals with data layer

##### ALT. Recommend healthy meals from database ( could combine well with other trigger)

