# Coupon Acceptance EDA - Practical Application
UC Berkeley Professional Certificate in ML and AI

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



## Data Preparation for the Analysis

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

#### Insights:
- Of the total observations, 57% of the coupons were accepted by the user.
- The coupon type with the highest count of coupons is Coffee House, followed by Restaurants(<20) ( Restaurants with average expense less than 20 $ per person)
- The coupon types with the highest counts of accepted coupon are both Coffee House and Restaurants(<20)
- Most observations had a temperature of 80.

  ![Alt text](https://github.com/vtsou359/CouponAcceptance/blob/main/plots/Plot1.png)





