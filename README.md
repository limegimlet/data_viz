# Visualizing major-league baseball stats with dimple.js

Course files & final project for the Udacity Data Visualization, part of the Data Analyst nanodegree.

## Summary

This plot highlights the difference in average homeruns and batting averages for right-, left-, and ambidextrous major-league baseball players, without any clear correlation to height or weight. It uses the dimple.js charting library.

## Design

**Plot type: bubble chart** 
* Since there were major differences for 2 different variables (homeruns and batting average), the plotting on an x-y axis most clearly shows each group's relative position. 
* To further emphasize this difference, the size of each group's bubble will be increase in proportion to their homerun and batting average.
* Lastly, a bubble surrounded by whitespace conveys the sport of baseball far more than, say, bars rising up from the x-axis.

**Colour scheme: black and white**
* conveys pen & ink which again conveys the feeling baseball more than the muted pastels ubiquitous to corporate KPI dashboards.
* use cross-hatching to denote different groups: can use direction of cross-hatching to reinforce left vs right vs both.
* Inspiration is this [plot](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_bars_sketchy)

**Axes: standardized around a mean of 0**
* a standardized axes allows the same axes to compare different pairs of variables. Since I'd like to allow users to toggle between a plot of `homeruns` vs `batting average` and `height` vs `weight`, having common axes allows the user to focus only on the positional changes of bubbles.
* Not everyone is familiar with what is a good homerun score and batting average. By showing instead standard deviations above & below the league means, viewers can better understand how each group fared compared to the league as a whole.

**Animation**
* the user can click to comparing the other two numeric variables, height and weight, where there is nearly no difference between right- and left-handed players. 
* inspriration is this [plot](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control). 

## Evolution of prototypes


## Feedback

Summary:

Evolution of feedback

## v1

http://bl.ocks.org/limegimlet/9a3ffd08e82fa35f878717b939a1cf08

Dec 20 2018 - Feedback from Karsten, a director for analytics with SAP.

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_karsten_dec20.png)

### v2

Changes:

* Updated .csv file to make values more explicit.
  * `hr` => `homeruns`
  * `avg` => `batting avg`
  * `B` => `Both`

http://bl.ocks.org/limegimlet/2e635b97f6e405aa8e4968f0d878d46d

Dec 21 2018 - Feedback from Paula, Director, Learning & Knowledge Management at Vision Critical.

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_paula_dec21.png)


### v3

Changes:
* Increased duration time for frames: `story.FrameDuration=4000;`
* Hid the y-axis

http://bl.ocks.org/limegimlet/5159b4a9c7fe20814f19217a6dccedad

Dec ??? 2018 - Feedback from 
* Shoko, Visual Artist / Writer / Translator & 
* Kinga

#### Shoko
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_shoko_dec24.png)

#### Kinga
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_kinga_dec24.png)
  
## Resources

_list any sources you consulted to create your visualization_


