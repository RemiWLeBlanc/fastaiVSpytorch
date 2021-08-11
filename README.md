# fastai VS pytorch
### Remi LeBlanc and Max Shinnerl

In this project our goal is to compare a language model and classifier created by fastai to a similar model written from strach wiht pytorch. To compare these model we are looking at several different factors including performace, ease of use, and model interpretability. 

### The data
Our dataset consists of African new articles scraped from https://allafrica.com with the help of the USF mBio practicum team. These news articles are tagged by allafrica according to the article topics and themes. The dataset consists of about half a million news articles, half of which are in English and half in French. For this project we only used the English text articles. 

### The problem
The goal of our model is to identify the articles that are agricultural related. These articles are tagged with either "Food and Agriculture" or "Agribusiness". We first need to create a language model that is finetuned on African new articles. With this language model make a binary classification problem to identify articles that discuss agriculture or do not discuss agriculture. This purpose of this is to be able to take other, new African news articles, not only from allafrica, and be able to label them as agricultural or not. This is helpful to researchers who hope to understand how the African media is portraying agriculture, specifically bio-agriculture. In the future the ghope would be to make this language model available to the public for others to use who are interested in African news.

### The models
The fastai language model we used was prebuilt by fastai and is a recurrent neural network (RNN), more specifically a long-short term memory network (LSTM) inspired by https://arxiv.org/abs/1708.02182. When training the lanuage model and classifier we used all of fastai's default parameters. fastai's has a unique tokenization that invloves token that are more than just words, like captializations and beginnings of texts. 
We created four different models in pytorch. All of which were different version of RNNs, two of which were LSTMs. We used our own tokenization process and created our our hyperparameters to improve performance. 

### Interesting notes/problems
One of the most interesting aspects of this project was that only about 3% of the new articles were agriculture related. With such a class imbalance identifying the minority class became an interesting problem. We evaluting the models, we found accuracy was not a good metric to measure the models. An accuracy of 97% could be we are missing every agrculture article, we were not interested in the true negatives. Instead we used precision, recall, and f score as metrics to evaluate our models. This allowed us to better measure how our model was doing in identifying these articles. 
Another problem we ran into with this project was the size of our data set. Attempting to train on all of the articles took a very long time, especially as some of the articles were very long. Instead we trained and validated our models on a small subset of the articles. This allowed us to quickly build and improve our models and run several epochs to enchance performance and get better metrics. 

### Conclusions
The models we built from scratch did not perform as well as the model we built in fastai. Our thought was that although fastai has very well built models, they are general and do not necessary peform the best for a specific problem. When building our model from scratch in pytorch we tailed our models to improve the performance to this specific task, identifying African agricultural news articles. Despite this, fastai out performed our models. 
From our personal experiences and opinions after building models in both fastai and pytorch, we saw pros and cons of both. 
Fastai was quick to set up, and many decisions were made for you when creating the model. There tokenization and processing of the data for input into the model is all done is quick steps and is very effective. This is helpful when you are limited for time, or want to create a quick model as a baseline. However, fastai left many of the details behind the scene. Understanding what the model was doing required digging and further research. We found that fastai's documentation was at times hard to follow, not helpful, and did not provide what we were looking for.
Writing the models from scratch in pytorch allowed us to really understand what our model was doing in each step. Preprocessing the data for our tokenization and creating DataSet class for the entry into our model is very hands on. We have control over every hyperparameter our model takes. Theses models required a much deeper level of understanding, forcing and allowing us to learn and get to know our data well. However building these models took a much longer time than it did in fastai. If you want a to build a quick, easy model that performs well pytorch may not be the best route. Additionally, these handmade models did not perform as well as the models created by fastai. 

### Further explorations
As perviously mentioned, we hope to make this pretrained language model on African news artciles avaiable to anyone else interested in a problem similar to ours. This is a very niche data set and problem and we may be the first ones to create a dataset and model like this one for others to use. 
There is more work we can do to improve our pytorch models, this requires just more time to be put in. As a future project and learning experience this is a great opportinuty to see what we can do to make our models even better.
Because fastai uses pytroch under the hood, it might be interesting to compare fastai or pytorch to another machine learning library like tensorflow or keras. In this comparision we can look as many of the same things we looked at in this project like performace, ease of use, and model interpretability. 

We learned a lot from this project about pytorch and fastai, as well as NLP and RNNs and LSTMS in general. We feel we are stronger data scientists as a result of this project. We hope you could learn something too!
