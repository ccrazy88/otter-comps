# Rough Outline of Stuff We Can Write



## Overview of occupancy modeling: -Sarah

### What is Occupancy Rate?

* "The probability that a randomly selected site or sampling unit in an area of 
  interest is occupied by a species" [MacKenzie2006] (pg. 11) 

### Different ways of sampling data
* Measuring rate of occupancy versus population
* Looking at tracks versus listening to stuff or actually looking for the
    animal

### Assumptions

* Independence of detection between sites
* No false positives
* Presence and detection probabilities constant across sites and surveys.
* Closed population.

### Types of Occupancy Models

* How much should we actually say about this?
* Maybe just talk about (basic) hierarchical models?

## Actual data/problem from the DNR

* Question of investigation
* Issues related to their data
* How their data was collected
-Kiva

### Descriptive Statistics on the Actual Data -Kiva

Kiva?


### Independence vs. Dependence Between Plots -Sarah

We tried to see if the assumption of independence is viable and whether or not
there were differences between data with different plot sizes and differences
between data containing plots and data containing every other plot.  

1. Using Markov Chains to find r.
   * r = potential long-term probability of detection, based upon the short-term
     conditional probabilities p and q acquired from our data (infinite limit as
     n approaches infinity of P<sup>n</sup>)
   * p = probability that a 0 follows a 0, q = probability that a 1 follows a 1
   * If 0->0 and 1->0 (the values of a column, basically) equaled each other,
     plots would have been independent?
   * Ultimately not useful to us because it does not take into account whether
     or not a site is occupied, so it doesn't apply to the hierarchical model
     that we are using.
2. Using s, where s = (# of 0-1's) - (# of 1-1's) for a given flight.
   * Decided to use the z-score of s as a measure of independence.
   * Therefore, needed the expected value and the standard deviation of s.
   * So, we needed the expected value of each term and the variance, which
     required finding the variance of each term and the covariance between the
     two terms.
   * Expected value is straightforward and we have all of the equations.
   * Variance is fun and we also have all of the relevant equations.
   * Calculated z-score for every flight and box-plotted them for each year and
     plot size and pitted data with every other plot against data with all 
     plots.
   * Nothing important with respect to plot size.  Alternating plots show more
     independence than all plots.  Look at report for more.
   * CAR model started working once we took s values of simulated data into
     account by increasing dependence.

### Adding E to the Model -Kiva

Hopefully Kiva has something in her notes.  Sarah has something, but she is not
100% sure that it is correct.

## Theoretical Stuff -Sarah

### Bayesian Statistics

* Bayes' Theorem
* Useful for hierarchical modeling: look at section 3.3 in book.
* Can use Markov Chain Monte Carlo (MCMC) to calculate posterior distribution

### BRugs/R

* All of our statistical analysis was performed in R.
* All of our modeling was performed using BRugs, which allowed us to use WinBUGS
  commands and stuff in R.

## Standard Hierarchical Model -Chrisna

We assume a different p and E for each observer.  

1. Normal distribution for p and E
    * uniform distribution for a and c
    * b = .1
    * p from (.6, 1) and E from (0, .4)
    * uniform distribution for psi
    * uniform distribution for theta
    * iterations: 10000, 10000
2. Beta distribution for p and E
   * gamma distribution for a, b, c, d
   * p from (.6, 1) and E from (0, .4)
   * uniform distribution for psi
   * uniform distribution for theta
   * iterations: 10000, 10000
   


### Data Simulation

1. Simple simulated data.
   * Variables: # of sites, # of snow events, # of observers, # of snow days,
     psi, theta, p (for each observer), E (for each observer)
   * Simulates data using simple hierarchical model with E included.
2. Irregular simulated data.
   * Variables added: Lots of vectors that allow for different numbers of snow
     events and snow days each observer participated in.
   * Simulates data using simple hierarchical model with E included.
   * Made the way it was made for technical reasons we will probably not bother
     to mention because they aren't important.

     The beta distribution worked better.  
     Can use chart from status reports to show how well it worked.

## Dealing with the Spatially Correlated Data -Kiva
### Some General Information About the CAR Model

* Spatial dependence between sites that are adjacent.  We give every adjacent
  site a weight of 1.
* Sarah and Kiva will add more!

### The Actual CAR Model (what parameters we used it on, etc.)

* Our data is not aggregated values and is not quantitative, so we had to make
  some adjustments.
* Used a CAR prior on theta.
* CAR normal distribution for alpha1
* flat distribution for alpha0
* gamma distribution for tau
* uniform distribution for psi
* beta distribution for p and E, limited to the intervals (.6-1) (0-.3) and
  a,b,c,d are taken from a gamma distribution
* iterations: 12000, 10000



### Different Ways We Simulated Data

3. Simulated data spatially correlated on theta.
   * Variables added/changed: theta + alpha (probability of a track being laid 
     given the current site is occupied and the previous site has a track),
     theta (probability of a track being laid down given the current site is
     occupied and the previous site doesn't have a track)
   * Very rarely converged with the CAR model.
   * Data showed more independence than the actual data, according to s-hat
     values.
4. Simulated data spatially correlated on theta and psi.
   * First tried to correlate data just on psi, but didn't improve upon #3.
   * Variables added/changed: beta (probability of a site being occupied given 
     that the previous site is occupied), psi (probability of a site being
     occupied given that the previous site is not occupied)
   * Worked better with the CAR model, but the CAR model was still not great.
   * Data simulated with this model shows similar dependence to the actual data.


   We can just look at the most recent status report (StatusReport.tex).  We need
   to add stuff about the difference between the estimates for different plot
   sizes (which makes sense but we didn't actually analyze this).  So, for that,
   look at the most recent e-mail from John F.

## Discussion -Chrisna

### Trying to get models to work on the actual data (taking out E?)

* When the model did not converge, we tried removing E in order to simplify it.
* This improved convergence in the standard model for the 402m 2004 data, but 
  the estimates are questionable.
* This improved convergence in the CAR model for 402m 2003 data, and maybe would
  for the rest of the data, but always estimate psi above .9, which we do not 
  believe to be accurate.  Therefore, we did not try this for all of the data.

### What estimates we found for our data, what data didn’t work and why

* Take from most recent status report.  StatusReport.tex

### Effect of plot size on parameters

* Look at the latest email from John F.

### Effect of covariates (i.e. which ones are more important?)

* Number of observers: Least important.
* Number of snow events
* Number of days since snow: Most important!
* Simulation results saved in R.

### All plots versus alternating plots

* We decided that the data with all plots are better because they have more 
  information, and the models work pretty well on correlated data.

### Suggestions on best practices for further data gathering trips

* Look at section on covariates.
* More observers are better, but can use only one.
* Maybe the same observer could go twice in one day.  Would they have a 
  different p and E for the second flight?
* Need at least two snow days worth of flights per snow event.  More is better.
* Need at least three snow events if you have one observer, two if you have 
  three or more.  More is always better.
* No need to use alternating plots.