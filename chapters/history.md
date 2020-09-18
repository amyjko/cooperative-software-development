Computers haven't been around for long. If you read one of the many histories of computing and information, such as James Gleick's _The Information_<gleick11>, Jonathan Grudin's _From Tool to Partner: The Evolution of Human-Computer Interaction_<grudin17>, or Margo Shetterly's _Hidden Figures_<shetterly17>, you'll learn that before _digital_ computers, computers were people, calculating things manually. And that _after_ digital computers, programming wasn't something that many people did. It was reserved for whoever had access to the mainframe and they wrote their programs on punchcards like the one above. Computing was in no way a ubiquitous, democratized activity--it was reserved for the few that could afford and maintain a room-sized machine.

Because programming required such painstaking planning in machine code and computers were slow, most programs were not that complex. Their value was in calculating things faster than a person could do by hand, which meant thousands of calculations in a minute rather than one calculation in a minute. Computer programmers were not solving problems that had no solutions yet; they were translating existing solutions (for example, a quadratic formula) into machine instructions. Their power wasn't in creating new realities or facilitating new tasks, it was accelerating old tasks.
	
The birth of software engineering, therefore, did not come until programmers started solving problems that _didn't_ have existing solutions, or were new ideas entirely. Most of these were done in academic contexts to develop things like basic operating systems and methods of input and output. These were complex projects, but as research, they didn't need to scale; they just needed to work. It wasn't until the late 1960s when the first truly large software projects were attempted commercially, and software had to actually perform.

The IBM 360 operating system was one of the first big projects of this kind. Suddenly, there were multiple people working on multiple components, all which interacted with one another. Each part of the program needed to coordinate with the others, which usually meant that each part's _authors_ needed to coordinate, and the term _software engineering_ was born. Programmers and academics from around the world, especially those who were working on big projects, created conferences so they could meet and discuss their challenges. In the [first software engineering conference|http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1968.PDF] in 1968, attendees speculated about why projects were shipping late, why they were over budget, and what they could do about it. There was a word for the phrase, and many questions, but few answers.
		
At the time, one of the key people behind pursuing these answers was [Margaret Hamilton|https://en.wikipedia.org/wiki/Margaret_Hamilton_(scientist)], a computer scientist who was Director of the Software Engineering Division of the MIT Instrumentation Laboratory. One of the lab's key projects in the late 1960's was developing the on-board flight software for the Apollo space program. Hamilton led the development of error detection and recovery, the information displays, the lunar lander, and many other critical components, while managing a team of other computer scientists who helped. It was as part of this project that many of the central problems in software engineering began to emerge, including verification of code, coordination of teams, and managing versions. This led to one of her passions, which was giving software legitimacy as a form of engineering--at the time, it was viewed as routine, uninteresting, and simple work. Her leadership in the field established the field as a core part of systems engineering.

The first conference, the IBM 360 project, and Hamilton's experiences on the Apollo mission identified many problems that had no clear solutions:
		
* When you're solving a problem that doesn't yet have a solution, what is a good process for building a solution?
* When software does so many different things, how can you know software "works"?
* How can you make progress when _no one_ on the team understands every part of the program?
* When people leave a project, how do you ensure their replacement has all of the knowledge they had?
* When no one understands every part of the program, how do you diagnose defects?
* When people are working in parallel, how do you prevent them from clobbering each other's work?
* If software engineering is about more than coding, what skills does a good coder need to have?
* What kinds of tools and languages can accelerate a programmers work and help them prevent mistakes?
* How can projects not lose sight of the immense complexity of human needs, values, ethics, and policy that interact with engineering decisions?

As it became clear that software was not an incremental change in technology, but a profoundly disruptive one, countless communities began to explore these questions in research and practice. Black American entreprenuers began to explore how to use software to connect and build community well before the internet was ubiquitous, creating some of the first web-scale online communities and forging careers at IBM, ultimately to be suppressed by racism in the workplace and society<mcilwain19>. White entreprenuers in Silicon Valley began to explore ways to bring computing to the masses, bolstered by the immense capital investments of venture capitalists, who saw opportunities for profit through disruption<kenney00>. And academia, which had helped demonstrate the feasibility of computing and established its foundations, began to invent the foundational tools of software engineering including, version control systems, software testing, and a wide array of high-level programming languages such as Fortran<metcalf02>, LISP<mccarthy78>, C++<stroustrup96> and Smalltalk<kay96>, all of which inspired the design of today's most popular languages, including Java, Python, and JavaScript. And throughout, despite the central role of women in programming the first digital computers, managing the first major software engineering projects, and imagining how software could change the world, women were systematically excluded from all of these efforts, their histories forgotten, erased, and overshadowed by pervasive sexism in commerce and government<abbate12>.

While technical progress has been swift, progress on the _human_ aspects of software engineering, have been more difficult to understand and improve. One of the seminal books on these issues was Fred P. Brooks, Jr.'s _The Mythical Man Month_<brooks95>. In it, he presented hundreds of claims about software engineering. For example, he hypothesized that adding more programmers to a project would actually make productivity _worse_ at some level, not better, because knowledge sharing would be an immense but necessary burden. He also claimed that the _first_ implementation of a solution is usually terrible and should be treated like a prototype: used for learning and then discarded. These and other claims have been the foundation of decades of years of research, all in search of some deeper answer to the questions above. And only recently have scholars begun to reveal how software and software engineering tends to encode, amplify, and reinforce existing structures and norms of discrimination by encoding it into data, algorithms, and software architectures<benjamin19>. These histories show that, just like any other human activity, there are strong cultural forces that shape how people engineer software together, what they engineer, and what affect that has on society.

If we step even further beyond software engineering as an activity and think more broadly about the role that software is playing in society today, there are also other, newer questions that we've only begun to answer. If every part of society now runs on code, what responsibility do software engineers have to ensure that code is right? What responsibility do software engineers have to avoid algorithmic bias? If our cars are to soon drive us around, who's responsible for the first death: the car, the driver, or the software engineers who built it, or the company that sold it? These ethical questions are in some ways the _future_ of software engineering, likely to shape its regulatory context, its processes, and its responsibilities.

There are also _economic_ roles that software plays in society that it didn't before. Around the world, software is a major source of job growth, but also a major source of automation, eliminating jobs that people used to do. These larger forces that software is playing on the world demand that software engineers have a stronger understanding of the roles that software plays in society, as the decisions that engineers make can have profoundly impactful unintended consequences.

We're nowhere close to having deep answers about these questions, neither the old ones or the new ones. We know _a lot_ about programming languages and _a lot_ about testing. These are areas amenable to automation and so computer science has rapidly improved and accelerated these parts of software engineering. The rest of it, as we shall see in this, has not made much progress. In this class, we'll discuss what we know and the much larger space of what we don't.