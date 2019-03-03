1. We A/B tested two styles for a sign-up button on our company's product page. 100 visitors viewed page A, out of which 20 clicked on the button; whereas, 70 visitors viewed page B, and only 15 of them clicked on the button. Can you confidently say that page A is a better choice, or page B? Why?
* First, I caculate both possibility of A/B.
    * The posibility of page A and clicked on the button is 20/100 = 20%.
    * The posibility of page B and clicked on the button is 15/70= 21.42%
* From the posibility of A/B, I am confidently say page B is better choice.

2.  Can you devise a scheme to group Twitter users by looking only at their tweets? No demographic, geographic or other identifying information is available to you, just the messages they’ve posted, in plain text, and a timestamp for each message.
In JSON format, they look like this:

{
"user_id": 3,
"timestamp": "2016-03-22_11-31-20",
"tweet": "It's #dinner-time!"
}

Assuming you have a stream of these tweets coming in, describe the process of collecting and analyzing them, what transformations/algorithms you would apply, how you would train and test your model, and present the results.

* Collecting and analyzing: Using pandas library in python to import json file. And because we are grouping users by their tweets, so we can ignore timestamp column, because timestamp is not the factor of grouping user. 
* Transformation/ algorithim: For the message, we need to do some text preprocessing, I will first transform each word into lower case, and remove symbol, and tokenlize them. And I will apply lemmatization to make each word transform to base form. Finally, I would apply one hot encoing, to calculate the appearance count of each word for each user_id. And because this is a clustering problem, I will apply KNN algorithm to clustering users.
* How to train and test model: For train and test data, we should analyze total number of message from each user_id, if any user_id has more than two message, their tweets can use one as train data, and user another one as test data. However, if any user_id has more than three message, I would pick one as test data, and the rest of two messages should combine togther by add their one hot encoding result, because I suppose same user should group into same group. We will first train them and we will get N groups, each group has several user_id group together. As for evaluation, we will use test data to check whether each user_id can group into same group, count their accuracy.
* How to present the results: We can present the result by showing the summarize words of each group, the word shows bigger while there's larger appearance in the group. 

3. In a classification setting, given a dataset of labeled examples and a machine learning model you're trying to fit, describe a strategy to detect and prevent overfitting. 


4. Your team is designing the next generation user experience for your flagship 3D modeling tool. Specifically, you have been tasked with implementing a smart context menu that learns from a modeler’s usage of menu options and shows the ones that would be most beneficial. E.g. I often use Edit > Surface > Smooth Surface, and wish I could just right click and there would be a Smooth Surface option just like Cut, Copy and Paste. Note that not all commands make sense in all contexts, for instance I need to have a surface selected to smooth it. How would you go about designing a learning system/agent to enable this behavior?
5. Give an example of a situation where regularization is necessary for learning a good model. How about one where regularization doesn't make sense?
6. Your neighborhood grocery store would like to give targeted coupons to its customers, ones that are likely to be useful to them. Given that you can access the purchase history of each customer and catalog of store items, how would you design a system that suggests which coupons they should be given? Can you measure how well the system is performing?
7. If you were hired for your machine learning position starting today, how do you see your role evolving over the next year? What are your long-term career goals, and how does this position help you achieve them?