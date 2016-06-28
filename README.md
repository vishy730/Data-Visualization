# Data Visualization of Crops Yield from India over a period of 20 years from 1994-2014.

## Summary

   In this visualization we try to find out how different crops yield for a given period of time i.e., 1994 - 2014. The question is: were some crops just give more yield consistently over the years and were some crops fluctuate often in their yield?. Is that just a one time event or is it persistent over time? That could mean that so many factors were influencing the yields other than weather patterns. However, the dataset is limited just to the crops and their yield in tonnes over the years in India. Seconds thoughts could include that if a crop is consistently decreasing, we could find out more about the crop that why it is diminishing in our further analysis....etc. 

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

## Final Visualization:

![Minion](https://github.com/vishy730/Data-Visualization/blob/master/Capture2.PNG)

#### Observations: 

* Of all the crops, Coconut showed the steady increase in the yield followed by pulses.
* The most fluctuating yield was observed in two crops - Fruits and Vegetables.


### Future Work:

* ItemCode mapping should be done and breakdown of various itemcodes for a given Item.
* Summary Legend on top right of the graph showing Top 5 yields over the years.
