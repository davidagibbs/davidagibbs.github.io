---
layout: default
---


## *Transportation Cost Forecasting Project*

### The Concept

This page is an overview of assignment in my OM621 Advanced Visual Analytics class. The problem set out for this project is that invoices for shipments are often delayed such that a shipment can go out and the invoice would arrive in an unknown amount of time.

It could potentially take 2 days or 2 weeks or 2 months to receive the actual invoice. This created a problem because during the time that the invoice had not yet been received the company would not know their actual shipping costs so they wouldn't have accurate cost data to use when budgetting for upcoming periods.

A complicating issue the company has is that multiple divisions of the company make internal and external shipments with different carriers as they see fit. This illustrates the need the company has to budget at a division level or perhaps at a finer detailed level within each division and not just at a company level.

### My proposal

My proposal for the company is that they should use FedEx for all of their shipments. The reason is that a company like FedEx can handle large and small shipments domestically and internationally so they can support all of their shipping needs
The benefit of this would be 
 - to simplify their shipping processes since all divisions would have the same types of paperwork
 - The process for creating and managing shipments would be consistent
 - costs would be more consistent and predictable because all shipments would go through one carrier
 - FedEx has an API that the company could use to create a database of all of their shipping information including cost estimates that are created at the time that a shipment is made

These shipping estimates would not be exact because different fees and costs could change during the shipment that would affect the actual cost but the estimates would be accurate enough that they could be used for budgeting purposes. This would mean that the company would have a database of near real-time shipping costs and this would negate the issue of needing to wait for an actual invoice before being able to budget for future time periods.

Further, FedEx can issue subaccount numbers that could be dividion specific so that shipping information would be tracked by division in the shipment records. So while this would be a large project to change over to a single carrier it would simplify their shipping processes, create economies of scale that would reduce shipping costs, and eliminate the need to wait for invoices before budgeting.

### Unfortunately... 

Unfortunately my hypothetical company did not accept this recommendation and preferred to use their partial records to forecast future transportation costs as a way to budget without having received the most recent invoices.

### The process

This meant the project involved cleaning their records in python and finding patterns in their data using visualizations to better understand what factors were involved in making a shipment's invoice more delayed. This led to the discovery that because final invoices are only sent after a shipment is delivered, shipments with longer transit times had longer delays in receiving their invoices.

These shipments with longer transit times were large container load and partial container load shipments that also had high dollar values. This meant that in terms of dollars, a significant portion of their invoices were delayed two to three months.

Within the past invoices there was also seasonality which could be used to create a forecast using the actual invoices they had with a seasonal trend after removing the most recent three months from the data used for forecasting since it is known that a significant amount of invoices were missing within that timeframe, making the most recent month's records too low to be representative of future trends.

### The results

These findings were then presented in a Power BI dashboard including visuals showing the relationships between the amount of delay and the transportation mode, the value of the total shipments made by region they were shipped from, and a final forecast.