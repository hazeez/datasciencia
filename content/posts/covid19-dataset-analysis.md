---
title: "Analysis of COVID-19 dataset"
date: 2020-03-21T00:12:52+05:30
tags: [data-analytics, portfolio, excel]
---

> A personal account of my experience - the thought process, challenges and solution approach is documented in this post. The idea is to express that data analysis / science can be tricky and not everyone gets it right the first time. It takes multiple iterations to come up with something decent while navigating the challenges faced.

## Objective

The objective of this exercise is to analyze the COVID-19 cases and report the findings.

The data for the same can be downloaded from [Tableau Website](https://www.tableau.com/covid-19-coronavirus-data-resources).

The data source has approximately 114,000 rows of COVID-19 cases all over the world. The following data is provided - the date, country, region, the case status (active, confirmed, recovered, deaths) information and the location details.
	
> Note: This is a point in time exercise. The dataset is of Mar 21, 2020 and the analysis is based on this data. Any interpretations are based on this date and might not reflect the current trend.


## Tool to be used

The data will be analyzed via Microsoft Excel and insights will be provided. 

Why Excel? 

Because, at this point, I knew only Excel (40% I presume). But, I thought that it was enough to do this exercise. Actually speaking, the choice of the tool doesn't matter. What matters is the analysis!

I took stock of what all Excel stuff I knew and whether it would be sufficient to do my analysis!? I didn't know yet. 

The following features of Excel may be used to make analysis easier was my guess.

- pivot table
- basic functions
- graphs

In the retrospective, I was grossly wrong on my Excel skills and I had to do some learning along the way to achieve what I wanted. 

	
## Metrics

At the start of the analysis, I was not having a definitive list of what metrics I would be reporting on - as I was just having a raw dataset.

The possible things that came up rationally is to report on certain key metrics that are easy to report like

- Top 10 countries with most confirmed cases
- Top 10 countries with most deaths
- Top 10 countries with most recovered cases
- Time series analysis of the growth pattern across countries
- Geological location of cases concentrated

Time series data is the complex one here. Why complex? Anything with dates' - my understanding is that it can be complex. 

Geological location - well, I don't have much experience in plotting data on maps. But, apart from that, the rest is easy to report.

Will the analysis be interesting? Will I capture the essence of the dataset? Not sure yet!

My understanding is that data analysis does not have a definitive ending. What metrics to report on depends on the amount of time we have at hand and what metrics the business will be interested in.

If we think that way, the top three in the above list does not add much business value plus point 5 is just cosmetic. Time series analysis is the one the business will be much interested in as they can see the trend and can take decisions if such diseases spread next time. I presume China did this as they played along with the SARS playbook which they drafted when it hit China in 2003.

I didn't overthink at this point as to what metrics to report unless I look into the data and understand it.

I had to get the ball rolling as overthinking can lead to a thought-loop and I will end up where I have started.

So, I started with the first step - the data clean-up and understanding process. 
	
## Data challenges

### Data clean-ups

The first thing to notice was that the data needed a clean-up. The first column date had two different formats when imported into Excel. I don't know why this happens in Excel. 

Not a good start! Ugh! 

Upon Googling, I found that this is a known problem in Excel (for large datasets?). 

The first challenge - I have to bring it to a consistent format to present a meaningful analysis.
	
![](https://i.imgur.com/2Qq0kao.png)
	
I had to further see which of the two formats needed a clean-up. Upon applying the filter, I got to see that `mm/dd/yyyy` was not properly picked up and it needs clean-up.
	
![](https://i.imgur.com/tHVpOpa.png)
	
!!! Note "Date problem in Excel"
		
	Though the data in the Tableau website is correct, when opened locally in Excel, Excel might change the day to month and month to day.
		
	This would change the date value e.g. march 11, 2020 will change to November 03, 2020, as the day and month might get swapped.
		
	We have to correct the data before we start working on the data. The solution to the problem is documented [here](https://www.macroption.com/Excel-reverse-date/)

### Understanding the data

Understanding the data is critical - what data is captured in the spreadsheet and how to interpret it!?

First of all, the date column was not sorted. I had to sort on the date - Column A to set the date in ascending order. This would give me the ability to see how the total cases were captured. Is it incremental or cumulative cases reported per day? 

Then, I did a quick pivot table analysis to check the cases of a few countries; one being Afghanistan. 

Afghanistan - as per my analysis with a quick pivot table suggested that there were a total of 418 cases.

![](https://i.imgur.com/q7mh2od.png)

To understand if the above numbers were correct, I cross-verified with the coronavirus numbers published by [John Hopkins University's Corona Dashboard](https://coronavirus.jhu.edu/map.html)

What I found was that the total cases for Afghanistan was only 40! (see image below - as of date Mar 23, 2020)

![](https://i.imgur.com/JOPPnxR.png)
	
The data-set which I downloaded was also accurate but, my interpretation of the data was wrong.

The cases were captured by date and the latest date across any country was the cumulative total on that date. 

When I did a pivot table and computed by "Sum of total cases", I got a grossly wrong number. Instead, the total cases have to be set to "Max of total cases" in the pivot table to get the correct number.

I did that and I could see that the data was in-line with the data provided in the John Hopkins University website.

But there was one more problem!

### Manual tweaks

When I took the "Max of total cases", it would not work for countries like China, US, France, etc as they have multiple districts and province numbers reported separately in each row.

What do I mean?

Well, for countries like America, it had multiple rows - one for each State in the US like Arizona, Washington, New York, etc. But, for countries like India, Japan, etc there was just one row for the entire country.

So, if I take the China data and compute the data based on "Max of total cases", it would only report numbers from the Wuhan province as it had the most confirmed cases. For most of the countries like India, Japan etc, I had to go with the "Max of total cases" route and for other countries like China, the US etc, I had to compute based on "Sum of total cases".

This data pre-processing took hours as I didn't expect the pattern of data to change based on countries. At the end, I found it and manually tweaked the data. It was a boring process but I had to do and correct it.

**Lesson learned:** Always double check the data.

### Additional cleanups

Concerning data, one more clean up was necessary. The total number of cases were broken down into categories like "Confirmed", "Active", "Recovered" and "Deaths" and all these numbers were reported in "Rows". [See image below]

![](https://i.imgur.com/PEcYYpw.png)

What I need was - the data to be represented in columns (like the image below) so that aggregating the numbers would be easier. 

![](https://i.imgur.com/jdEVTCw.png)

To get it in this format, I had to do a pivot table on the raw data and for each country, I had to translate data in this format. I had to break this task into two days as the dataset had 168 countries and each country had approximately 80 rows of data. 

Once I had this data cleaned and prepared, I was ready to launch the analysis.

## Solution Approach

> ## Give me six hours to cut a tree and I will spend the first four to sharpen the axe
>― _Abraham Lincoln_

Anybody can cut a tree when enough time is given. But, the challenge is to cut a tree in six hours which not everyone can do. The approach has to be different.

My thought process at this point was - how can I efficiently analyze the data!? The dataset is huge; 110K rows which I had aggregated to 9700+ rows for 160+ countries.

In short, I thought how can I sharpen the axe so that I can cut down the tree in minimal time. I have a week to complete the analysis. 

I can take the traditional route and make one worksheet for each country and each sheet can have $n$ number of pivot tables and graphs which can be analyzed further.

I started with this approach and whenever I saved the file, it took almost 10 seconds to save. The reason behind is the master data, cleaned up data was all in one file.

I had to move the master data to another sheet to save some time plus size of the file itself. But, that didn't help much.

Since I had multiple sheets and multiple graphs, I had to scramble across sheets to find the required data and in the process, I got mad. Yeah! too much data can make you mad - at times. There has to be a better way!

What if I can create one master sheet and have it as a base template? When I change a country from a drop-down list, the dataset has to change and the graph should refresh automatically. Sounded better!

Well, there was a problem! 

I didn't know how to do it. I had never worked with Excel dynamic ranges or drop-down lists. I began my research and learned a few topics and watched some videos. (References at the end of this article.)

> ## And, when you want something, all the universe conspires in helping you to achieve it. 
> ― _Paulo Coelho_

One thing leads to another, that thing leads to another and finally, I learned the following functions and features in Excel that helped me to get it done.

#### Functions learnt
	
- MATCH
- INDEX
- OFFSET
- ADDRESS
- SMALL

#### Features learnt

- Using <KBD>F9</KBD> key in formula bar
- Name manager
- Array Formulas
- Maps in Excel
- Controls like text box, list box.
- Graph features like Markers
- Tweaks like
	- Highlighting a specific bar in a bar chart
	- Adding vertical lines to any chart to highlight a certain date

#### Extra stuff learnt

- Dashboards in Excel
- Preparing layouts in Powerpoint (Yes! Powerpoint) and bring that to Excel
- Design principles

All these topics were learnt _as and when it required_ in preparing the holy grail - the Excel dashboard. 

### First iteration

I prepared a time-series chart in a separate sheet to show the confirmed cases, active and recovered cases over time, plotted the map for the specific country (Excel makes it very easy), another time series to show the recovery % and death %, Next 10 countries in the list to show how the selected country is doing with respect to its counterparts, list countries based on their recovery and death percentage - who is doing good? and who is doing bad?

And yes! the final thing - Add a list of countries and make all the above charts dynamic. Woohoo!

The first iteration is the one below!

![](https://i.imgur.com/hRkxdUq.png)

Clicking each country refreshed the graph, highlighted the specific country in the Recovery % graph and the Death % graph (highlighted in Cyan and Red respectively in the above image).

I played around with it and saw what analysis I could get from it. Well! the basic analysis were there - what I needed!

> ## In three words, I can sum up everything I have learned about life: it goes on!
> ― _Robert Frost_
	
Like the quote said, life moved on and a curious question popped up. I wanted to narrow down to a particular period to see how many people were affected in a particular period. 

This would give me the ability to see how pre-lockdown and post-lockdown trends vary and answer whether the lockdown was effective or not!? 

Such questions cannot be answered by the current dashboard as it didn't have a provision to narrow down a time-period say e.g. From Feb 21st to Mar 7th. This sort of ability can help me breakdown the data into different time-periods like weeks, months and analyze.

### Second iteration

I knew the solution would be to give some sort of date range as input - a start date and an end date.

I had to introduce a couple of combo boxes and based on the _from date_ and _to date_, the results should also filter and give me numbers for that week.

I chose to keep the current graph but added one more graph to the bottom to show the trend and numbers for the period. With some combo boxes, `INDEX`, `MATCH`, `OFFSET` functions and the Name Manager feature, I was able to do it.

The second iteration of the dashboard looked like the one below.

![](https://i.imgur.com/heKBwDK.png)

I changed the layout to accommodate more graphs. `1` is the _From date_, `2` is the _To date_. Clicking each of these will change the graph `4` and `5` accordingly. Countries list `3` moved to the top. `6` is the numbers on the _From date_ and  _To date_ respectively. `7` and `8` represents Death % and Recovery %.

Not bad at all! I took it for a test and everything seems to be in place.

### Third iteration


> ## To improve is to change. To be perfect is to change often.
> ― _Sir Winston Churchill_ 
	
Again, I stumbled upon a thought. I am not doing this for myself. I am doing this for everyone who does not have the time to clean the data and do the analysis. 

Can I add a visual-cue to the graph to indicate the _From date_ and _To date_ so that the users know which window they are looking into? So, I decided to introduce a couple of vertical lines into the graph to show the dates. 

Also, I wanted to add a line to indicate when the first infected case was reported? This would give me an indication as to when the infection started and how much time the countries had to make decisions before the infections grew exponentially.

![](https://i.imgur.com/cdXhBbc.png)

I tested it and it worked fine. Now, I can find out when the infection started and can narrow down to the period when the first death occurred. I can then find (from Google) when the lockdown period was announced and can describe the trends before and after - and how much lead-time the countries had before going on lockdown and what they could have done differently to minimize the infection.

## Final result

This is how the Excel based COVID19 Dashboard looks like. Here is a gif that tells you how it looks like in action.

![](https://media.giphy.com/media/SUdASbhSLsVUmkNBrm/giphy.gif)


## What next?

So, I was happy with the result - not only because of what I could churn out but also I learnt so much in the process. It was time-consuming but, worth it!

Now you may ask where is my analysis!? 

Here is the generic analysis - the one that businesses would expect - one-liners mostly. Detailed analysis would make a separate post.

### Generic observation

- Every country had enough lead time for them from the day of the first infection to when the growth in infection started exponentially.
- From the samples studied like the US, Italy, Spain, France, etc, the death rates (not the number of deaths) have gone up - which is worrying. As of Mar 22, 2020, India's death rate was 2% but, it has gone upto 2.2% now (Mar 27, 2020)

### Western countries

- European countries like Italy, France, Spain, Germany all had infections within a 1 week window.
- Germany has managed better than the US and the United Kingdom despite having a large number of confirmed cases. Germany's death rate is less than 1%.
- Switzerland - a neighbor sharing borders with Italy was infected almost a month later than Italy.  On 25th Feb 2020, when Italy had almost 300+ confirmed cases, Switzerland had the first confirmed case reported. Still, It didn't introduce the lockdown till March 2nd week. It costed Switzerland with 6575 confirmed cases.
- The US is one of the worst mis-managed countries with 307 deaths and 17 recoveries despite having a well-established health care system. The death rate to the recovery rate is too high. This is due to bad decisions like undermining the seriousness of the situation, not practicing social-distancing, not enforcing lockdowns etc.

### Developing countries

- Most Middle-east countries have managed the virus much better than European countries despite having lesser resources. They have lesser death rate and good recovery rates when compared to European countries.
- Iran was affected most because of economic sanctions. With 8% of confirmed cases dead, it has closed the gap between the _active_ cases and _recovered_ cases with 37% recoveries - only next to China and Bahrain.
- Most developing countries have death rates above 5%. E.g Algeria at 11%, Indonesia, Bangladesh, Iran, Iraq at 8%, Mauritius, Ukraine, Jamaica, etc above 6%. This might be largely due to poor health-care infrastructure.

### African countries

- African countries are outliers (less number of cases so far) but, if they are affected, the death rates could be higher than other countries to as close as 20% due to poor health care infrastructure. At the time of analysis, the infection count is less but, once it starts, the fatality rate would be higher than other nations.

## Summary

This exercise was time consuming yet, rewarding. On the learning front, some key take-aways

- Data analysis comprises a lot of data-preparation activity (read that as 'nasty' work) which is about 60% to 80% but, by the time it is over, we may already get a feel of the data. It is boring work we have to live with. 
- Useful data (cleaned data) will give a lot of insights and there is no end to how much value we can churn from it. It is only a matter of time - we need to decide what is most important and what is not. We have to prioritize based on business objectives.
- Sharpening the axe (building right tools - in this case, a dashboard) is an important skill and if we do it faster, cutting the tree (analysis) will be a breeze. 
- Excel is a versatile tool. It may trick with its simplicity but, it provides so much for people who look into it deeply enough.
- Data science - in other words, means you have to keep learning new tools, techniques and assimilate whatever is thrown-upon on you faster.

### What does it have for others?

Well, you can download the COVID19 Excel dashboard (link below) and can come up with your analysis. That way, this is open-ended and gives you the opportunity to explore more and come up with analysis. In short, this is my version of the sharpened axe you can take and go for cutting the tree!

If you have any feedback on how this can be improved, let me know. Thanks for reading! 

Be socially responsible, practice social-distancing and stay safe!


#### References

- [John Hopkins University - Corona Website](https://coronavirus.jhu.edu/map.html)
- [COVID India Tracker Website](https://www.covid19india.org/)
- [Excel Dynamic Dropdown Video](https://youtu.be/22jcw5slQJk)
- [Excel Dashboard Tutorial](https://youtu.be/cKkXtyjleX4)

### Download Covid19 Dashboard

The Excel dashboard discussed in this post can be downloaded from the following link.

- [Excel - COVID19 Dashboard](https://github.com/hazeez/IDS13/raw/master/class06/COVID-19-Cases-Dashboard.xlsx)