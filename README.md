# deep-learning-challenge
Matthew Idle
University of Minnesota Data Analytics and Visualization Bootcamp
September 2023

Overview of the analysis: The purpose of this analysis was to help the prestegious Alphabet Soup Charity better predict who will be successful with money they've been trusted with. 

Results: Using bulleted lists and images to support your answers, address the following questions:

Data Preprocessing

What variable(s) are the target(s) for your model? "IS_SUCCESFULL"
What variable(s) are the features for your model? NAME, APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT
What variable(s) should be removed from the input data because they are neither targets nor features? EIN and STATUS

How many neurons, layers, and activation functions did you select for your neural network model, and why?

I used relu twice with the higher density layer 1 and layer 2, because I felt the leaky_relu function range allowed for more values at the initial layer, then relu being only positive, might help to smooth it out a bit, then the two tanh function layers would push it down to a much smaller range, then sigmoid steps up to the plate and splits it into a binary result since the outcome is pass/fail

Initial Model:
Layer 1: units=34, activation="leaky_relu"
Layer 2: units=25,  activation="relu"
Layer 3: units=16,  activation="tanh"
Layer 4: units=7,  activation="tanh"
Output: activation="sigmoid"

I tried I don't know how many combinations, but could not get anything over 0.73


Were you able to achieve the target model performance? not with the initial model.
What steps did you take in your attempts to increase model performance?

To increase model performance, I redid all of the preprocessing steps. To determine the best column values to use, I broke "NAME", APPLICATION_TYPE", "CLASSIFICATION", and "AFFILIATION" down and created a new dataframe for each. In that dataframe I took the counts of each occurance, added up the associated success and failures, then created a 
seperate column called, "Success Rate %", which is the successes/(Failures+successes). With the success rates in hand, I looked at where the counts were, and trimmed based upon that, making sure not to trim too much.

Optimized Model:
Layer 1: units=80, activation="relu"
Layer 2: units=30,  activation="tanh"
Layer 3: units=15,  activation="tanh"
Output: activation="sigmoid"

accuracywas ~91%

to avoid overfitting I used one less layer, much smaller neuron counts compared to the input, as well as only using relu once, and tanh twice. However a lot of data was cut out.

Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.

This is a classification problem with high dimensionality, a method like ensemble learning would be much better suited for this type of problem. I would reccomend, "Random Forest"


References:
Géron, Aurélien. Hands-on Machine Learning with Scikit-Learn, Keras and Tensorflow: Concepts, Tools, and Techniques to Build Intelligent Systems. O’Reilly Media, 2019. 
 “Scikit-Learn.” Scikit, scikit-learn.org/stable/index.html. Accessed 21 Feb. 2024. 
 
Also used chat gpt for general questions and spell check