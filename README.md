
### TWEET CLASSIFICATION
Tweet Classification: Using Naive Bayes Law and bag of words assumption, we created a Classification model and trained 
it using the training data and predicted the class to which an object of words belongs to.

#### Problem Statement:
* We are using Multinomial Naive Bayes Classification wherein we create a multinomial distribution of words for each 
  class present in the training data and then predict the class to which the Object of words from the testing data 
  belongs to.

* Using the labels already given in the test data, we also find the accuracy of the classification model.We achieved an 
  accuracy of around 84 %.
	
* Firstly, we are loading the training and testing data files on the disk into 2 separate lists and then we are 
  pre-processing/cleaning the training data as well as the sanitized test data (test data without labels) by removing 
  the special characters, extra spaces, and carriage return using regex. 
	
* Secondly, we are considering all the words present in the training data after pre-processing to create a multinomial 
  distribution for each city. 
	
* Also When we encounter a word not present in a class we punish(multiply by a pseudo count around 10**-6) that class 
  by a factor. here we are smoothening the data so that no prob value is zero. 
(Reference: https://medium.com/syncedreview/applying-multinomial-naive-bayes-to-nlp-problems-a-practical-explanation-4f5271768ebf)
	
* We used Naive Bayes law To find how likely it is that an object belongs to a particular class, which states that:
  P(Posterior) prob i.e. P(Class | object of words ) = P(Likelihood) prob * P(Prior) prob 
  where the Prior prob of each class is equal to the ratio of the number of objects present in that particular category 
  to the total num of objects in the data set and likelihood probability of a word given category is the number of 
  repetitions of that particular word in that category to the total number of words in that category.We have calculated 
  the above by creating a dictionary word_freq[category][word]
	
* The class/category which gets the maximum P(Posterior) probability value for an object will be assigned to that object.
	
* Here we are ignoring the denominator (prior prob of each class) of the Bayes law because it will be constant for all 
  classes in the given data set.

* So, we are only maximizing over the numerator for all the tweets and then selecting the maximum from that.

* Also as all the words are independent of each other P(w1,w2,w3,.....) = P(w1) * P(w2) * P(w3) * ....



  

