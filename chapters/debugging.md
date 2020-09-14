Despite all of your hard work at design, implementation, and verification, your software has failed. Somewhere in its implementation there's a line of code, or multiple lines of code, that, given a particular set of inputs, causes the program to fail. How do you find those defective lines of code? You debug, and when you're doing debugging right, you do it systematically<zeller09>. And yet, despite decades of research and practice, most developers have weak debugging skills, don't know how to properly use debugging tools, and still rely in basic print statements<beller18>.

# What is debugging?
		
# Findings defects

To start, you have to *reproduce* the failure. Failure reproduction is a matter of identifying inputs to the program (whether data it receives upon being executed, user inputs, network traffic, or any other form of input) that causes the failure to occur. If you found this failure while _you_ were executing the program, then you're lucky: you should be able to repeat whatever you just did and identify the inputs or series of inputs that caused the problem, giving you a way of testing that the program no longer fails once you've fixed the defect. If someone else was the one executing the program (for example, a user, or someone on your team), you better hope that they reported clear steps for reproducing the problem. When bug reports lack clear reproduction steps, bugs often can't be fixed<bettenburg08>.
		
If you can reproduce the problem, the next challenge is to *localize* the defect, trying to identify the cause of the failure in code. There are many different strategies for localizing defects. At the highest level, one can think of this process as a hypothesis testing activity<gilmore91>.
		
* Observe failure
* Form hypothesis of cause of failure
* Devise a way to test hypothesis, such as analyzing the code you believe caused it or executing the program with the reproduction steps and stopping at the line you believe is wrong.
* If the hypothesis was supported (meaning the program failed for the reason you thought it did), stop. Otherwise, return to 1.
		
The problems with the strategy above are numerous. First, what if you can't think of a possible cause? Second, what if your hypothesis is way off? You could spend _hours_ generating hypotheses that are completely off base, effectively analyzing all of your code before finding the defect.
		
Another strategy is working backwards<ko08>.
		
* Observe failure
* Identify the line of code that caused the failing output
* Identify the lines of code that caused the line of code in step 2 and any data used on the line in step 2
* Repeat three recursively, analyzing all lines of code for defects along the chain of causality
		
The nice thing about this strategy is that you're _guaranteed_ to find the defect if you can accurately identify the causes of each line of code contributing to the failure. It still requires you to analyze each line of code and potentially execute to it in order to inspect what might be wrong, but it requires potentially less work than guessing. My dissertation work investigated how to automate this strategy, allowing you to simply click on the fault output and then immediately see all upstream causes of it<ko08>.
		
Yet another strategy called _delta debugging_ is to compare successful and failing executions of the program<zeller02>.
		
* Identify a successful set of inputs
* Identify a failing set of inputs
* Compare the differences in state from the successful and failing executions
* Identify a change to input that minimizes the differences in states between the two executions
* Variables and values that are different in these two executions contain the defect
		
This is a powerful strategy, but only when you have successful inputs and when you can automate comparing runs and identifying changes to inputs.

One of the simplest strategies is to work forward:
		
* Execute the program with the reproduction steps
* Step forward one instruction at a time until the program deviates from intended behavior
* This step that deviates or one of the previous steps caused the failure
		
This strategy is easy to follow, but can take a _long_ time because there are so many instructions that can execute.
		
For particularly complex software, it can sometimes be necessary to debug with the help of teammates, helping to generate hypotheses, identify more effective search strategies, or rule out the influence of particular components in a bug<aranda09>.
		
Ultimately, all of these strategies are essentially search algorithms, seeking the events that occurred while a program executed with a particular set of inputs that caused its output to be incorrect. Because programs execution millions and potentially billions of instructions, these strategies are necessary to reduce the scope of your search. This is where debugging *tools* come in: if you can find a tool that supports an effective strategy, then your work to search through those millions and billions of instructions will be greatly accelerated. This might be a print statement, a breakpoint debugger, a performance profiler, or one of the many advanced debugging tools beginning to emerge from research.

# Fixing defects

Once you've found the defect, what do you do? It turns out that there are usually many ways to repair a defect. How professional developers fix defects depends a lot on the circumstances: if they're near a release, they may not even fix it if it's too risky; if there's no pressure, and the fix requires major changes, they may refactor or even redesign the program to prevent the failure<murphyhill13>. This can be a delicate, risky process: in one study of open source operating systems bug fixes, 27% of the incorrect fixes were made by developers who had never read the source code files they changed, suggesting that key to correct fixes is a deep comprehension of exactly how the defective code is intended to behave<yin11>.

This risks suggest the importance of *impact analysis*, the activity of systematically and precisely analyzing the consequences of some proposed fix. This can involve analyzing dependencies that are affected by a bug fix, re-running manual and automated tests, and perhaps even running users tests to ensure that the way in which you fixed a bug does not inadvertently introduce problems with usability or workflow. Debugging is therefore like surgery: slow, methodical, purposeful, and risk-averse.