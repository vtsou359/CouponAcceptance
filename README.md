# Coupon Acceptance EDA - Practical Application
Advanced Data Analysis Project

* For the notebook click [here](https://github.com/vtsou359/CouponAcceptance/blob/main/Coupon_Acceptance_EDA.ipynb)


## Description of the Dataset

### Context

Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. Would you accept that coupon and take a short detour to the restaraunt? Would you accept the coupon but use it on a sunbsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaraunt? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?
Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

### Overview
The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

### [Data](https://archive.ics.uci.edu/dataset/603/in+vehicle+coupon+recommendation)
This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’. There are five different types of coupons -- less expensive restaurants (under $20), coffee houses, carry out & take away, bar, and more expensive restaurants ($20 - $50).

### Data Description
Keep in mind that these values mentioned below are average values.
The attributes of this data set include:

#### User attributes
- Gender: male, female
- Age: below 21, 21 to 25, 26 to 30, etc.
- Marital Status: single, married partner, unmarried partner, or widowed
- Number of children: 0, 1, or more than 1
- Education: high school, bachelors degree, associates degree, or graduate degree
- Occupation: architecture & engineering, business & financial, etc.
- Annual income: less than $12500, $12500 - $24999, $25000 - $37499, etc.
- Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
- Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
- Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
- Number of times that he/she eats at a restaurant with average expense less than $20 per person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
- Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

#### Contextual attributes
- Driving destination: home, work, or no urgent destination
- Location of user, coupon and destination: we provide a map to show the geographical location of the user, destination, and the venue, and we mark the distance between each two places with time of driving. The user can see whether the venue is in the same direction as the destination.
- Weather: sunny, rainy, or snowy
- Temperature: 30F, 55F, or 80F
- Time: 10AM, 2PM, or 6PM
- Passenger: alone, partner, kid(s), or friend(s)

#### Coupon attributes
- time before it expires: 2 hours or one day



## Data Quality checks, Data Cleansing, Data Transformations and initial Data Analysis

#### The data frame contains:
- 12684 rows in the dataset
- 26 features in the dataset

#### The data were cleaned appropriately:
The rows that contained duplicates (74 rows) were dropped. 
The rows that contained missing values (603 rows) were dropped.
The feature/column car was dropped as it was problematic.

#### Transformations of values were implemented in the following features:
- destination
- passenger
- weather
- time
- gender
- age
- maritalStatus
- expiration
- education
- income
- Bar
- CoffeeHouse
- CarryAway
- RestaurantLessThan20
- Restaurant20To50

For example, the Bar, CoffeeHouse, CarryAway, RestaurantLessThan20 and Restaurant20To50 columns were transformed as:
- never: 0
- less1: 1
- 1-3: 2
- 4-8: 3
- gt8: 4

### Data Analysis:
- Of the total observations, 57% of the coupons were accepted by the user.
- The coupon type with the highest count of coupons is Coffee House, followed by Restaurants(<20) ( Restaurants with average expense less than 20 $ per person)
- The coupon types with the highest counts of accepted coupon are both Coffee House and Restaurants(<20)
- Most observations had a temperature of 80.

  ![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot1.jpg)

  ![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot2.jpg)

  ![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot3.jpg)

## Data Analysis Results for Coupons of type Bar:
In relation to total coupons, only 6.5% of Bar-type coupons were accepted. In relation to total accepted coupons, the acceptance grows to 11.5%

![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot4.jpg)

![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot5.jpg)


#### In addition, some groups were created to investigate further the acceptance rates of Bar-type coupons. The groups are demonstrated below:
- Drivers who went to a bar 3 or fewer times a month
- Drivers who went to a bar 4 or more times a month
- Drivers who go to a bar more than once a month and are over the age of 25
- Drivers who go to bars more than once a month and had passengers who were not a kid and had occupations other than farming, fishing, or forestry
- Drivers who go to bars more than once a month, had passengers that were not a kid and were not widowed
- Drivers who go to bars more than once a month and are under the age of 30
- Drivers who go to cheap restaurants more than 4 times a month and earn less than 50K.
<sub> * Note: The analysis was conducted in relation to the total accepted Bar-type coupons. * <sub>

![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot8.jpg)

The group with the most significant acceptance rate is the drivers who went to a bar 3 or fewer times a month. This insight led to further analysis of the visit frequency in Accepted Bar-type coupons.

#### Some additional insights:
- Drivers who visit a bar more than once a month tend to accept the bar-type coupon. People who do not visit or visit a bar less than one time per month tend not to accept the bar-type coupon. To further investigate it, I will analyse how the time, passenger and destination affect the behaviour of the user.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot9.jpg)
- There is a slightly bigger frequency of accepted coupons for people who go to Bars 1 to 3 times per month in the morning hours (07:00, 10:00). In the afternoon (14:00), people who tend to accept bar-type coupons go to a bar less than once per month. The same pattern is noticed for the night hours.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot10.jpg)
- Drivers who go to their Home and tend to visit a bar less than once per month have a higher frequency of accepted coupons than drivers who go to their Home and have other visit frequencies to a bar.
- In addition, drivers with no urgent destination, whose bar visit frequencies are less than once per month and one to three visits per month, tend to have a high frequency of accepted coupons.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot11.jpg)
- Drivers alone in the car whose bar visit frequency is less than once per month or one to three times, have a higher frequency of accepted coupons.
- Drivers with friends in the car whose bar visit frequency is one to three times have a higher frequency of accepted coupons.
- Drivers with their partner in the car whose bar visit frequency is less than once per month have a higher frequency of accepted coupons.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot12.jpg)


## Data Analysis Results for Coupons of type Restaurant (<20):

- The proportion of the restaurants with an average expense of less than 20 $ coupons that were accepted (in relation to total Coupons): 15.64%
- The proportion of the restaurants with an average expense of less than 20 $ coupons that were accepted (in relation to total Accepted Coupons): 27.52%
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot13.jpg)

#### Additional insights - Investigating the variables of temperature and time subjected to drivers' acceptance behaviour (in relation to accepted coupons):
- It seems that more people accept the coupons in higher temperatures (80).
- Also, on hot days, the time with the most significant count of accepted coupons for cheap restaurants is 18:00.
- For the days when the temperature is 55, the highest counts are in the morning (07:00) and at 14:00.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot14.jpg)


#### Additional insights - Investigating the variables of passenger and time subjected to drivers' acceptance behaviour (accepted coupons):
- Users who are Alone or with Friends have higher frequencies of accepted coupons for cheap restaurants.
- In particular, users who drive Alone have a high frequency of accepted coupons in the early morning hours (07:00) 
- In addition, users who drive with Friends have a high frequency of accepted coupons for 18:00.
- Both of the above classes/groups also have a high frequency of accepted coupons at 14:00.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot15.jpg)

#### Additional insights - Investigating the variables of passenger and restaurant visit frequency (Restaurant(<20) subjected to drivers' acceptance behaviour (accepted coupons)):
- Users tend to accept the restaurant coupons when their restaurant visit frequency is 1-3 times, followed by 4-8 times.
![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot16.jpg)




## Next steps and Recommendations
This dataset is analysed and is ready to be inserted into a predictive model. Of course, more sophisticated data transformations could be implemented in order to make it even more "understandable" by an ML model.

According to the analysis conducted, the features that should be used as inputs to an ML model are:    
- The Bar and Restaurant(<20) visit frequency
- The Temperature
- The time of the day the coupon was sent 
- The destination
- And probably the passenger type.

To additionally validate the decision to choose the above feature, further analysis should be conducted between other features such as: Occupation, type of coupon and visit frequency in expensive restaurants. Also, an analysis of income and visit frequencies in various places could be conducted.




