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
* 4 out of 4 clearly understood the overall message. 
* However, only 1 out of 4 liked the animation. The other 3 were puzzled why it couldn't be static.
* 1 person didn't understand that bubble size represented group size. 
* Surprsingly (to me), only 1 person complained about the lag time after pressing "Play".

**Why I did NOT remove the animation, despite the negative feedback**

The main reason I animated plot 1 is that if it were static, it would show 4 groups of 3 bars. 12 bars is a lot to process.

Moreover, by forcing the viewer to press the Play/Pause button to see the bars and read the tooltips, it introduces ['cognitive disfluency'](https://blogs.allari.com/are-dashboards-and-visualization-too-good): interacting with the visualization means the user needs to pay more attention to it. 

I must say, it also solved the awkwardness of having batting average (a decimal) share the same y-axis with the other stats. However, even without batting average, I would have taken the same approach. A declarative title for a mostly-empty plot with a 'Play' button is an invitation to dive deeper.

It did make me uneasy ignoring such a common refrain, so I create a version with a static plot, and another that left out plot 1 altogether, to compare. 

(I did NOT send them back to those who gave the feedback, because it's Christmas and I want to keep them as friends)


**Why I did NOT fix the 'Play' lag time**

While only 1 person complained about it, it bothered me too. Unfortunately I could not figure out how to fix it. I tried to add a `.transition.delay()` to this series variable through also through D3, but it didn't work.

====

### v1

http://bl.ocks.org/limegimlet/9a3ffd08e82fa35f878717b939a1cf08

#### Feedback from Karsten, Director Solution Management, SAP Global GTM Analytics

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_karsten_dec20.png)

### v2

Changes:

* Updated .csv file to make values more explicit.
  * `hr` => `homeruns`
  * `avg` => `batting avg`
  * `B` => `Both`

http://bl.ocks.org/limegimlet/2e635b97f6e405aa8e4968f0d878d46d

#### Feedback from Paula, Director, Learning & Knowledge Management, Vision Critical

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_paula_dec21.png)

### v3

Changes to address feedback:
* Increased duration time for frames: `story.FrameDuration=4000;`
* Hid the y-axis
* Made the hover text lighter, so it was easier to see the button change to 'Pause' after clicking.

http://bl.ocks.org/limegimlet/5159b4a9c7fe20814f19217a6dccedad

Dec 24 2018

#### Shoko - Visual Artist / Writer / Translator
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_shoko_dec24.png)

#### Kinga - Mobile Application Developer, BAM software
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_kinga_dec24.png)

### v4 - Final version
Changes to address feedback:
* In plot 1, to reduce the 'noise' inherent with animations, I removed redundant tooltip text.
* In plot 3, added units of measure to axes labels

Additional changes:
* To provide context, added a short description of dataset beneath plot 1.
* In plot 2 & 3, adjusted axes ranges to reinforce idea that bubbles represent means, i.e. towards the middle of plot, rather than upper right corner. Specifically:
   * plot 2: set `x.overrideMax` to the max value for `batting avg`. I did NOT do the same for `y.overrideMax` since it's such an extreme outlier.
   * plot 3: set both `x.overrideMix` & `y.overrideMin` to the minumum value for weight & height. This makes it more clear that the `Both` group shorter and lighter, although still close to the `L` & `R` means.
  
## Resources

_list any sources you consulted to create your visualization_


