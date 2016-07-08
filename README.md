# Is there any effect of deforestation and industrialization on Crops Yield over the last two decades?

## Summary

   What are the effects of Industrialization, Global Warming, Deforestation? The primary affected sector is agriculture and lets explore here what are those effects and whether commercial crops were affected or staple ones. After having a bit of analysis, we could see that effect was visible on fruits and vegetables espically but commercial crops were steadily picking up over the two decades. Lets go through to understand the effects better over the years.

## Design

### 1.Preparing the data:
checking for any NA values and removing such entries.
```
> timeuse<-read.csv("D:/udacity/project6/lesson2/crops_production_2.csv");
> timeusedf<-data.frame(timeuse);
> summary(timeusedf)
                                     Domain.Code     Domain        AreaCode    AreaName     ElementCode   ElementName           ItemName        Year     
                                           :   1        :   2   Min.   :100        :   2   Min.   :5419        :   2   Vegetables   :528   Min.   :1994  
 FAOSTAT Date: Tue Mar 22 05:10:23 CET 2016:   1   Crops:1934   1st Qu.:100   India:1934   1st Qu.:5419   Yield:1934   Fruits       :420   1st Qu.:1999  
 QC                                        :1934                Median :100                Median :5419                Coarse Grains:208   Median :2004  
                                                                Mean   :100                Mean   :5419                Dry Fruits   :162   Mean   :2004  
                                                                3rd Qu.:100                3rd Qu.:5419                Spices       :141   3rd Qu.:2009  
                                                                Max.   :100                Max.   :5419                Cereals      : 84   Max.   :2014  
                                                                NA's   :2                  NA's   :2                   (Other)      :393   NA's   :2     
     Value        Flag                  FlagD     
 Min.   :  1059     :   2                  :   2  
 1st Qu.:  9015   Fc:1934   Calculated data:1934  
 Median : 28915                                   
 Mean   : 71462                                   
 3rd Qu.:101294                                   
 Max.   :765328                                   
 NA's   :2
      
modifieddf<-na.omit(timeusedf)
write.csv(timeusedf,file = "crops_production.csv")     
```

After exploring the data, and trying out different charts, I thought to communicate in fancy way and used bubble chart/scatter plot for my initial draft and posted for feedback. I quickly realized that for Time series line chart is best and I got the same comments when I took feedback from members. So I choose to stick to the story rather than fancy presentation. 

Line chart simply communicates the data in better fashion espically when we are dealing with time series. I have taken the max values for each Item/product and displayed on hoverover of the points in the line chart. Item codes have different names which dataset didnt provide and to be considered for future development.

### Line Chart

| Visual Encoding | Variable |
|-----------------|----------|
| x-axis          | Year     |
| y-axis          | max count|
| color hue       | Item Name|


Bar chart communicates better when we are comparing which crop is yielding more in a given year. I have taken the max values for each Item/product and displayed on hoverover of the points in the line chart. Item codes have different names which dataset didnt provide and to be considered for future development.

### Layout and Narrative

Layout is thought of communicating the trends of different crops. The idea is to narrate the trends of production yield in India over the period of 20 years. The initial design before feedback shows the trends in very cluttered way.

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture.JPG)

##### Feedback 1.
>  Hi Vishy, nice visualization. I am missing some context to fully understand the plot, maybe you can add some text? What is the x-axes (no label)? I can only see it with mouseOver event. What  the unit of value of crop production? The legend of the colours is not fully readable to me (letters cut off). I also think a line graph is better for time-series. good luck!

##### Feedback 2.
> I would say that the data are incomplete, as all data points are much lower than the previous years. Remember that for your final project, your visualization should be more explanatory than exploratory (your visualization should have a clear finding and focus on that). So, maybe you could include some text to help users get the story you are trying to convey.

##### Feedback 3.
> Perhaps when you click one of those crops, the graph should have a change of scale. Perhaps log, or a cut in the scale.

Considering above all the feedback points, I have modified the graph from bubble chart to line chart and applied aggregateMax function over ItemCode and showed it, on the hoverover of the points, instead of total count of the Yield per year. Also changed the title of y-axis.



Considering the feedback from the reviewer, I have created a story board and thought that bar chart would be apt for this visualization and modified the same.

### Bar Chart

| Visual Encoding | Variable |
|-----------------|----------|
| x-axis          | Item Name|
| y-axis          | max count|
| color hue       | Year     |

## Final Visualization - Iteration -1:

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture1.JPG)

## Working Example

http://bl.ocks.org/vishy730/2103dcf7f20ff086bde3400f58a3d1e2

In the above example we could see the distribution of various crops over the years and its a bit harder to identify the trends from it. However, we could observe a couple of things such as pulses and Lentils were more or less the same or in other words, the production is constant with some variance here and there till El Nino effect hit harder in 2014. So we have moved over a more sophisticated chart to understand the trends better.

## Final Visualization - Iteration -2:

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture2.PNG)

## Working Example

http://bl.ocks.org/vishy730/58dcc8f664c2eb73da90837cece47b4d

In this version we could see that chart is not cluttered. However, it was again difficult to draw the conclusion of various crop yields. Still we can observe that Fruits and vegetables were the most fluctuating crops in terms of yield. So can we conclude that fruit and vegetable crops were badly affected? In order to confirm we wanted to show the trends of all the crops across the years for better understanding. So we have introduced trend graphs in next iteration.

## Final Visualization - Iteration -3:

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture_3.PNG)

## Working example.

http://bl.ocks.org/vishy730/42beef5005b2010401ed895002a58992

In this version, introduced the trend for each crop on hover over of each crop. Have used crops for x-axis as I wanted to show different categories. The animation for years has given so that one can see the yield of crops over the years automatically. The hover over graph tells us the overall trend for a given crop over the years. Here I could find that coconuts had steady growth in yield and Fruits had very much turbulent down trend. However, by looking at the chart itself we could not deduct anything better apart from knowing the trend of each crop on hover over. So we thought of grouping various crops based on color and show the trends.

## Final Visualization - Iteration -4:

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture_5.PNG)

## Working example.

http://bl.ocks.org/vishy730/b65bb7d42a4dc61b88fd666249cd79a9

In this version, commercial crops such as Jute, Cotton, Tobacco were grouped and assiged a color Blue. The interesting crop Coconuts were steadily increasing over the years was given Red color and the diminishing trend of Fruits was given Green. The primary colors RBG were choosen so that they are catchy to eye-ball. Now by looking at the chart one could easily understand the trend of commerical crops were increased over the years and the coconut is the real winner since 2 decades in terms of production. So the three trends were highliighted in the chart for better understanding and conveying a story. Also the year 2014 was hit severly by El nino effect and was visible clearly in the chart. 

#### Observations: 

* Of all the crops, Coconut showed the steady increase in the yield followed by pulses.
* The most fluctuating yield was observed in two crops - Fruits and Vegetables.


### Future Work:

* ItemCode mapping should be done and breakdown of various itemcodes for a given Item.
* Summary Legend on top right of the graph showing Top 5 yields over the years.
