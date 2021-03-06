# Visualizing major-league baseball stats with dimple.js

Course files & final project for the Udacity Data Visualization course, part of the Data Analyst nanodegree.

## Summary

This plot highlights the difference in average homeruns and batting averages for right-, left-, and ambidextrous major-league baseball players, without any clear correlation to height or weight. It uses the [dimple.js](http://dimplejs.org/) charting library.

## Data

The data comes originally Udacity's baseball [data set](https://s3.amazonaws.com/udacity-hosted-downloads/ud507/baseball_data.csv) of stats for 1157 professional players.

The final visualizations use 2 datasets that are slightly modified versions of the original:

* Plot 1 uses a long-format version of the dataset, `baseball_data_long.csv`. The variable names were stacked into an `attribute` category column, and their values into a `value` column. This allows the creation of a categorical x-axis for all 4 baseball metrics.
* Plots 2 & 3 use the original wide-format `baseball_data.csv` with an additional `counts` column. It stores the total number of people in that player's `handedness` group, so it can be used to size the bubbles.
* Both .csv's had column names and values renamed, described in the Feedback details section.

## Design

In retrospect, I focused too much initially on customizing look & feel instead of assessing the effectiveness of my design choices. On top of that, I ran into some showstopper bugs with customizing tooltips. In the end, I had to go back to the drawing board before I had something working well enough to seek outside feedback.

The evolution is documented below.

### Initial design

**Plot type: bubble chart** 
* Since there were major differences for 2 different variables (homeruns and batting average), the plotting on an x-y axis most clearly shows each group's relative position. 

**Colour scheme: black and white**
* conveys pen & ink which again conveys the feeling baseball more than the muted pastels ubiquitous to corporate KPI dashboards.
* use cross-hatching to denote different groups: can use direction of cross-hatching to reinforce left vs right vs both.
* Inspiration is this [plot](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_bars_sketchy)

**Axes: standardized around a mean of 0**
* a standardized axes allows the same axes to compare different pairs of variables. Since I'd like to allow users to toggle between a plot of `homeruns` vs `batting average` and `height` vs `weight`, having common axes allows the user to focus only on the positional changes of bubbles.

**Animation**
* the user can click to comparing the other two numeric variables, height and weight, where there is nearly no difference between right- and left-handed players. 
* inspriration is this [plot](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control). 

### Prototypes

#### Prototype 1a: Bubble plot with standardized data (z-scores)

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/images/proto1_sketch.jpg)

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/images/proto1_a.png)

Issues: 

* Standardized axes over-complicates message
* The customized tooltip returns 0 for negative y-values and all x-values!
* It's statistically incorrect. Since `HR` and `avg` are not normally distributed, it's misleading to assume a mean of 0 with standardized values (this is the Central Limit Theorem).

Solution: use the original baseball data.

#### Prototype 1b: Bubble plot with non-standardized data

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/images/proto1_b.png)

Issues:
* While bubbles are efficent in that they represent 3 variables at once, it also means there's more to absorb.
* The fill patterns are too noisy, especially when bubbles overlap
* Custom tooltip still returns 0 for x-values.

Solution: Instead, use a bar plot.

#### Prototype 1c: Animated bar plot

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/images/proto1_c.png)

Issues: 
* Unlike bubbles, the bars are side by side, so the fill pattern is hard on the eyes.
* Bars don't do as good a job as bubbles for contrasting performance differences vs size differences.

Solution: combine bar & bubble in one data story. And let go of the custom fill patterns. 

Back to the drawing board!

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/images/proto2_sketch.jpg)

Initially, I envisioned animating each of the 3 plots. 
* The bar plot introduces to the data story. By displaying bars L, B, R for each statistic in turn, the viewer can more easily digest compare the handedness groups for each variable.
* The bubble plots provide the main point of the story. They would toggle to show the non-aggregated data as a scatterplot OR the means as bubbles.

#### Prototype 2a:'Overview' bar plot +  2 bubble/scatter plots

[View on bl.ocks.org](http://bl.ocks.org/limegimlet/3d31190dfc1637c74e438e3c902a110e)

Issue: 
* In the end, the scatterplots didn't do anything to explain the differences between each `handedness` group, and would require extra dev time and clutter up the page with additional toggle buttons.

Solution: Keep plot 1 (the bar plot) animated, but plots 2 & 3 would be static bubble plots.

#### Prototype 2b:'Overview' bar plot +  2 bubble plots

[View on bl.ocks.org](http://bl.ocks.org/limegimlet/16252e6d8b900ae42783a3cddbdc16fa)

### V1.0 - Ready for outside feedback

* Added titles to each plot that together formed a sentence. Aside from that, kept text minimal as the plots pretty much speak for themselves.
* Restored the handwriting-like font 'Shadow into Light'

[View on bl.ocks.org](http://bl.ocks.org/limegimlet/9a3ffd08e82fa35f878717b939a1cf08)

### v1.1 & v1.2

These are interim versions I made after receiving feedback. See the 'Feedback details' section for a description of changes.

### V2.0 - Final version

This is the version being submitted and included in this repo. See the 'Feedback details' section for a desciription of changes.

## Feedback

4 people in total gave gave feedback on 3 different iterations of the data story.

To summarize:

* All 4 clearly understood the overall message. 
* However, only 1 out of 4 liked the animation. The other 3 were puzzled why it couldn't be static.
* 1 person really liked the changing y-axis, another hated it.
* 1 person didn't understand that bubble size represented group size. 
* Surprsingly (to me), only 1 person complained about the lag time after pressing "Play".

## Feedback details

### For [v1.0](http://bl.ocks.org/limegimlet/9a3ffd08e82fa35f878717b939a1cf08)

#### From Karsten, Director Solution Management, SAP Global GTM Analytics

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_karsten_dec20.png)

### For [v1.1](http://bl.ocks.org/limegimlet/2e635b97f6e405aa8e4968f0d878d46d)

Changes to address Karsten's feedback:
* Updated .csv file to make values more explicit on x-axis and legend
  * `hr` => `homeruns`
  * `avg` => `batting avg`
  * `weight` => `weight (lbs)`
  * `height` => `height (in)`
  * `B` => `Both`

#### From Paula, Director, Learning & Knowledge Management, Vision Critical

![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_paula_dec21.png)

### For [v1.2](http://bl.ocks.org/limegimlet/5159b4a9c7fe20814f19217a6dccedad)

Changes to address Paula's feedback:
* Increased duration time for frames: `story.FrameDuration=4000;`
* Hid the y-axis
* Made the hover text lighter, so it was easier to see the button change to 'Pause' after clicking

#### From Shoko - Visual Artist / Writer / Translator
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_shoko_dec24.png)

#### From Kinga - Mobile Application Developer, BAM software
![](https://github.com/limegimlet/data_viz/blob/dev/final_project/feedback/feedback_kinga_dec24.png)

### [v2.0](http://bl.ocks.org/limegimlet/255dbc945c697a77b49ef86b6be1899b) - Final version

Changes to address Shoko & Kinga's feedback:
* In plot 1, to reduce the 'noise' inherent with animations, I removed redundant tooltip text.
* In plot 3, added units of measure to axes labels

Additional changes based on my own assessments:
* To provide context, added a short description of dataset beneath plot 1.
* In plot 2 & 3, adjusted axes ranges to reinforce idea that bubbles represent means, i.e. towards the middle of plot, rather than upper right corner. Specifically:
   * plot 2: set `x.overrideMax` to the max value for `batting avg`. I did NOT do the same for `y.overrideMax` since it's such an extreme outlier.
   * plot 3: set both `x.overrideMix` & `y.overrideMin` to the minumum value for weight & height. This makes it more clear that the `Both` group shorter and lighter, although still close to the `L` & `R` means.
   
### Justification for not addressing some feedback

#### Animation of plot 1

The main reason I animated plot 1 is that if it were static, it would show 4 groups of 3 bars. 12 bars is a lot to process.

Moreover, by forcing the viewer to press the Play/Pause button to see the bars and read the tooltips, it introduces ['cognitive disfluency'](https://blogs.allari.com/are-dashboards-and-visualization-too-good): interacting with the visualization means the user needs to pay more attention to it. 

It also solved the awkwardness of having batting average (a decimal) share the same y-axis with the other stats. However, even without batting average, I would have taken the same approach. A declarative title for a mostly-empty plot with a 'Play' button is an invitation to dive deeper.

It did make me uneasy ignoring such a common refrain, so I create a version with a [static plot 1](http://bl.ocks.org/limegimlet/78260a3948950a74e260f52a4aba377c), and another that [left out plot 1 altogether](http://bl.ocks.org/limegimlet/ef2e059afe48a0360254b8af75247bae), to compare. Still preferred keeping an animated plot 1.

(I did NOT send them back to those who gave the feedback, because it's Christmas and I want to keep them as friends)


#### Lag time for 'Play' button

While only 1 person complained about it, it bothered me too. Unfortunately I could not figure out how to fix it. I tried to add a `.transition.delay()` to this series & stories variables, as well as through D3, but it didn't work.
  
## Resources

* Dimple documentation https://github.com/PMSI-AlignAlytics/dimple/wiki
* Inspiration for the first design http://dimplejs.org/advanced_examples_viewer.html?id=advanced_bars_sketchy
* Example of storyboards in action, plus how to create onClick events: http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control
* bug with negative values in mouseover: https://github.com/PMSI-AlignAlytics/dimple/issues/204
* Creating a play button https://bl.ocks.org/officeofjane/47d2b0bfeecfcb41d2212d06d095c763
* Information on overriding Dimple inline styles: https://stackoverflow.com/questions/27830560/custom-tooltip-color-and-font-size-in-dimple-js
* Writing reusable javascript: https://medium.com/@_kamerontanseli/writing-reusable-javascript-d220aa501e67
* Seeing what's available in an object: https://stackoverflow.com/questions/957537/how-can-i-display-a-javascript-object
* D3 transistions: https://bl.ocks.org/Kcnarf/9e4813ba03ef34beac6e

