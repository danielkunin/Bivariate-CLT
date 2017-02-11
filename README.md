# An Illustration of the Bivariate Central Limit Theorem using D3

## Introduction

This is a final project for the [Interacting with Data](https://github.com/Brown-BIOL2430-S04-Fall2015/syllabus) graduate seminar that took place in the fall of 2015. The goal was to build an interactive visualization that illustrates the (multivariate) central limit theorem, an important statistical result.

To view the complete visualization, click [here](https://rawgit.com/danielkunin/finalproject/master/2D_CentralLimitThrm.html). Read on to learn more about the details of our work.

This project was carried out in equal part by **Daniel Kunin** and **Tyler Dae Devlin**, who were juniors at Brown University at the time.

## The Theorem

This visualization is not meant to replace a rigorous development of the mathematical results in question. Rather, it is designed to supplement a more analytical approach to understanding the multivariate CLT. As such, we assume that the reader already familiar with the conventional univariate CLT at a minimum, and the multivariate CLT in the ideal case.

## Background

Ours is not the first attempt to create a visualization of the central limit theorem. In fact, there are even a few CLT visualizations in D3. See, for example, [Victor Powell's interactive animation](http://blog.vctr.me/posts/central-limit-theorem.html) of Sir Francis Galton's [bean machine](https://en.wikipedia.org/wiki/Bean_machine) or [Philipp Plewa's visualization](http://www.mpe.mpg.de/~pmplewa/showcase/clt/) of the CLT , which takes sample means from a uniform distribution. 

In Powell's animation, D3 is used mainly to visually simulate the process by which Galton's bean machine works while updating a histogram in real time. Plewa's illustration uses motion to connect the various steps involved in taking a sequence of sample means from a population. In our view, both visualizations are successful in communicating a particular facet of the univariate CLT.

To our knowledge, however, no attempt has been made to create a visualization of the multivariate CLT, which concerns joint probability distributions.

The fact that the formal mathematical treatment of the multivariate CLT is [fairly abstruse](https://en.wikipedia.org/wiki/Multivariate_normal_distribution) justifies the need for a well-designed intuitive visualization.

## This project

### Mapping of data to esthetics

Each sample point is drawn uniform at random over the square [0,100]×[0,100]. This can be seen by setting the sample size to one and generating many points: the plot is uniformly covered by the resulting samples.

For a sample size *n* > 1, *n* points are plotted on the square. The *x* and *y* means of the n points are calculated, and all n points move to the location on the square coordinating to this mean position. Motion helps the viewer see how the points move to their collective "center of mass."

Once the *n* points move to their mean, they fade to a low transparaency. This allows the viewer to see the density distribution when many mean points are generated.

The color red is used to connect the box that sweeps from right to left to the plot of the cumulative distribution function on the right hand side of the graphic. This reminds the viewer that the cdf is generated, loosely speaking, by sweeping from left to right accumulating points along the way.

The total number of esthetic modalities in our visualization is quite small. For a complex concept, a simple illustration is crucial.

### Filtering

Filtering is used only in the sense that the actual data that generate the visualization, i.e. the individual sample draws from the uniform distribution on the square, are only shown transiently: these points are shown for an instant before moving to the calculated mean point and permanently disappearing from the visualization.

This way of filtering the data keeps the plot from becoming overly crowded. Although we could have used color to distinguish between sample points and sample means, we believe this would have cluttered the plot in such a way that the explanatory power of the graphic would be diminished.

### Extra ink

There is not too much in the way of non-data ink in our visualization. Perhaps one element that might be considered chartjunk by Edward Tufte's standards is the set of chart borders. Not only do we plot the entire *x* and *y* axes, but we also include chart borders on the upper and right side of the plot. 

We believe that despite contributing non-data ink, these elements help remind the reader of the scope of the underlying uniform distribution. They also allow the viewer to more easily locate the center of this distribution and verify that this is also the center of the bivariate normal distribution of the sampling means.

### Motion

As mentioned above, motion is used to illustrate *n* sample points converging upon their sample mean. This use of motion is inspired by Plewa's D3 [visualization](http://www.mpe.mpg.de/~pmplewa/showcase/clt/) which takes one-dimensional sample means. Although this approach is certainly correct, we think it is not immediately clear that the animation illustrates the process of averaging sample points.

Somehow, using an additional dimension makes it easier to recognize that the sample points are moving to their collective center of mass, thus bridging the gap between intuition and theory.

### Perspective

Many aspects of the visualization are fixed in ways that are not strictly necessary as dictated by the statistical results of the CLT:

* Each sample point is always taken from a uniform distribution over the square, whereas the CLT is much more general and applies to many other distributions.
* The red box always sweeps from left to right. The rotational symmetry of the bivariate normal distribution implies that a box sweeping in any direction should generate a normal cdf.
* Sample sizes are limited to the range [0,20]. This is sufficient to see how the bivariate normal is "narrower" for larger sample sizes, but of course in reality larger sample sizes are often used.

Ultimately, the gains in simplicity were worth the sacrifices in generalizability for us. Although someone with training in statistics might desire additional interactive functionality, we aimed to keep the graphic at a level that would ensure its accessiblity to any educated layperson.

## Assessment

In sum, we hope that we have created a tool that is at least somewhat useful in helping people understand a nontrivial statistical theorem. We think that using two dimensions is actually helpful for understanding both the univariate and multivariate versions of the central limit theorem.

One important future addition to our visualization would be an empirical histogram of the sample means in addition to the cdf that exists in the current version of the project. The bell curve is iconic among statisticians and non-statisticians alike; a presentation of a histogram that mimics this curve would serve to demonstrate the CLT's main conclusion.


