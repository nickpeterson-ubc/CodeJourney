## MILESTONE 1

For project 2, we are planning to analysis a git repository and display the result as a 2d platform game for the user to explorer. For the git repository, we will analysis all the commits based on the properties such as the branch, no. of lines that were added, no. of files that were deleted and more. Once we finish the analysis, we will assign sprites such as blocks, coins, items, and even monsters to the commit based on the analysis result. Eventually we will create the game map using the sprites assigned to all the commits. The first commit will be the start of the map and the last commit will be the end of the map. Our goal is to let the user control the character in game and explore the map that were created from their git repository.<br/><br/>

We have talked with Amir and got some feedbacks on our project 2 idea. The TA suggested that our visualization idea of making a game may not be helpful at analyzing the git repository. And we should do some more researches on the existing git visualization tool.

For the next week, we are planning to do the following:

 - Do more researches on git visualization 
 - Do more researches on tools that can help us analysis the git repository
 - Finalize the project 2 idea and provide better description on its feature  
 - Finalize the language & framework we want to use for project 2


## MILESTONE 2

Since last week, we have received the feedback from Amir about our project 2 idea. Amir suggested that we want to emphysis our analysis on the source code. We have done more searching and brainstorming during the weenk and talked with our TA and Alex about our idea on the project 2. Eventually we came up with the below idea:

Code coverage tools are useful and tell us how much of an aplication is touched by an existing test suite, but sometimes we want to know exactly how a certain input makes our application behave. To solve this problem we are building a tool to generate a call graph for an application given certain inputs. This tool will perform a dynamic analysis of a Java programs. Given an entry point and set of inputs, we will execute the program, storing the input parameters, return value and possible other information about each method call. Then we will render a call graph that displays a node containing the relevant information for each method call.

For thsis project, we will have Nick, Muriel and Shobhit working on implement analysis of the Java program. Meanwhile, Francis and Roy will be working on designing and implementing the visualization. 

Roadmap for the remaning week will be:
- November 7th - 11th: Research, evaluation and initial implementation on the tools for the Java program analysis and visualizations.
- November 12th - 19th: Implementation for the Java program analysis and visualizations.
- November 20th - 24th: Integrate the Java program analysis result wiuth the visualization tool.
- November 25th - 29th: Testing, debugging and wrap up the changes.
- November 30th: Deadline of the project.

## MILESTONE 3
CHANGES: We have made some changes to our project this week. We decided to do our dynamic analysis on Javascript instead of Java. We plan to create a 
user interface where the user can write javascript code and then produce a visualization just like the one outlined in the previous milestone. We will be using a library called 
Iroh (https://github.com/maierfelix/Iroh) to do the analysis and d3.js to do our visualization both libraries require a significant amount
of programming to use.

User Study #1: We explained our analysis to a programmer with experience using Javascript and showed them a mock up of the vizualization. 
Then we asked the following questions to get feedback on our plan. The mock up visualization we used is in sample.png

Name: Peter Gawtry 
Programming Experience: 5 years of front end web development
Javascript Experience: 5 years


Questions:

1. Do you or have you used any dynamic analysis tools for Javascript?

   No.


2. Would you use this analysis tool?

   Maybe. It's nice that it will be super easy to use. Many dynamic analysis tools require a lot of set up and programming to make work. This is simple and convenient.


3. What problems would this analysis tool help you solve?

   It could be useful for understanding code written by other people. Javascript can be a little messy and hard to follow, especially if a file is large. This tool would provide an easy and fast way to see the flow of data during execution. It could also be useful for testing. Code coverage for unit tests is nice, but sometimes it's also valuable to see the actual data flow from each test.


4. Is there any information that you would add to the nodes or the edges that would make the visualization more useful?

   It would be nice to see the time spent in each function each time it's called and the total time spent in each function (including all calls to that method).


Conclusion: Peter seemed to really like the idea. He had a very good suggestions about including some analysis on the time spent in each function. We will include this in our final implementation.