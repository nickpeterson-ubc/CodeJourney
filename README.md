# Code Journey: A Visual Tool for Dynamic Analysis

## Why Code Journey
Code Journey dynamic analysis provides developers with a lot of useful and hard to obtain information about the execution of their program.
This includes parameters, return value, number of invocations, caller, and execution time of each function call. It is presented 
in a nice easy to understand visualization.

We performed several user studies that guided our decisions about which information to include and how to present that data.
Overall, our users indicated that this would be a useful analysis tool for Javascript developers.

## How to start
You need to run both Front-end and Back-end application to for this program. First install Node if you don't already have it on your machine.
Our frontend runs on port 3000 and the backend runs on port 9000. Please clear those ports before running Code Journey.

## Front End
Navigate to /api and run the terminal command:
```npm install && npm start```

Then navigate to /client and run:
```npm install && npm start```

Now, point your browser to localhost:3000.

## The Analysis

The code journey performs a dynamic analysis on Javascript code. It specifically looks at important information 
about each function call including parameters, return value, number of invocations, caller, and execution time. We are using a
Javascript analysis tool called Iroh to perform the analysis. This tool allows the user to add listners to the Javascript AST. The listeners get 
called when specific code characters are reach such as a return statement, function declaration, etc. We track the order of calls 
and important data like execution time using a call stack.

### Visualization

Our visualization is a call graph that shows how functions call each other. There are two types of call graphs that can be generated:

1. Compact: A compact call graph shows a single node for each function, even if the function is called multiple times. The 
    arrows contain information about how many times the function was called from each caller. Additional data is viewed in the 
    tooltip by hovering over the node. You can expand the inputs to see the parameters, return value, caller, and execution time of each call.

2. Not Compact: This call graph shows a new node for each time a function call. We find this visualization most useful for 
    small programs and small recursive and mutually recursive functions where it can be interesting and valuable to construct an
    execution tree. For larger programs with many function calls it is much better to use the compact visualization.
    
Note: we decided to implement both versions of our visualization after our user studies were inconclusive about which one would be more useful.

### Testing
The initial code in the editor provides a great example of the two visualizations and how they differ. Start by running that code 
with compact toggled on and off to see the difference. For a larger example, I encourage you to try inputting the code we
used in our user stories below. That code provides an example of how the "non-compact" version can be unusable with large programs and
how the compact version can show you information about your execution that would otherwise be very hard to obtain.

### User Studies

Note: We did several user studies for project 2. In our first user study we just interviewed the user about the visualization.
This user study was only moderately helpful, so we decided to change the user study for the remaining four users.

------------------------------
User Study 1

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

<br/><br/>
------------------------------
For the remaining user studies we gave the user a fairly complicated piece of Javascript code and asked them some questions about
it. The purpose of these first questions was just to get them thinking about what they do and do not know about the code. Then
We asked them questions about our visualization for this code to get valuable feedback and ideas.

The Code:
```
    function add(a, b) {
    		return foo(a + 1, b + 1);
    };
    function foo(a, b) {
        return bar(a + 1, b + 1);
    };
    function bar(a, b) {
        doNothing();
        let ret = 1;
        while (ret < 1000) {
        	ret += factorial(b);
        }
        return a + ret;
    }
    function doNothing() {
      console.log('do nothing');
    }
    function factorial(n) {
      doNothing();
      if (n === 1) {
        return 1;
        }
      return n * factorial(n - 1);
    }
    add(1, 1);
}
```

The Questions (primers to get the user thinking about the code, the idea is to not spend a lot of time on any individual question):
1.  How many times will bar call factorial? (No one was able to answer this correctly)
2.  How many times will factorial recurse in total?
3.  How many times is doNothing() called from Bar?
4.  How many times will doNothing() be called from factorial?

User Study 2 
Name: Kelsey Peterson
Programming Experience: 3rd year Computer Science student
Javascript Experience: <1 year

Questions:
1. Do you or have you used any dynamic analysis tools for Javascript?
    No.

2. Would you use this analysis tool?
    I would much rather use this than try to figure out by hand how many times bar will call factorial. So yes.
    
3. Would you rather see a node for each time a function is called or a single node per function?
    Interesting, before seeing the two examples I would have said one node per function makes more sense. But
    for small recursive functions I think it's cool to see the recursion tree. So, I think you should show a node for each
    function call.
    
4. Is there any information you would like to add to the visualization? 
    Yes, you should add the return value in the tooltip. 
    
Changes that we made from this user study:
    We added the return value in the tooltip.
    
    
User Study 3
Name: Danny Lyons
Programming Experience: 2nd year BCS Student
Javascript Experience: 1 year (including co-op and school)

Questions:
1. Do you or have you used any dynamic analysis tools for Javascript?
    No.

2. Would you use this analysis tool?
    Yes. It would be really fun to play with to try to generate interesting call graph. And, sometimes you want to know things
    like how many times a function was called or you need to unroll a recursive function for debugging.
    
3. Would you rather see a node for each time a function is called or a single node per function?
    Definitely one node per function. For interesting programs it will be too complicated the other way.
    
4. Is there any information you would like to add to the visualization? 
    Yes, you should add the name of the caller function to the tooltip. 
    
Changes that we made from this user study:
    We added the caller to the tooltip in the compact visualization. It's doesn't really make sense in the non-compact visualization.
    
User Study 4
Name: Mei Lew
Programming Experience: 4th year Computer Science Student
Javascript Experience: 2 years

Questions:
1. Do you or have you used any dynamic analysis tools for Javascript?
    No.

2. Would you use this analysis tool?
    Yes. It would help show the execution path in javascript files.
    
3. Would you rather see a node for each time a function is called or a single node per function?
    It doesn't really matter. Both are interesting in different ways.
    
4. Is there any information you would like to add to the visualization? 
    Not really.
    
Changes that we made from this user study:
    After this user story we realized that there was no definitive answer on whether we should include a single node per 
    functio or a single node per function call. We decided to implement both versions. We call the single node per function
    the 'compact' visualization.
    
 
