Despite all of the activities that we've talked about so far--communicating, coordinating, planning, designing, architecting--really, most of a software engineers time is spent reading code<maalej14>. Sometimes this is their own code, which makes this reading easier. Most of the time, it is someone else's code, whether it's a teammate's, or part of a library or API you're using. We call this reading *program comprehension*.
		
Being good at program comprehension is a critical skill. You need to be able to read a function and know what it will do with its inputs; you need to be able to read a class and understand its state and functionality; you also need to be able to comprehend a whole implementation, understanding its architecture. Without these skills, you can't test well, you can't debug well, and you can't fix or enhance the systems you're building or maintaining. In fact, studies of software engineers' first year at their first job show that a significant majority of their time is spent trying to simply comprehend the architecture of the system they are building or maintaining and understanding the processes that are being followed to modify and enhance them<dagenais10>.
		
What's going on when developers comprehend code? Usually, developers are trying to answer questions about code that help them build larger models of how a program works. Because program comprehension is hard, they avoid it when they can, relying on explanations from other developers rather than trying to build precise models of how a program works on their own<roehm12>. When they do try to comprehend code, developers are usually trying to answer questions. Several studies have many general questions that developers must be able to answer in order to understand programs<sillito06,latoza10>. Here are nearly forty common questions that developers ask:
		
1. Which type represents this domain concept or this UI element or action?
2. Where in the code is the text in this error message or UI element?
3. Where is there any code involved in the implementation of this behavior?
4. Is there an entity named something like this in that unit (for example in a project, package or class)?
5. What are the parts of this type?
6. Which types is this type a part of?
7. Where does this type fit in the type hierarchy?
8. Does this type have any siblings in the type hierarchy?
9. Where is this field declared in the type hierarchy?
10. Who implements this interface or these abstract methods?
11. Where is this method called or type referenced?
12. When during the execution is this method called?
13. Where are instances of this class created?
14. Where is this variable or data structure being accessed?
15. What data can we access from this object?
16. What does the declaration or definition of this look like?
17. What are the arguments to this function?
18. What are the values of these arguments at runtime?
19. What data is being modified in this code?
20. How are instances of these types created and assembled?
21. How are these types or objects related?
22. How is this feature or concern (object ownership, UI control, etc) implemented?
23. What in this structure distinguishes these cases?
24. What is the "correct" way to use or access this data structure?
25. How does this data structure look at runtime?
26. How can data be passed to (or accessed at) this point in the code?
27. How is control getting (from here to) here?
28. Why isn't control reaching this point in the code?
29. Which execution path is being taken in this case?
30. Under what circumstances is this method called or exception thrown?
31. What parts of this data structure are accessed in this code?
32. How does the system behavior vary over these types or cases?
33. What are the differences between these files or types?
34. What is the difference between these similar parts of the code (e.g., between sets of methods)?
35. What is the mapping between these UI types and these model types?
36. How can we know this object has been created and initialized correctly?

If you think about the diversity of questions in this list, you can see why program comprehension requires expertise. You not only need to understand programming languages quite well, but you also need to have strategies for answering all of the questions above (and more) quickly, effectively, and accurately.

So how do developers go about answering these questions? Studies comparing experts and novices show that experts use prior knowledge that they have about architecture, design patterns, and the problem domain a program is built for to know what questions to ask and how to answer them, whereas novices use surface features of code, which leads them to spend considerable time reading code that is irrelevant to a question<vonmayrhauser94,latoza07>. Reading and comprehending source code is fundamentally different from those of reading and comprehending natural language<binkley13>; what experts are doing is ultimately reasoning about *dependencies* between code<weiser81>. Dependencies include things like *data dependencies* (where a variable is used to compute something, what modifies a data structure, how data flows through a program, etc.) and *control dependencies* (which components call which functions, which events can trigger a function to be called, how a function is reached, etc.). All of the questions above fundamentally get at different types of data and control dependencies. In fact, theories of how developers navigate code by following these dependencies are highly predictive of what information a developer will seek next<fleming13>, suggesting that expert behavior is highly procedural. This work, and work explicitly investigating the role of identifier names<lawrie06>, finds that names are actually critical to facilitating higher level comprehension of program behavior.

Of course, program comprehension is not an inherently individual process either. Expert developers are resourceful, and frequently ask others for explanations of program behavior. Some of this might happen between coworkers, where someone seeking insight asks other engineers for summaries of program behavior, to accelerate their learning<ko07>. Others might rely on public forums, such as Stack Overflow, for explanations of API behavior<mamykina11>. These social help seeking strategies are strongly mediated by a developers' willingness to express that they need help to more expert teammates. Some research, for example, has found that junior developers are reluctant to ask for help out of fear of looking incompetent, even when everyone on a team is willing to offer help and their manager prefers that the developer prioritize productivity over fear of stigma<begel08>. And then, of course, learning is just hard. For example, one study investigated the challenges that developers face in learning new programming languages, finding that unlearning old habits, shifting to new language paradigms, learning new terminology, and adjusting to new tools all required materials that could bridge from their prior knowledge to the new language, but few such materials existed<shrestha20>. These findings suggest the critical importance of teams ensuring that newcomers view them as psychologically safe places, where vulnerable actions like expressing a need for help will not be punished, ridiculed, or shamed, but rather validated, celebrated, and encouraged.

While much of program comprehension is individual and social skill, some aspects of program comprehension are determined by the design of programming languages. For example, some programming languages result in programs that are more comprehensible. One framework called the _Cognitive Dimensions of Notations_<green89> lays out some of the tradeoffs in programming language design that result in these differences in comprehensibility. For example, one of the dimensions in the framework is *consistency*, which refers to how much of a notation can be _guessed_ based on an initial understanding of a language. JavaScript has low consistency because of operators like `==`, which behave differently depending on what the type of the left and right operands are. Knowing the behavior for Booleans doesn't tell you the behavior for a Boolean being compared to an integer. In contrast, Java is a high consistency language: `==` is only ever valid when both operands are of the same type.

These differences in notation can have some impact. Encapsulation through data structures leads to better comprehension that monolithic or purely functional languages<woodfield81,bhattacharya11>. Declarative programming paradigms (like CSS or HTML) have greater comprehensibility than imperative languages<salvaneschi14>. Statically typed languages like Java (which require developers to declare the data type of all variables) result in fewer defects<ray14>, better comprehensibility because of the ability to construct better documentation<endrikat14>, and result in easier debugging<hanenberg13>. In fact, studies of more dynamic languages like JavaScript and Smalltalk<callaú13> show that the dynamic features of these languages aren't really used all that much anyway. Despite all of these measurable differences, the impact of notation seems to be modest in practice<ray14>. All of this evidence suggests that that the more you tell a compiler about what your code means (by declaring types, writing functional specifications, etc.), the more it helps the other developers know what it means too, but that this doesn't translate into huge differences in defects.		

Code editors, development environments, and program comprehension tools can also be helpful. Early evidence showed that simple features like syntax highlighting and careful typographic choices can improve the speed of program comprehension<baecker88>. I have also worked on several tools to support program comprehension, including the Whyline, which automates many of the more challenging aspects of navigating dependencies in code, and visualizes them<ko09>:

|https://www.youtube.com/embed/pbElN8nfe3k|The Whyline for Java|The Whyline for Java, a debugging tool that faciliates dependency navigation|Amy J. Ko|

The path from novice to expert in program comprehension is one that involves understanding programming language semantics exceedingly well and reading _a lot_ of code, design patterns, and architectures. Anticipate that as you develop these skills, it will take you time to build robust understandings of what a program is doing, slowing down your writing, testing, and debugging.