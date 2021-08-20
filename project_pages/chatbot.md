## Covid-19 Chatbot: 2nd Place Technical Project - Northrop Grumman Spring 2021 AI Challenge

**Project description:** I completed this project during the Spring semester of my first-year. The challenge was to build an Artificial Intelligence application focused around Covid-19. I was provided with an NVIDIA Jetson Nano Development Kit to aid in the development of the project. Due to a need for easily accessible yet up-to-date information regarding campus Covid protocols, I chose to develop a social chatbot aimed at providing students with an easy way of getting necessary information. After the development period, I gave a 15 minute presentation to a panel of judges from Northrop Grumman as well as submitted my code for evaluation. 

### 1. Training the Chatbot

In order to train the model, I created my own dataset consisting of 'tags' and 'patterns'. A set of patterns were associated with each tag (or category) and consisted of common queries relating to the tag. I utilized a three-layer sequential model and Stochastic gradient descent to train a classifier. The model used a bag of words approach to classify input as belonging to a specific tag.
<img src="images/thumbnail.png?raw=true"/>

### 2. Web Scraping
To provide users with real-time information, I implemented web scraping using the BeautifulSoup4 library. Depending on the user request, the chatbot would query the web for results and return the desired information. Asking the chatbot for the nearest testing site would initiate a scrape to determine local testing sites in the area and the chatbot would display that information to the user. This also allows for keeping up to date with my University's actual mask policy.
<img src="images/scrape.png?raw=true"/>


### 3. Mask Detection + Sockets
Since this project was intended to be hosted in a public location such as in a student lounge, users may or may not be expected to wear masks due to changing campus policies. If there is a mask mandate in place, the chatbot will not operate if the user is not wearing a mask. A sequential model with two dense layers was trained on a dataset of images correlating to a classification: "mask" or "no mask". To concurrently run the mask detection program alongside the chatbot and have the mask state shared between them, I implemented sockets to send the mask state at regular intervals. If there is no mask detected then the chatbot will shut down until a mask is once again detected.
<img src="images/mask.png?raw=true"/>

For a full demonstration see [Demonstration Video](https://www.youtube.com/watch?v=setG5GfccIU&ab_channel=SachinS).
