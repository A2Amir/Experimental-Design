# Experimental Design
IF you see that two variables are related to one another doesn't mean that when one changes the other also changes as well which gives meaning **Correlation does not imply causation**.  However, there will be cases where you do want to say that **one variable causes another to change**. You might want to say that changes to your website cause visitors to make more purchases or maybe you want to show that changes to your recommendation engine provide better search results to your users.  To test your hypotheses,
you should run an experiment. This is why experiment design is so important for data scientists to know about the scope of conclusions that they can make from their data. 

In this Repo you'll learn:

   #### 1. what it takes to build an experiment. 

   #### 2. about the types of experiments,
   
   #### 3.types of Sampling

   #### 4. ways of measuring outcomes,

   #### 5. pitfalls to check for when designing an experiment.


 ## 1. What is an Experiment?
 
 Assume we want to add a new feature to our website to see if this new feature leads to more sales. 
 
 * First to create an experiment we need to perform a comparison between two groups. If we have some people interact with the old website without this new feature and some people interact with the new website with this new feature then a difference in purchases made by each group will show us the effect of the new feature.
 
 <p align="center">
<img src="imgs/1.PNG" height="300" weight="500"/>
<p align="center">
 
 *  Secondly, we need to control for other differences between groups. The only difference between the two groups should be the feature that we specifically manipulate (whether the customer gets the site with the feature or the site without the feature). The typical way of doing this is through randomization.
For each customer, we randomly assign them to a site version. By randomly assigning individuals to each page, the distribution of other variables like age or gender should be similar between groups.  **The only practical difference between the groups should be the feature we care about whether they got the new feature or not.** 
 
  
 <p align="center">
<img src="imgs/2.PNG" height="300" weight="500"/>
<p align="center">
 
 
**Sometimes, you might not be able to run a true experiment to test your hypotheses due to not having multiple groups or not being able to control random assignment to groups.** This will require  to consider alternative study designs. These methods can be put into three main bins, based on the amount of control that you hold over the variables in play:


   1. If you have a lot of control over features, then you have an **experiment**. In the social and medical sciences, an experiment is defined by comparing outcomes between two or more groups, and ensuring equivalence between the compared groups except for the manipulation that we want to test.
    

   
   2. If you have no control over the features, then you have an **observational study**. A classic example of this is on the risks posed by smoking.  The hypothesis is that smoking increases the likelihood of developing diseases like lung cancer. Because it is **unethical** for us to make people smoke in order to run an experiment for testing our hypothesis. Instead, we need to rely on collecting data passively making connections between smoking rates and disease incidences based on groups or matched individuals. Establishing causality is very difficult or perhaps even impossible with an observational study.
    
 <p align="center">
<img src="imgs/3.PNG" height="300" weight="500"/>
<p align="center">
 

   
   3. If you have some control, then you have a **quasi-experiment**. One example of this is when a video game company rolls out
a patch to modify character and item attributes.This may then have an effect on character and item popularity, since everyone is affected in the same way and We only have one group to track and there's no control group and in our analysis, we can only compare the games ecosystem from before the patch and from after the patch.  If we do see changes then there is the possibility for other factors to have caused these changes not just the patch itself. 

 <p align="center">
<img src="imgs/4.PNG" height="300" weight="500"/>
<p align="center">
 
Another classic example of the quasi-experiment is if a researcher wants to test some new supplemental materials for a high school course. If they select two different schools, one with the new materials and one without, we have a quasi-experiment since the differing qualities of students or teachers at those schools might have an effect on the outcomes. Ideally, we'd like to match the two schools before the test as closely as possible, but we can't call it a true experiment since the assignment of student to school can't be considered random.


## 2. Types of Experiment

Most of the time, when you think of an experiment, you think of a **between-subjects experiment**. In a between-subjects experiment, each unit only participates in, or sees, one of the conditions being used in the experiment. The simplest of these has just two groups or conditions to compare. In one group, we have either **no manipulation, or maintenance of the status**. This is like providing a known drug treatment, or an old version of a website. This is known as **the control group**. The other group **includes the manipulation** we wish to test, such as a new drug or new website layout. This is known as our **experimental group**. We can compare the outcomes between groups (e.g. recovery time or click-through rate) in order to make a judgement about the effect of our manipulation. (Since we have an experiment, we'll randomly assign each unit to either the control or experimental group.) **For web-based experiments, this kind of basic experiment design is called an A/B test**: the "A" group representing the old control, and "B" representing the new experimental change.

**Note:** We aren't limited to just two groups. We could have multiple experimental groups to compare, rather than just one control group and one experimental group. This could form an A/B/C test for a web-based experiment, with control group "A" and experimental groups "B" and "C".


 <p align="center">
<img src="imgs/5.PNG" height="300" weight="500"/>
<p align="center">
 

If an individual completes all conditions, rather than just one, this is known as **a within-subjects design**. Within-subjects designs are also known as **repeated measures designs**. By measuring an individual's output in all conditions, we know that the distribution of features in the groups will be equivalent. We can account for individuals' inclinations in our analysis. For example, if an individual rates three different color palettes for a product, we can know if a high rating for one palette is particularly good compared to the others (e.g. 10 vs. 5, 6) or if it's not a major distinction (e.g. 10 vs. 8, 9).

Randomization still has a part in the within-subjects design in the order in which individuals complete conditions. This is important to reduce potential bias effect. One other downside of the within-subjects design is that it's not always possible to pull off a within-subjects design. For example, when a user visits a website and completes their session, we usually can't guarantee when they'll come back. The purpose of their following visit also might not be comparable to their first. It can take a lot more effort in control in order to set up an effective within-subjects design.


**Note:** As noted at the start, the goal of sampling is to use a subset of the whole population to make inferences about the full population, so that we didn't need to record data from everyone. To that end, **probabilistic sampling techniques** were described above try to obtain a sample that was representative of the whole. However, it's useful to note that there also exist **non-probabilistic sampling techniques** that simplify the sampling process, at the risk of harming the validity of your results.



## 3. Types of Sampling

 If you need to perform a survey of a population, it could be unreasonable in both time and money costs to try and collect thoughts from every single person in the population. This is where sampling comes in. The goal of sampling is to only take a subset of the population, using the responses from that subset to make an inference about the whole population. Here, we'll cover two basic probabilistic techniques that are commonly used.
 
 

* The simplest of these approaches is **simple random sampling**. In a simple random sample, each individual in the population has an equal chance of being selected. We just randomly make draws from the population until we have the sample size desired; your sample size depends on the level of uncertainty you are willing to have about the collected data. Since everyone has an equal chance of being drawn, we can expect the feature distribution of selected units to be similar to the distribution of the population as a whole. In addition, a simple random sample is easy to set up.

* It is possible that certain groups are underrepresented in a simple random sample, especially those that make up a low proportion of the population. If there are certain rarer subgroups of interest, it can be worth adding one additional step and performing **stratified random sampling**. In a stratified random sample, we need to first divide the entire population into disjoint groups and each individual must be a part of one group. Then, from each group, you take a simple random sample. In a proportional sample, the sample size is proportional to how large the group is in the full population.
 <p align="center">
<img src="imgs/6.PNG" height="300" weight="500"/>
<p align="center">
 
 ## 4. ways of measuring outcomes 
 
 The goals of your study may not be the same as the way you evaluate the study's success. Perhaps this is because the goal is something that can't be measured directly. Let's say that you have an idea of a website addition that improves user satisfaction. How should we measure this? In order to evaluate whether or not this improvement has happened, you need to have a way to objectively measure the effect of the addition. For example, you might include a survey to random users to have them rate their website experience on a 1-10 scale. If the addition is helpful, then we should expect the average rating to be higher for those users who are given the addition, versus those who are not. The rating scale acts as a concrete way of measuring user satisfaction. These objective features by which you evaluate performance are known as **evaluation metrics**.
 
 As a rule of thumb, it's a good idea to consider the goals of a study separate from the evaluation metrics. This provides a couple of useful benefits:

* First, this makes it clear that the metric isn't the main point of a study: it's the implications of the metric relative to the goal that matters. This is especially important if a metric isn't directly attached to the goal. For example, measuring students' confidence going into a standardized test might be a proxy for the goal of test preparedness, in the absence of being able to get their test scores directly or in a timely fashion.

* Secondly, having the metric separate from the goal can clarify the purpose of conducting the study or experiment. It makes sure we can answer the question of why we want to run a study or experiment. From the above example, we aren't measuring confidence just to make people feel good about themselves: we're doing it to try and improve their actual performances.

**Note:** You might hear other terminology for goals and evaluation metrics than those used in this section. In the social sciences, it's common to hear a **"construct" as analogous to the goal or objective under investigation** and **the "operational definition" as the way outcomes are measured**.


