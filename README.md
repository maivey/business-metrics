# Business Metrics


## Prerequisites
Both scripts requires imports of the following:
```python
import pandas as pd
import datetime as dt
import matplotlib.pyplot as plt
import seaborn as sns
```

## Summary
In most — if not all — institutions, management keeps track of the overall health of the business through the result of measurements called **metrics**. A ubiquitous and familiar example of a metric is revenue. In retail, a very popular metric is the [average order value](https://www.optimizely.com/optimization-glossary/average-order-value/) ; and in subscription-based products, churn rate is crucial.

Metrics are also important in other contexts, and the same principles apply. Examples of metrics that are followed by governments are GDP, inflation, and unemployment rate.

![](images/Unemployment.png)

Metrics are observed across time. Metrics are calculated separately at specific points in time, but are understood in a chronological context.

Common time frames in which to calculate metrics are days, weeks, or months. Which time frame to use depends on factors like importance, data availability, and how dynamic the metric is.

----- 
A good metric should have the following characteristics:

- **Accurate**

    It should go without saying that metrics should be accurate. Remember how, in the last mission ,we abandoned the estimation of the impact of the project because we couldn't properly measure it? By the same token, if a concept can't be adequately measured, then it shouldn't be a metric.

- **Simple and intelligible**

    Metrics are meant to be read and understood at a glance. Metrics are often presented in the context of a dashboard or report containing other metrics. There is much to read and understand, so it should be easy to read each of the dashboard's components. Think of metrics as the headline to a story.

    Because metrics are often divulged to broad audiences, they should be targeted to a common denominator.

- **Easy to drill down into**

  Metrics are meant to monitor how a business is doing. Sometimes they will reveal that something is going exceptionally well, or exceptionally bad. In either case we will be interested in knowing what factors contributed to the change in the metric. In other words, metrics are headlines, you need to be able to read the story.

  Since metrics typically are comprised of components (for example, profits can be seen has having two components: revenue and costs), we need to be able to drill down into them to understand what the change is attributed to.

- **Actionable**

  The point of measuring the health of the business is not just so we know if things are going well or not. The goal is to act on things if they're not going in the direction we want. For this reason, a good metric needs to be actionable.

  For example, it's known that weather has an impact on sales in brick-and-mortar stores, but we can't change the weather. A better option — and one we can act on — would be to measure the relevancy of our products based on the weather.

- **Dynamic**

  Metrics need to be dynamic, they need to change over time. This characteristic is somewhat related to the above, but merits some distinction.

  Many companies rent their offices instead of buying them. How much companies pay on leases is something that can potentially be acted on, in this sense it is actionable. However, since leases are legal contracts with relatively extended periods of time, this metric shouldn't be tracked — it's not dynamic enough.

- **Standardized**

  The broader the reach of a metric (in terms of its audience), the more the metric's elementary components need to be standardized, so that everyone sees the same thing. Not doing this causes inconsistency and misinformation, potentially resulting in unwanted outcomes.

  To give a couple of examples:

  - Should Amazon count a sale as such the moment the customer places the order? When the payment goes through? When the order leaves the warehouse? When it is delivered? Even something as simple as the concept of sale can be ambiguous.

  - In [supply chain management](https://en.wikipedia.org/wiki/Supply_chain_management), **lead time** is defined as "the amount of time that passes from the start of a process until its conclusion."

    Piggybacking from the previous example, should the lead time go up to the point where the order leaves the warehouse or until the customer receives it? Given that Amazon outsources the deliveries to companies like UPS, they don't have much control over what happens once the order is "on the road." However, from a customer satisfaction perspective, how long a customer takes to receive the order is definitely very relevant.

  Conflicting definitions should be resolved when a metric is monitored by many people in the company.


- **Business oriented**

  A metric should be relevant for the business. Here at Dataquest, we could potentially track how many times students use the character `a` in their answers. But it's unlikely to have any impact on how well they learn.

  Metrics need to be adjusted to the current needs of the business. Take, for instance, Netflix. They possibly tracked how much business they were losing to piracy. When streaming became easily available and relatively cheap, piracy stopped being a serious issue and there (possibly) was no need to track it anymore.
  
----------
## 1. Customer Churn

### Scenario:
You purchased your local gym from its previous owners. It was a great deal as their mismanagement led the owners to decide that the business wasn't profitable; you as a customer and entrepreneur were able to see the unfulfilled potential.

In January of 2013, the transaction was complete and you immediately took the opportunity to make a New Year's Resolution promo where people could sign up for the whole year and pay \\$500 instead of \\$50 per month. You also renamed the gym as Muscle Labs — not only are you fit, you also are a creative genius.

You decided to use the traditional subscription model used in gyms where customers pay an installment per month to access the gym. A customer churns when they elect not to pay the installment — this makes our life easier in implementing the concept for churn.

### Dataset
Here's the data dictionary:

- `id`: The subscription ID; a customer can appear multiple times in this dataset by virtue of having multiple subscriptions instead of a continuous one
- `customer_id`: The customer's ID
- `end_date`: The actual (if in the past) or estimated (if in the future) end date of the subscription
- `start_date`: The subscription start date
- `subscription_period`: Specifies whether it is a monthly or annual subscription
- `price`: The price

It is now December 2014, and you just finished one of Dataquest's tracks. You decide to put your knowledge to use and track the monthly churn rate from before you owned the gym up to last month (November 2014).

### Calculation
The churn rate is calculated as follows:

![equation](https://latex.codecogs.com/gif.latex?%5Cfrac%7B%5Ctext%7BNumber%20of%20Churned%20Customers%7D%7D%7B%5Ctext%7BNumber%20of%20Total%20Customers%7D%7D)



Where number of total customers is calculated by the number of customers at the begining of the time period. Specifically, given a month ym, count the number of subscriptions where start_date comes before the first day of ym, and where end_date is after the last day of the previous month (which is to say that the end_date is greater than or equal to the first day of ym).

----------
## 2. NPS (in progress)
Net Promoter Score, more commonly known as NPS, is a customer success metric that quantifies customer satisfaction.

Customers who pick:
- Anything from 0 through 6 are called detractors;
- 7 or 8 are called passives;
- 9 or 10 are called promoters;

By proxy each of these categories are gauged as follows:
- Detractors: Unhappy customers who share their negative experience with the product or company; they may actively spread negative feedback.
- Passives: Customers who may be pleased with the product, but aren't actively promoting it and will quickly turn to the competition if a better opportunity presents itself.
- Promoters: Extremely satisfied customers who will act as brand ambassadors.

NPS is then calculated as the percentage of promoters minus the percentage of detractors.

The jupyter notebook `NPS.ipynb` computes the net promoter score using a dataset that has three columns:

- `event_date`: The date and time in which customers completed the survey
- `user_id`: A customer identifier
- `score`: Their answer to the question featured above

The NPS is tracked month by month.


### References
This dataset was obtained by DataQuest.io's Data Analysis for Business course.
