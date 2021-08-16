# tableau-citibike

https://public.tableau.com/app/profile/james.gonzales



Tableau CitiBike: January 2020 - February 2020
Goal
Analyze CitiBike data between January and August 2019 for trends and visualize them using Tableau Public. View the Tableau Public workbook here (it may take a moment to load).

Data Cleaning
Before doing any visualizations, I first used Python and the Pandas library to clean the data. In a Jupyter Notebook, I concatenated monthly data files into one, and then dropped rows where the trip duration was under 90 seconds and the starting and ending stations were the same. This was done to weed out any instances of a faulty bike.

Then, trip duration was converted from seconds to minutes, which is personally easier to understand at first glance, and all trips over 24 hours (1440 minutes) dropped. Under CitiBike’s current pricing model, bikes can be used an unlimited amount of times (under the day passes and subscriptions) but in 30- or 45-minute intervals. Trips longer than that, are charged an extra $2.50 or $4.00 every 15 minutes. Therefore, all bikes that were not docked for over 24-hours were most likely stolen, and not legitimate rides. This was still a conservative assumption, as bike rides up to 24 hours would still cost the user between $232.50 and $376.

Next, I converted the gender column (which was originally numerically coded) into strings using a list comprehension, and added an extra column for ride id to uniquely identify each ride. Then, I calculated the distance for each trip, and the ages of each rider. Finally, I dropped all rows where riders were above the age of 90, assuming these were fake ages (some riders even gave ages over 130), and divided the riders into age bins. Like trip duration, I again made a conservative estimate, as it is unlikely that users in their 80s would be riding bikes in a large city.

In a separate notebook, I reshaped the cleaned data. Originally, each row represented one ride, with the starting and ending information in one row. Because I wanted to visualization each bike path, I need to plot two sets of coordinates at the same time. So, I divided the data so that the starting information and ending information would be in separate rows. Though visualizations were made with this data, it was not included in the final analysis.

Analysis
My analysis focused on user types (customer or subscriber) and gender (male, female, unknown). Though annual subscribers make up over 90% of total riders, customers (1-day and 3-day rentals) have a higher growth rate (1718%) than subscribers (113%). This could signal a growing interest in short-term rentals for users who want to experience the CitiBike product without being tied down for a whole year, or perhaps even a growing tourist market.

![image](https://user-images.githubusercontent.com/80234800/129581106-c998d002-d5b8-449b-a943-0a8fc722fdcb.png)

