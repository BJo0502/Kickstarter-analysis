# Module 1: Kickstarter Challenge

## Overview of the Project:

The data visualizations provided below were created to display how Louise’s play, *Fever*, compared to similar initiatives that also sought fundraising support through Kickstarter campaigns. Louise is specifically interested in taking a closer look at campaign outcomes based on the launch date and funding goal variables. These visualizations help to explain how *Fever’s* near success of reaching the initial funding goal compares to other campaigns in the theater parent category and plays subcategory.

## Analysis:

In the Theater Outcomes vs Launch Date visualization, I first created a Pivot Table to ensure the correct variables and filters were set. I created a filter for the Parent Category and selected only the theater. This step ensures that when evaluating the *Fever* campaign, we are comparing it to like campaigns. Additionally, I created a filter for the year in which a campaign took place. To do this, I first needed to add a helper column to the raw Kickstarter dataset and use the YEAR() function to populate the cells. By adding this filter, Louise can explore the data further to see if theater campaigns were more or less successful from year-to-year. Next the outcomes field was added to both the Columns and Values sections and the Date Created was added to the Rows section in the Pivot Table. The Date Created field was an additional helper column added to the raw dataset which was populated using the following formula: =(((Launched_at/60)/60)/24)+DATE(1970,1,1). The “Launched_at” cell was left relative so that the formula could be dragged down to populate all the following rows of data. This formula identifies the date a campaign was launched and converts the unix timestamp to a human readable date format. I also reformatted the order of the outcome column in the Pivot Table so that the successful campaigns were listed first, followed by failed and canceled. Lastly, I adjusted the Date Conversion in the rows secition to display months rather than years since years is now a filter.

### The line chart below displays Theater Outcomes vs Launch Date

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/88041368/129758178-ba229867-652a-49a2-b18a-bd6550b9631a.png)


To visualize the Outcome Results Based on Goals, I grouped the goals into a range of values. Next I populated columns that showed the number of campaigns based on each outcome and their corresponding percentages based on total projects within each goal range. To populate the number of successful, failed and canceled projects for each goal range, I used the COUNTIFS function. The criteria in this function allowed me to specify the range of the goals considered, the outcome type, and the subcategory as plays. It is worth noting that no campaigns that were identified under the plays subcategory were canceled. To solve for the Total Projects within each goal range, I used the SUM function. Lastly, to populate the percentage of successful, failed and canceled outcomes I used the corresponding number field (previously populated utilizing the COUNTIFS function), divided by the Total Projects and multiplied by 100.

### The line chart below displays Outcomes Based on Goals

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/88041368/129758317-99dc50d3-7548-4c49-b5a6-afb44cf6d408.png)



## Challenges:

The ran into two challenges while working through the above analyses; I did not know how to populate the range criteria within the COUNTIFS function and I forgot to set the subcategory criteria to only include records for plays. When initially populating the COUNTIFS function for a range of values I was trying to use “AND” to capture values greater than a number but less than another number rather than listing each as a comma separated criteria. When I created the line graph, I noticed it did not look like the one provided as a reference in the project description. Fortunately, after rereading the directions I realized I needed to add an additional criterion to the COUNTIFS function to select only plays.

## Results

From the Theater Outcomes by Launch Date analysis, we can conclude that overall, most of the theater campaigns have been successful. The line graph clearly displays this and if we solve for the percentage of successful theater campaigns against the total theater campaigns (using the grand total row in the Pivot Table) we see that roughly 62% of all the total theater campaigns have been successful. From the line chart we can also determine that the ideal time of year to launch a successful campaign is from April through July. Alternatively, campaigns that launch in December only have about a 50% chance of being successful. Since we know that Louise’s campaign fell short of meeting her funding goals, and we also know that most of the other theater campaigns were successful, it would be helpful to know when Louise launched her campaign. If she launched her campaign during a time of the year when her chances of meeting her goal were less likely, it’s possible that this variable had a significant impact on her outcome.

In the Outcomes Based on Goals line chart, we dig deeper into the subcategory of plays within the parent theater category. Right away the absence of a line depicting the number of play campaigns canceled tells us that none of these campaigns were actually canceled; they were either successful or they failed. We can also conclude that if the goal was less than $15,000 it was more likely that a campaign would be successful. There does appear to be an exception when the goal is between $30,000 and $34,999. In fact, this goal range has the highest percentage of successful outcomes at 80%. Louise’s outcome could have also been impacted by the amount she set her goal at during the launch of the *Fever* campaign.

## Data Limitations

While the Kickstarter dataset allows us to provide some helpful insights to Louise, it also lacks some additional information that could potentially be useful to know. One example of the dataset’s shortcomings is that the subcategory of plays is not very specific. It doesn’t tell us enough about the types of plays that were successful or failed. For example, were comedies more successful than tragedies? The blurb field also does not specifically make mention of the types of plays, so we would have to conduct some additional research to create a new category that breaks out plays by type. Additionally, it would be helpful to drill down deeper into the actual location of a campaign when considering successful outcomes. While we know the country of a campaign, it would be interesting to see if certain cities are more successful than others. For example, New York city is well known for Broadway shows; however, it would be interesting to explore if grassroots campaigns can also be successful in this city. Perhaps less competition in cities with fewer arts programs would be more likely to gain appropriate funding.

## Additional Insights

There are certainly opportunities to ask additional questions of the Kickstarter dataset. A Pivot Table and accompanying chart that displays the average donation per goal range would be helpful to know for any of Louise’s future campaigns in the plays subcategory. By breaking the goal amount down into average per backer, she can be more deliberate about how she targets getting the word out to potential supporters. Would it be more helpful to have more backers that provide smaller amounts or fewer backers that provide larger amounts? It would also be interesting to consider the average length of time for a campaign in the plays subcategory. Maybe it would be worth considering a longer campaign so that there is more time for backers to support an initiative? Alternatively, if a campaign lasts too long, backers may not feel its urgent to support a campaign and be less likely to support right away, if at all.
