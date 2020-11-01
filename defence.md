---
marp: false
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
---


<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}

.slide h1{
 text-align: center;
 }

.slide {
 background-color: black;
 font: 40px arial, sans-serif; 
 }

.slide a {
 color: indigo !important;
 }

.slide h1 {
 color: indigo !important;
 text-align: center;
 }

.slide h2 {
 color: darkviolet !important;
 }

.slide p {
 color: darkorchid !important;
 }

</style>
<!--
backgroundImage: url('https://marp.app/assets/hero-background.jpg')![bg left:40% 80%](https://marp.app/assets/marp.svg)
-->
# **Towards Neuronal Deep Fakes:**
### Data Driven Optimization of Reduced Neuronal Models
author: Russell Jarvis, PhD candidate Neuroscience. 
ICON Laboratory.
Co-advisors: Prof Richard Gerkin, Prof Sharon Crook.
PhD Committee: Prof Richard Gerkin, Prof Sharon Crook Prof Yi Zhou, Prof James Abbas.
date: 5 November 2020

---


# Introduction 
- Better electrical models of the brain are needed.
- Better brain models will Improve Medicine and Artificial Intelligence.
- Current models are lacking in speed, accuracy, and interprebility.
- Fortunately models can be  improvemed. There are some leads about how to make models: faster more accurate, and more interpretable.
---

### Virtual Experiments
![width:275px center](figures/vclamp.png)
- What they are and why?
Many Electrical Neuron Models 
are capable of simulation applied current injections at the cell soma.
- Virtual experiments are a way of finding out information about in vitro cells.
Virtual experiments can also help to bring models and in vivo cells into better alignment.


### Why would we need to Optimize?
* Without proper alignment models may fail to capture 
important biological details they were intended to represent.
* Virtual Experiments can help us to optimize.

---
### Virtual Experiments Gather Useful Measurements: Features <!--fit--> 
* These Measurements are collectively called Features.
* Action Potential height as it varies along the spike train.
* Example Features:
![center](figures/AP_Amplitude.png)

---


<!--
Features: Linear behavior of the cell 
![center](figures/voltage_features.png)
-->

### Single Spike Shape: After Hyperpolarisation Potential. <!--fit--> 
  ![center](figures/AHP.png)

---
<!--models are virtual experiments.-->
<!--* Negative results are important.-->
<!--
* Fitting to the mean is a bad idea.
I show that fitting to the mean measurement, may work often, but it is also based on flawed methodological assumptions.
- Above threshold spiking fits 'spot the fake' part 2.
- Preferred current versus fixed current search.
- optimal still possible despite rastrigrin's function
-->

### What is Required for Successful Optimization? <!--fit--> 
4.1 What is Required for Successful Optimization?For optimization to both succeed and be useful, several criteria must be met:
**Overall Speed**,**Smoothness of Error Function**, and **Relevance**
(Van Geit et al, 2007)

---
<!--biological relevance is desirable, but it is not necessary-->

### Relevance 
**Relevance:** The objective function should reflect fundamental and important properties of thed data that a good model would reproduce. Ie the model should not fit to noise in the data, or exclusively a small part of a waveform, such as exclusively getting a minor detail right like the depth of an AHP.

---
### Fast Work Flow
**Speed:** Models, Errors, optimization, the whole work flow needs to be fast to calculate, since typically a large number 
$$ > 1,000,000\ \ models $$ 
best if each one is only ~2 ms
of model evaluations are performed during the search, many of which may require re-simulation. I will explain more about this later. Largely this is needed to deal with human limitations
* The human designer benefits from prompt feed back about violated assumptions.

---

### Smooth Learnable Error Surface
**Efficient Convergence:** The solution space should be as continuous and convex as possible,so that the search algorithm can rapidly converge to a global optimum

---


### Computer Algorithms are like Recipes.
<!--True but not the point I need to make
The ordered sequence of adding ingredients matters.
-->
Ingredients (**data**, and **features**). 
* With the wrong ingredients Error surfaces can become 
* too complicated for machine learning to learn.
<!--* Because GA can satisfice they return reasonable solutions in a short -->

---

### What Data to Fit Models with
![width:700px center](figures/mouse_opt_data.png)

---

### The Genetic Algorithm Recipe
![center](figures/GA_process.png)
An engine that drives a lot of results in this work
True solution inaccessible 

---

<!--

Wont get trapped
How good were fits?
How good are these fits with regards to other standards?

Simulation as an Experimental Platform: The Need for Speed
- Mean model not mean measurement
- Above threshold spiking fits 'spot the fake' part 2.
- Preferred current versus fixed current search.
- optimal still possible despite rastrigrin's function

Identify the Features (ingredients) that will add up to good recipes
Science
Show how some ingredients lead to bad recipeas.
-->

### Part 2  Models and Data are Readily Distinguishable in a Reduced Dimension Space



* 48 features.
* Number of samples
If models and experiments are still distinguishable it means
1 Models need revision.
2 Models need More specific optimization.
* Since optimization conditions are fragile, if 2 is true. 
Its sometimes hard to find the right approach.
Models and Data are Readily Distinguishable in a Reduced Dimension Space

---


### Experiments from different brain regions are distingiushible.
* Experiments versus models are distinguishable
* Models from different brain regions cluster together.

![center](figures/cortical_model_data_agreement_52_1_croped.png)

---
### 

![center center w:400 h:400](figures/cortical_model_data_agreement_52_1_croped.png)

---
# Alternatives to Eve Marder Dilemna
Fitting to experimental means can work but is not reliable.
Depends on assumptions of data covariance.
Alternative: 
Fit to the whole trace of a single experiment.
Sources of experimental error will not be averaged away

---
<!--
[allen_exp](figures/mouse_opt_data.png)
-->

### Models and Data are Readily Distinguishable in a Reduced Dimension Space <!-- fit --> 
---
### 2nd Eigen Vector:


* **fast-trough-index**: Index into array when begging of trough occurs **1.5** 
$$1.5 \times rh$$ 
* Two
* Three

| Feature Name   |  Feature Description | Extraction Library Stimulus Strength |
|---:|---------:|---------------:|
| fast-trough-index |Index into array when begging of trough occurs | Allen 1.5× Rheobase |    
| peak-index-1.5x | Index into array when peaks occurs | Allen 1.5× Rheobase |                              
|  upstroke-index-1.5x | Index into array of detection of first upward phase of AP | Allen 1.5× Rheobase |
|  fast-trough-index | The time when a trough is commenced Allen | 1.5× Rheobase |
|  peak-index indexs | Indexs into array when the start of a trough is entered | Allen 3.0× Rheobase |
| threshold-index | Index into array when threshold occurs | Allen 3.0× Rheobase | <!-- fit --> 

---

<!--fast-trough-index Index into array when begging of trough occurs Allen 1.5× Rheobase
peak-index-1.5x Index into array when peaks occurs Allen 1.5× Rheobase
upstroke-index-1.5x index into array of detection of first upward phase of AP Allen 1.5× Rheobase
threshold-index-1.5x Description Allen 1.5× Rheobase
fast-trough-time The time when a trough is commenced Allen 1.5× Rheobase
fast-trough-index Indexs into array when the start of a trough is entered Allen 3.0× Rheobase
peak-index indexs into array when voltage peak(s) occur Allen 3.0× Rheobase
upstroke-index Index into array when first upward phase of a spike commences Allen 3.0× Rheobase
threshold-index Index into array when threshold(s) are surpassed Allen 3.0× Rheobase -->



### Maths works
$$ \eta, 12^{N}  $$

---

### IZHIkevich_fit_60Adexp_80.jpg
It is hard to see but generally spike time and spike shape conflict.
![center](figures/IZHIkevich_fit_60Adexp_80.jpg)

---

### IZHIkevich_fit_60Adexp_80.jpg

It is hard to see but generally spike time and spike shape conflict.
![center w:900 h:450](jtt.jpg)

---

### IZHIkevich_fit_60Adexp_80.jpg

![](figures/94spikes)

---

### Spot the fake

![Identify the counterfit](figures/adexp_fit_allen_specid_325479788.png)

---

Identify the counterfit
========================================================
![Identify the counterfit](figures/adexp_fit_allen_spec_id_476053392.png)

---

Identify the counterfit 2
========================================================
![Identify the counterfit](figures/adexp_fit_allen_specid_325479788.png)

---

Spot the fake part 3.
========================================================
High density firing without adaptation
![Identify the counterfit](figures/28spikesB95.png)

---

### Optimization Failure
![center](current_voltage_breakdown.png)
48 spikes are matched, base $$ V_{M} $$ is matched

---


Strengthened Some Pre-Existing Theoretical Claims
=======================================================
Marder considered conductance based models of somato-gastro ganglion cell in lobster
we consider two classes of reduced models in broad categories of experimental cells

---



Mean model not equal to model mean
=======================================================
![center ](figures/mean_model_vs_mean_measurement.png)

---

<!--skewed_distribution.png
![center ](figures/skewed_distribution.png)
-->

reproduced_izhi.png
========================================================
![center ](figures/reproduced_izhi.png)

---

<!--
parameter_b_hopeless_surface2.png
![](figures/parameter_b_hopeless_surface2.png)
-->


 



Visualization of Eigen Vector Loadings
========================================================
![center](figures/cortical_model_data_agreement_54_1.png)

---

### Data Driven Optimization can be Fragile. 
#### Optimization Needs Special Conditions
##### Possible Causes of Failure:
* 1 Models are not flexible enough to recapitulate important variance in data
* 2 Data is reliable but misrepresented (1 & 3 are sound but).
* 3 (1 & 2 are sound but) Error Surfaces lack learnable information.

---

### Controls. 1 and 3 can be controlled by randomly simulating data, but checking the learnability of error surfaces.
* * In my work I found evidence for all 3 types of failure, but before any problems 
2. Cannot be directly controlled but the data can be interrogated.

---

### Hardening Optimization, by Controlling for failure.
## Possible Causes of Failure:
* 1 Models are not flexible enough to recapitulate important variance in data
* 2 Data is spurious (1 & 3 are sound but).
* 3 (1 & 2 are sound but) Error Surfaces lack learnable information.

Controls. 1 and 3 can be controlled by randomly simulating data, but checking the learnability of error surfaces.
2. Cannot be directly controlled but the data can be interrogated.

---


### The Need Speed
* In order to get a picture of what was going wrong. 
* To reveal all of this. Must do many virtual experiments.
* To do many experiments quickly I needed faster models so I had to rewrite models using code accelerators. 
as there were very many different types of experiments I would need to do in a short amount of time

---
### Although Genetic Algorithms are Overall Robust
* In neuronal modelling 
* They still are fragile in the sense that they benefit 
From human design supervision and testing

---

### High Dimensional Space
![center](error_surface_pairs2.png)

---

### slice
Small part of Error Hypervolume reveals a problem

![center](slice_into_error_surface.png)

---

### Bad Recipe Ingredients A Closer Look:

![center](figures/corrogations.png)

---

###
![center](rastrigrins_cross_section3.png)

### Slightly Bad Recipe Ingredients
### Error Surface Defects

![center](figures/corrogated_surface_but_functional.png)




---


### Good recipe ingredients:

![center](figures/friendly_error_surface.png)

---



<!--
Can exploit global convexity of complex surface
satisficing
Still Vulnerable to poor learning environments
Still benefit from supervision and intervention.

Can fall back to random sampling
With memory of best.-->


### Error Surface Defects

The 10% of surfaces that are practical to visualize.
12 variables 

---


### E Marder 

Showed What can go wrong when fitting models to the mean of electrical neuron data
when the mean and variance violates assumptions of normal distributions.snk

---

<!--
E Marder postulated, that the mean model is not always a good 
representation of neuronal electrical recordings, and that bad things could happen 
if you fit models to the mean.

Marder showed this in conductance based models of the lobster somato-gastrion-ganglion neuron.
-->
![](figures/eve_marder.png)



<!--friendly_error_surface.png
========================================================
![](figures/friendly_error_surface.png)-->

Error Surface Defects
========================================================


<!--In 10 dimensions 40 unique pairs of dimensions in error hyprevolume-->



### Contributions to Modeling:
=======
* Two fast models.
* Auto code generation to make novel feature/data combinations.
* High dimensional exploration of variance in data and models.

---

Contributions to Science:
=======
* Recipe for fitting to Izhikevich and AdEx models to 
* spike train shape+AP times
* recipe for fitting Izhikevich and AdEx models to FI curves.
* better understanding of model limits (shape is often incompatible with firing frequency current relationship.) Probably because of underlying representations of capacitance, and resistance (a,b), are more like fudge factors than anything else.

Contributions to Science:
=======
* Spike shape and spike times seem conflicted.
* More complex models don't necessarily fit better.
* Reduced Models not good at fitting to time constant.
* Demonstrated Reasons why fitting to the mean of neuron electrical experiment data is not a good idea.
* main reason is bi-modality, second reason is variance structure (skewed).

Contributions to Science:
=======
* Fitting to FIcurve usually possible
* Spike shape and spike times seem conflicted.
* More complex models don't necessarily fit better.
* Reduced Models not good at fitting to time constant.
* Demonstrated Reasons why fitting to the mean of neuron electrical experiment data is not a good idea.
* main reason is bi-modality, second reason is covariance structure.

<!--
* A L5PC was not necessarily great at fitting to mean based data also-
-->

Contributions to Science:
=======
* Reduced models could usually fit to FI-curves of experiments.
* Reduced models could fit Some types of spike trains quite well.
* Reduced models could be over-fitted to spike shape.


Models are not flexible enough or over fitting or both
=======
When data is good, you could fit a model to the spike times and spike shapes in waveforms.
but only for a single current injection value



Web Application
=======
Why? 
Users should be to upload data, and get fitted models in return.
If users could do that then they could build more accurate network simulations.
API for power users.


Qaulity of Fits
=======

| specimen id   |   FI Slope Gradient |  TimeConstantTest |   RestingPotentialTest |   InputResistanceTest |   RheobaseTest |
|---:|---------:|----------:|-------------------:|-----------------------:|----------------------:|---------------:|
|  623960880 |     0.18 |                 23.8 |                  -65.1 |                   241 |             70 |
|  623893177 |     0.12  |               27.8 |                  -77   |                   136 |            190 |
|  471819401 |     0.18 |               13.8 |                  -77.5 |                   132 |            190 |
|  482493761 |     0.09 |                24.4 |                  -71.6 |                   132 |             70 |


The End: Acknowledgements:
==========
This research effort was a large international team effort that was only possible because of
continuous attention from diverse faculty at ASU.
First and foremost I would like to thank my committee: Professor Sharon Crook, Professor Rick
Gerkin, Professor Jimmy Abbass, and Professor Yi Zhou. Additionally Sharon Crook and Jimmy
Abbas offered significant unexpected personal support. Lastly, Rick poured many hours of his life
into consulting about this project. Thanks generally to the ASU research community
<!---
Other sources of general support came Professor John Alcock who allowed me to lodge for free in
his house and, SOLS Graduate Program Associate Directory Professor Emilia Martins, Professor
Julie Liss, Professor Susanne Neuer, and Professor Bradley Gregor, were called on. I would also
like to thank Amy Pate who helped with VR and Augmented reality technology.
I would also like to thank the late Jane Hurley, a recent PhD graduate from ASU Department of
Exercise and Nutritional Sciences, who put significant work into making Arizona desert accessible
to outsiders, and offered significant personal support. I would also like to thank the Anthony
Nicholas for inspiration and Imogen Hamel-Green, and the Hamel-Green family.
I would also like to thank my parents, as well as the late Jane Hurley, a recent PhD graduate from
ASU who offered significant personal support.
“When applying digital methods, you may have to try very many different things” – Emilia Martins
I would also like to thank Research Professional Renate Mittelmann for supporting an early and
difficult transition to Docker-driven development.

deceptively difficult problem. 
Mohammad Samavat had a poster on this problem when I first arrived at ASU.
-->

What is publishable Now:
==========
Mean model not mean measurement. 
* Problems of using the mean to optimize with.


Pre-emptive Question Slides from committee.
==========
![]()

<img src='esp.png'> 
  

<img src='mod.jpg'> 
<strong>9 * 9 dimensions</strong>
 <br>
 <p> did it work? </p>

To find out about the brain we can do virtual experiments.
==========
![]()


<!-- 
speed, results might violate your assumptions, and could be not what is expected, provoking more experiments.

speed 3.
The most common type of result is tentative, to get results that are consistent in a system, need prompt feedback.

smoothness 3 , and relevance  6.

What is publishable With More work:
==========
-->