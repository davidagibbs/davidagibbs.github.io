---
layout: default
---


## *Safety Stock Calculation Project*

### The Concept

This page is an overview of assignment in my OM620 Tools and Technology for Business Analytics class. This project involved taking a dataset and cleaning and transforming it to produce a subset of data that could be used to calculate individual safety stock levels for a series of finished good items in that data set.

This process involved standardizing column headings and creating a subset of the data that only included the particular make to stock finished goods that we wanted to focus on. Next we created new columns that had calculated values for each SKU which had calculated values for minimum order quantity, maximum order quantity, standard deviation of order quantity and so on so that we could later use the standard deviations to calculate safety stock values.

In order to get closer to finding safety stocks we first needed to find the z-score values for the service levels we wanted to consider. Using a function from scipy.stats we found the z-score values we needed.

Now that we had the z-score value, standard deviation quantity, and the lead time for each SKU we could calulate safety stock quantities for each SKU using the safety stock formula

    SS = Z-score × Standard Deviation of Demand × Square Root of Lead Time

The result was a table of different safety stock values per SKU with multiple options based on different potential service levels the safety stock would support. This is where we ended our last assignment but I realize now that this isn't actually correct.


### The Next Steps

In the process of teasing out the data that we needed from the dataset for this safety stock calculation we used Order Quantity as the basis of a lot of those calculations. Order Quantity isn't actually relevant to what we are trying to do, we should be summing the order quantities by time in order to find the average demand per day because it is being used in a caluculation with lead time which is in days.

This became apparent when I reviewed the order data in Excel and saw that there are many orders for each SKU in a short time period. For example the SKU 0019425F has calculated safety stock values based on the service levels 75%, 90%, and 95% as follows 71, 134, 171. The amounts made sense because we were looking at the individual orders. The average size of an order is small and the standard deviation is relatively small so when combined with the 28 day lead time for this SKU these values seemed right.

Since safety stock is intended to cover variation in demand over **a period of time** we can't use the individual order quantities because they are not over a period of time. When looking in Excel I saw that for this SKU 0019425F there are orders almost every day and in some cases multiple orders per day.

Looking at January 2023 as an example the total order quantity for that month for this one SKU was 4,468. In fact over the 2 year period of the data we have the total order quantity was 120,347 units. If we were to just take that total and divide it by days we would find they are using on average about 165 units per day. In light of that and the fact that the lead time is 28 days, holding a safety stock of 171 units suddenly seems a bit low.

In order to correct this we would need do some real math or just use this overly simplistic calculation of total demand over two years divided by however many days that is to find a rough quantity per day. We could then use that instead of the order quantity in all the calculations we did and the result should be that the standard deviation value we use would be based on daily demand just like the lead time quantity is based on days. Ideally this would give us much larger safety stock values that would be comparable to their demand over the lead time.