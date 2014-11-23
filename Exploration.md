Data Exploration report
=========

To study the user migration from android to ios and vice versa, first step is to categorize the user as belonging to one community.
Initially we are considering a user belongs to a community if he has posted a question with tags belonging to android/ ios.

A user can be

1.  Only Android developer.
1. Only iOS developer. 
1.  Both Android and iOS developer. 

We executed various queries on data.stackexchange.com and assembled data about number of questions in each category and the users growth over the years. 
The following graphs demonstrates information captured.


Graphs
------

1. Number of distinct Users in each category at present.

  ![graph1](/images/Android_vs_iOS_Venn_Diagram.jpeg)

2. Growth of the Users in Android and iOS development.

  ![graph2](/images/User_growth.png)

3. Number of questions posted on Android and iOS.

  ![graph3](/images/questions_posted.png)

Conclusions
----
1. We can notice an interesting incline in year 2011 where the change in number of questions on Android was 320% and on iOS it was above 700%. 
2. Very few developers work on both Android and iOS platforms (7%).
3. Number of developers in Android community using stackoverflow is almost 2.5 times as compared to developers in iOS community.
4. Year 2009 - 2011 saw tremendous increase in development in both the communities.

Future Plan
-----
1. Take User that have answered a question on these topics into account.
2. Identify User migrations from one community to another over time.

