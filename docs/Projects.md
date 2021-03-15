---
layout: default
title: Projects
nav_order: 2
---

# Projects
{: .no_toc }

## Katana - Utility AI for football 2D 
[[code]](https://github.com/auxeon/katana-utility-ai) [[paper]](https://github.com/auxeon/katana-utility-ai/blob/main/KatanaResearchPaper.pdf)

<iframe width="100%" height="420" src="https://www.youtube.com/embed/rBCwW9KNq9A" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The primary objective of this research paper is to implement a utility-based AI that can play football, run simulations and be able to discern how changing the objective functions, and the utility parameters can tweak the player behaviors.

The second objective of this project is to explore utility functions in the context of a game of football and how they can control player characteristics.

A third nuanced yet more practical objective is to demonstrate a novel solution I came up with that lets you exploit preexisting behavior trees and still be able to have all the power of utility AI’s without spending upwards of 75USD that some plugins charge you.

---

## Burden - 2D puzzle solving platformer - Global Game Jam 2021
[[GGJ submission]](https://globalgamejam.org/2021/games/burden-4)

![Burden Menu](/files/burden_menu.jpg) ![[Burden Level 01]](/files/burden_level01.jpg)

This was a fun little project i built with two of my friends [Xingyu Wang](https://github.com/cjmms) and [Gerald Lee](https://github.com/gerald-lee) here at [DigiPen Institute of Technology](https://www.digipen.edu).
The Game Idea was to build a 2D platformer with a puzzle solving mechaninc.

only the small lightweight purple player ```Blip``` can jump around - but here's the catch he can't do it himself either 
he needs the help of heavyweight ```Bop``` to clear longer distance.

The key mechanic is that both players can instantly swap places at time. However you'll still be controlling a single player at a time.

This was a fun project that took us little under a day to build and design.

---

## Atom - Custom 2D Game Engine (ECS) - C++
[[code]](https://github.com/auxeon/Atom)

<iframe width="100%" height="420" src="https://www.youtube.com/embed/qDjw00-M0QI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Atom is a 2D Game Engine I am currently working with an ECS emplementation to drive its core. Will blog about it as I keep making progress. Right now it can render upto 1200 entities without significant frame drops. Next step is to Implement the Audio Manager and Level Loader followed by tools to help with debugging.

The Engine Supports Level Serialization, 3D Audio, AABB Physics and On screen controls via IMGUI. It also has support to play back audio on multiple channels.

---

## DSP - Moorer Reverb Filter - Research Paper Implementation
[[code]](https://github.com/auxeon/MoorerReverb) [[paper]](https://azrael.digipen.edu/MAT321/Moorer.pdf)

![Reverb](/files/reverb_01.png)

This was a very fun project that I worked on for a DSP course that i'm currently taking in spring 2021 - The task was to implement a Reverb filter. 

Specifically a Moorer Reverb filter that uses 6 combs filters (with a delay line and low pass filter) and a gain factor for the combs. once we're done with that we pass the samples through an all pass filter to correct the phase shift of the comb filter outputs and then pass all frequencies equally with unity gain.

The Image shows original mono recording of me saying "hello there" in the first waveform and the second waveform is the reverb'ed version of the signal  

---

## ML - Linear Regression - predit housing prices
[[code]](https://github.com/auxeon/MachineLearning/blob/main/P1_Linear_Regression/AbhikalpUnakal_P1_LinearRegression.ipynb)

This was a fun project that helped me step into the shoes of a data scientist and try to generate value from the raw data on housing prices that i had. It taught me about presenting data insights and trying to tell a story.

I put in a lot of effort and research in to trying to build a strong visual presentation and interpretation of the data along with the explanation for the math behind it. The Professor for this course loved my submission and then i decided to template the rest of my submissions along the same template as this and try to tell a story for each - although towards the end of the semester i spent lesser time on pretty graphs and more on making sure i can design good code to submit before the deadlines.

<iframe width="100%" height="500px" src="/files/Abhikalp_Unakal_P1_LinearRegression.html"></iframe>

---

## ML - Logistic Regression - predict college admits rates using gradient descent
[[code]](https://github.com/auxeon/MachineLearning/blob/main/P2_logistic_regression/AbhikalpUnakal_P2_Logistic_Regression.ipynb)

<iframe width="100%" height="500px" src="/files/Abhikalp_Unakal_P2_Logistic_Regression.html"></iframe>

---

## ML - Naive Bayes Email Spam Classifer
[[code]](https://github.com/auxeon/MachineLearning/blob/main/P3_Naive_Bayes_Spam_Filter/Abhikalp_Unakal_P3_Naive_Bayes_Spam_Filter.ipynb)

<iframe width="100%" height="500px" src="/files/Abhikalp_Unakal_P3_Naive_Bayes_Spam_Filter.html"></iframe>

--- 

## ML - Expectation Maximization Clustering - to predict geyser eruption times
[[code]](https://github.com/auxeon/MachineLearning/blob/main/P4_Clustering_EM_Geyser_Eruption/Abhikalp_Unakal_P4_clustering_EM.ipynb)

<iframe width="100%" height="500px" src="/files/Abhikalp_Unakal_P4_clustering_EM.html"></iframe>

---

## ML - Neural Networks from scratch with back propagation
[[code]](https://github.com/auxeon/MachineLearning/blob/main/P5_Neural_Networks/Abhikalp_Unakal_P5_Neural_Networks.ipynb)

This was honestly the most fun project I worked on for this course - firstly i had to implement an entire freaking neural network from scratch - with a total of 2 hidden layers to recognize the arithmetic operations on digits -I use the RELu function for my activation neuron. It was interesting to see how the back propagation algorithms with derivatives that we learnt in class could be put to practical use in a pretty sweet example. 

The later part of the project was to utilize Tensorflow and keras to generate the predictions for hand written digits. I really liked how modular the TF design to add and remove layers was ! that's probably something i would have spent more time making my code more modular if I wasn't crunched for time towards the end of the semester.

<iframe width="100%" height="500px" src="/files/Abhikalp_Unakal_P5_Neural_Networks.html"></iframe>



