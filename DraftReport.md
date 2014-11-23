#Draft Report - Empirical Track - User migration
###I. Abstract

With the advent of mobile app development technologies, many questions arises relating to the popularity of the development platform. More specifically, which platform offers more flexibility and support while developing an application? Or are there any issues related to a platform that may frustrate a developer so much so that it makes switch to another platform for development. With the introduction of forums and Question and answers (Q/A) sites like Quora, StackOverflow etc. it is becoming increasing popular to ask questions about a topic and get response from many users around the globe. Smartphones and their apps are the new way of the world, and developers are lured by their increasing popularity. But with two major platforms Apple's iOS and Google's Android competing with one another, how does a developer choose between them? In fact, would the developer be interested in either or both platforms?  
In this project, we study and identify migration of developers belonging to Android community to users belonging to iOS community and vice versa based on the dataset of StackOverflow, a sought-after online Q/A site where developers can post and answer to questions related to programming. The results shows that large number of developers continue development in one of the community and very few developers migrate from one community to another.


###II. INTRODUCTION
With the increase in internet usage, more and more informative and Q/A sites are being seeing in action. These sites that rely on crowd-sourcing knowledge provides a great platform for developers around the world to ask questions and share their experience. One such forum that is used by groups of large software developers is StackOverflow, where users can post questions related to programming. It allows users to vote questions and answers up or down which in turn allow them to earn badges, reputation points and/or some privileges on the website based on the correctness and relevance of the question or answer. Hence, the StackOverflow platform gives opportunities for even developers of mobile applications to post questions and seek answers to most common problems faced while developing them.

1. We classify a User as belonging to iOS or Android community on the basis of Tags on the Posts. So the users who posted at least one question with a particular tag, belongs to the community of that tag. Also the users who have answered questions which has Android or iOS tags belong to the community. We performed the following activities as part of our analysis.
We first classified the user as belonging to Android community, or iOS community or both the communities.
2. Identified the growth in activity (number of questions posted and answers received) for both the communities.
3. We then calculated the year-wise distribution of users in both the communities to see the growth of each of the communities relative to each other.
4. For user active in both the communities, we tabulated the count of question/answers posted by them on Android and iOS.
5. Identify users which show significant drift of activity from one community to another over the years.


###III. Data-Set and its Processing
StackOverflow provides a public dump of its database in every quarter. StackOverflow being a popular Q/A website for developers, the size of the data set is huge. We have used data.stackexchange.com to execute queries on the latest data set of StackOverflow. It allows us to run queries in a distributed fashion. This allows for faster fetching of results being computed in various clusters instead of running the same query on one single computer. The data set contains information from 31st July 2008 up till 9th November 2014.
The processing of data was done on data.stackexchange.com by adding conditions in the queries. We executed queries to identify information about the activities of Users. It allows users to download the query result in XML and CSV formats. Sample query which gives the number of Users who have posted a question on Android and not on iOS.

    select count (owneruserid)
    from 
    (Select distinct owneruserid 
    from Posts, PostTags, Tags 
    where Posts.Id= PostTags.PostID and PostTags.tagID = Tags.ID and Tags.Tagname like 'android%' 
    EXCEPT 
    Select distinct owneruserid 
    from Posts, PostTags, Tags 
    where Posts.Id= PostTags.PostID and PostTags.tagID = Tags.ID and Tags.Tagname like 'ios') as X

###IV. Analysis of Research Questions
The main goal of our project is to analyze how many developers in Android and iOS community switch between platforms over the years.
The following figure shows developer distribution in iOS and Android community. The number of developers in Android is far more than iOS.

<img src="/images/Android_vs_iOS_Venn_Diagram.jpeg" height = "350px"/>


The growth of app development have been significant in the recent years for both Android and iOS. The following graph shows the growth in Users from 2008 to 2014. We can observe that the years from 2009 to 2011, shows enormous change in curve for both iOS and Android.

![graph2](/images/User_growth.png)

iOS community became more active during the years 2011-2012 as there was about 4 times jump in number of users in iOS community over the previous year as compared to Android community, where number of user were increased by only 2.5 times. The year 2011-2012 also marked increase in number of users belonging to both the communities by almost 5.5 times, and, hence, indicates that some users migrated from one community to another. We can also that change in the number of developers contributing to both the communities is very low. This shows that developers prefer to work on one platform.

The above results were corroborated with our analysis of growth of number of questions asked on both the platforms. The graph for the same with year-wise distribution of number of questions asked is shown below:

![graph3](/images/questions_posted.png)

Based on the graph above, we can conclude that growth of the number of questions asked on iOS was about 700% in year 2011-2012 as compared to previous year. In the same year, the growth of number of questions on Android was about 320%, much less than that of iOS. These findings increased our assurance that we are on the right path of our analysis.
For the next steps of our analysis, we inspected activities of Users who have contributed to both Android and iOS. For these Users we obtained year-wise distribution of their activity. We classified a User as being migrated from one community to another if he showed significant change in number of questions and answers posted on one topic as compared to another over the years.

###V. Next Steps
We have tabulated the activity for each user belonging to both communities for each year. As suggested by professor, we have obtained difference of the activity in one community with another and downloaded this data as csv file. Now we just need to write a script to identify users which show change from positive to negative and vice versa.
Once we identify these users, we can also obtain the ratio of users who show migration versus the total users in this community.

