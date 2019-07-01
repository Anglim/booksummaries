# Code Complete

Code Complete was written by Steve McConnell and was originally published in 1993 with a second edition published in 2004. These notes are based on the second edition.

<br>

# **Part I - Laying the Foundation**
<hr>
<br>

# Chapter 1 - Welcome to Software Construction

The construction phase of software development focuses on activities such as coding, debugging and testing. It is the central activity that comes after requirements and architecture, and before systems testing.

Other terms for construction are "coding" and "programming".

Specific tasks involved in construction include:
- Verifying that the groundwork (specs, architecture, etc...) has been laid so that construction can proceed successfully
- Determining how the code will be tested
- Designing and writing classes and routines
- Creating and naming variables and constants
- Selecting control structures and organising blocks of statements
- Unit testing, integration testing and debugging your own code
- Reviewing other team member's low-level designs and code
- Polishing code through formatting and comments
- Integrating components that were created separately
- Tuning code to improve speed and reduce resources needed

<br>

# Chapter 2 - Metaphors for a Richer Understanding of Software Development

The use of metaphors in software development provides a great way to help someone understand something by relating it to an activity they already know about.

## Property building metaphor

A metaphor that works brilliantly in most cases is that of building a property. 

To start with, the phases of building a house have numerous paralells with building software:

- First, the owner will decide what sort of house they want. This is like a problem definition in software.
- Then an architect will be called in to create the design and get it approved. This is analagous with software architecture.
- Next, detailed blueprints are created specifying exactly how the house should be built. This is similar to the detailed software design phase.
- Then the builders are called in to lay foundations, frame the house, set the roof, do the plumbing and the wiring. This is like the software construction phase.
- When the builders are done, decorators, painters and landscapers and called in to beautify the property. This is similar to software optimisation.
- Throughout the entire process, various inspectors will check the state of things. This is similar to software reviews and QA.

To take the metaphor further, the size of the property that is being built affects how much time is spent on prerequisites such as architecture and design:

- If you're building a dog house, architecture and design might take up just 10 minutes before you start construction. Similarly if you're building a little hobby software project, you might start coding almost immediately.
- However, if you're building a skyscraper, much more extensive planning is needed and this phase alone might take just as long as the construction phase itself and involve hundreds of people. Similarly, if a large application is being built, it would be expected that the requirements specification would be thousands of pages long alone, with design documentation perhaps 2-3 times more extensive than that.

Another parallel is how both domains make use of pre-built items where it makes sense to do so. When building a house, you'll buy prefabricated cabinetry, a dishwasher, a refrigerator, etc rather than building them yourself. Similarly, when building software, it can be enormously cost-effective to use existing libraries and tools rather than building them from scratch.

There are numerous other parallels between property construction and software development making it a useful go-to when explaining software processes.

<br>

# Chapter 3 - Measure Twice, Cut Once: Upstream Prerequisites

Before the builders can come in to build a property, it is vital that the blueprints, surveys, permits etc... are all complete. When the builder is called in, their first step will be to verify that these are complete and correct before work begins. Similarly in software development, prerequisites such as architecture, design and project planning are critical to the success of a software project. Before any code is written, the developer should verify that these prerequisites are present and correct.

However, unlike in the construction industry, software developers are notorious for skipping prerequisites and jumping straight into coding.

## The Tendency to Skip Prerequisites

One reason prerequsites are skipped is due to lack of understanding from managers who believe developers should only be coding rather than working on prerequisites. There are a couple of solutions to this:
- Outright refuse to skip prerequisites
- Pretend to be coding and leave the manager in blissful ignorance
- Educate the manager in the reasoning for prerequisites. Use the construction analogy to explain the rationale.

Other reasons include:
- Some developers are unskilled in prerequisites
- Many developers have an urge to code right away
- Some developers don't see value in spending time on prerequisites

The problem with skipping prerequisites is that it is many, many times more costly to discover a defect later on in the project than at the beginning which is shown below.

## Data-Backed Rationale for Prerequisites

Research has proven that the earlier defects are found, the more cost effective they are to fix. Generally, problems found at the beginning of construction are 10 to 100 times less expensive than when found at the end of the process. The longer the problem stays in the process, the more damage it causes.

The below table shows the relative expense of fixing a defect depending on the phase where it was introduced and the phase where it was found.

|                    | Phase Detected ➜ |              |              |             |              |
|--------------------|----------------|--------------|--------------|-------------|--------------|
| **Phase Introduced ⬇️** | **Requirements** | **Architecture** | **Construction** | **System Test** | **Post-Release** |
| **Requirements**        | 1                | 3                | 5-10             | 10              | 10-100       |
| **Architecture**        | -                | 1                | 10               | 15              | 25-100       |
| **Construction**        | -                | -                | 1                | 10              | 10-25        |

## Up-Front vs. Iterative Prerequisites
A common question is whether prerequisites need to be done up-front or iteratively. The answer depends on the type of project.

Prerequisites should be defined up-front when:
- The requirements are stable
- The design is straightforward and well understood
- The development team is familiar with the applications area
- The project contains little risk
- Long-term predictability is important
- The cost of changing requirements, design and code downstream is likely to be high

Prerequisites should be defined in an iterative fasion when:
- The requirements are not well understood
- The design is complex and/or challenging
- The development team is unfamiliar with the applications area
- The project contains a lot of risk
- Long-term predictability is not important
- The cost of changing requirements, design and code downstream is likely to be low

In general, an iterative approach to prerequisites tends to be more useful.

## Ammount of Time to Spend on Upstream Prerequisites
The amount of time to spend on prerequisites varies depending on the project. Generally though, 10-20% of effort and 20-30% of time should be devoted to it. These figures don't include detailed design which is part of construction.

## Prerequisite 1: Problem Defintion
The problem definition is a clear statement of the problem that the system should solve. It should be a statement and should not contain a solution. For example:

- Good problem definition: *"The server crashes when we have too many concurrent users"*
- Bad problem definition: *"We should increase the number of servers to prevent the server crashing when we have too many concurrent users"*

Without a good problem definition, you could end up solving the wrong problem.

## Prerequisite 2: Requirements (Spec)
The requirements describe in detail what a software system is supposed to do.

They are important as they:
- Help ensure the user drives the system functionality rather than the dev. The user can review and agree to them and take any guesswork out of the equation.
- Help avoid arguments between devs as any disagreement about functionality can be resolved by reviewing the requirements
- Help minimise downstream changes which are costly

Stable requirements however, are very rare and most of the time, requirements will change during the latter phases.

There are multiple ways to handle changes to requirements:
- Ensure everyone understands that changing requirements *during the requirements phase* is far cheaper than changing them in latter phases.
- Ensure the requirements are good enough and if not, stop what you're doing, back up and make them right before proceeding.
- Ensure everyone knows the cost of requirement changes. Clients often get excited when they think up of a new feature and forget the cost of integrating the change. Responding with something like *"Great idea! Since it's not in the requirements document, I'll work up a revised schedule and cost estimate so you can decide whether you want it now or later"*.
- If warranted, set up a formal change-control procedure to let the client know that there is a plan for handling changes but minimises disruption to the developers.
- Use development approaches that can accomodate changes such as by using short development cycles.
- Dump the project is the requirements are so volatile that it is impossible to keep up and is costing you more than you're getting out.
- Keep the business impact in-mind when measuring the impact of a change request. Programmers who can advise on this are worth their weight in gold.

<br>

---
### Checklist: Requirements

The below is a checklist that can be used to sanity check requirements. **Not all questions will apply to a given project**.


#### Specific Functional Requirements
- Are all the inputs to the system specified, including their source, accuracy,
range of values, and frequency?
- Are all the outputs from the system specified, including their destination,
accuracy, range of values, frequency, and format?
- Are all output formats specified for Web pages, reports, and so on?
- Are all the external hardware and software interfaces specified?
- Are all the external communication interfaces specified, including handshaking, error-checking, and communication protocols?
- Are all the tasks the user wants to perform specified?
- Is the data used in each task and the data resulting from each task specified?

#### Specific Nonfunctional Requirements
- Is the expected response time, from the user’s point of view, specified for
all necessary operations?
- Are other timing considerations specified, such as processing time, datatransfer rate, and system throughput?
- Is the level of security specified?
- Is the reliability specified, including the consequences of software failure,
the vital information that needs to be protected from failure, and the strategy for error detection and recovery?
- Are minimum machine memory and free disk space specified?
- Is the maintainability of the system specified, including its ability to adapt
to changes in specific functionality, changes in the operating environment,
and changes in its interfaces with other software?
- Is the definition of success included? Of failure?

#### Requirements Quality
- Are the requirements written in the user’s language? Do the users think
so? 
- Does each requirement avoid conflicts with other requirements?
- Are acceptable tradeoffs between competing attributes specified—for
example, between robustness and correctness?
- Do the requirements avoid specifying the design?
- Are the requirements at a fairly consistent level of detail? Should any
requirement be specified in more detail? Should any requirement be specified in less detail?
- Are the requirements clear enough to be turned over to an independent
group for construction and still be understood? Do the developers think
so?
- Is each item relevant to the problem and its solution? Can each item be
traced to its origin in the problem environment?
- Is each requirement testable? Will it be possible for independent testing to
determine whether each requirement has been satisfied?
- Are all possible changes to the requirements specified, including the likelihood of each change?

#### Requirements Completeness
- Where information isn’t available before development begins, are the
areas of incompleteness specified?
- Are the requirements complete in the sense that if the product satisfies
every requirement, it will be acceptable?
- Are you comfortable with all the requirements? Have you eliminated
requirements that are impossible to implement and included just to
appease your customer or your boss?

---
<br>

## Prerequisite 3: Architecture (Top-Level Design)
Software architecture is the high-level part of software design that concerns itself with system-wide constraints. Good architecture makes construction easy whereas bad arhcitecture makes construction nearly impossible.

Here are 20 architectural components that should be considered in the doc:

### Architecture Component 1: Program Organisation
The architecture should define the major building blocks in a program. These might be a single class or a subsystem consisting of many clases. Every feature listed in the requirements should have at least one corresponding building block. 

Building blocks should have a single area of responsibility and should know as little as possible about other building blocks. How building blocks communicate should also be well defined. The architecture should define what other building blocks a building block can use directly, which ones it can use indirectly and which it should never use.

### Architecture Component 2: Major Classes
The architecture should define the major classes to be used. It should identify the responsibilities of each major class and how they interact with other classes. It should include descriptions of the class hierarchies, of state transitions, and of object persistence. If the system is large enough, it should also describe how classes are organised into subsystems.

However, the architecture does not need to specify every class in the system. A good rule to follow is the 80/20 rule - aim to specify the 20% of classes that make up 80% of the system's behaviour.

### Architecture Component 3: Data Design
The architecture should describe the major files and table designs to be used. It should specify the high-level organisation and contents of any databases used. It should explain why a single database is preferable to multiple databases or vice versa. It should identify possible interactions with other programs that access the same data, explain what views have been created on the data, etc...

Data should normally only be accessible by one subsystem or class, except through access classes or routines that allow access to the data in controlled and abstract ways.

### Architecture Component 4: Business Rules
If the architecture depends on some business rules, it should identify them and describe their impact on the system design. For example, if the system is required to keep personal customer data for no longer than 7 days, then that will likely have an impact on the architecture

### Architecture Component 5: User Interface Design
If not specified in the requirements, the architecture should specify the UI. The architecture should be modularised such that a new UI can be subtituted without affecting business rules and outputs. For example, the architecture should make it easy to remove a UI interface and replace it with a command line system - this is often useful to make software testing more convenient.

### Architecture Component 6: Resource Management
The architecture should describe a plan for managing scarce resources such as DB connections, threads and handles. It should also consider memory management if the program is memory-constrained. The architecture should estimate the resources used for nominal and extreme cases.

### Architecture Component 7: Security
Coding guidelines should be developed with security implications in mind, including approaches to handling buffers, untrusted data (user inputs, cookies, etc...), encryption, error detail, in-memory secret data and more.

### Architecture Component 8: Performance
If a concern, performance goals should be specified in the *requirements*. Then, the architecture should provide estimates and explain why they believe the performance goals are achievable. If certain areas are at risk of failing to meet the performance goals, the architecture should say so. If certain algorithms are required to meet the performance goals, the architecture should say that too. The architecture should also include O(n) space and time budgets for each class or object.

### Architecture Component 9: Scalability
The architecture should describe how the system will address growth in users, servers, database records, size of data, etc...

### Architecture Component 11: Interopability
If applicable, the architecture should specify how the system is expected to share data or resources with other software or hardware.

### Architecture Component 12: Internationalisation / Localisation
Internationalisation is the activity of supporting multiple locales. Localisation is the activity of supporting a specific local language. Sometimes internationalisation is referred to as "i18n" (i and n being the first and last letters, with 18 letters in the middle) and localisation is referred to as "L10n".

Internationalisation is important as most systems contain tons of prompts, status displays, help messages, error messages, etc. The architecture should specify how to manage the various foreign language strings with minimal impact on the code and UI such as through the use of class interfaces or resource files.

### Architecture Component 13: Input/Ouput (I/O)
The architecture should specify a look-ahead, look-behind or just-in-time reading scheme. It should describe at what level the I/O errors are detected - at the field, record, stream or file level.

### Architecture Component 14: Error Processing
Some estimate that as much as 90% of code is written for error processing, making this a vital part of a software development. Here are some questions the architecture should consider:
- Is the error processing corrective or detective. Corrective means the program should attempt to recover from the error. Detective means the program should continue as if nothing happened. But in both cases, the user should be notified of the error.
- Is error detection active or passive? An example of active would be checking user input for validity. A passive example would be where user input causes a numeric overlow error.
- How does the program propogate errors? The data that caused the error couuld be discarded, or the program could enter an error processing state, or the program could wait until all processing is complete before notifying the user of the error.
- What are the conventions for handling errors? Consistency is key to minimise a messy UI and user confusion.
- How will exceptions be handled? The architecture should consider how the errors will be logged and document and what code can throw exceptions and where they will be caught.
- At what level are errors handled? Should they be handled at point of detection or passed up the call chain?
- What is the level of responsibility of each class for validating its input data? Is each class responsible for validating its own data or is there a group of classes who handle validation? Can classes at any level assume that the data they're received is clean?
- Should the environment's built-in error handling be used or should your own be built?

### Architecture Component 15: Fault Tolerance
Fault tolerance concerns itself with increasing system reliability by detecting errors, recovering from them if possible and continuing their bad effects if not.

By way of a simplistic example, a system computing the square root of a number could be fault tolerant in several ways:
- If an answer was found to be incorrect, the system could back up to the last point where everything was correct.
- The system might have auxilary code which kicks in if it detects a problem with the primary code.
- The system could use three methods to calculate the square root and then take the average of the results.
- The system could replace the erroneous value with one it knows will not have a bad effect on the rest of the system.

Other options for fault tolerance include having the system change to a state of partial operation or degraded functionality. It could also shut down or automatically restart.

### Architecture Component 16: Architectural Feasibility
The architecture should demonstrate that the system is technically feasible. If infeasibility in any area could render the project unworkable, the architecturte should indicated how the issues have been investigated. These risks should be resolved before construction begins.

### Architecture Component 17: Overengineering
The architecture should specify whether programmers should err on the side of overengineering or on the side of keeping things simple. The reason one might overengineer is to increase robustness. It's also important to note that programmers generally overengineer due to pride and specifying the level of overengineering needed may help avoid this phenomenon.

### Architecture Component 18: Buy vs. Build
The architecture should specify what parts of the system don't need to be built from scratch but rather can use purchasable or open-source libraries/tools instead. Where custom-classes are needed instead of ready-made libraries/tools, the architecture should specify why custom capabilities are needed.

### Architecture Component 19: Reuse Decisions
If preexisting software will be used, where applicable, the architecture should specify how that software should be changed to conform to this system's architectural goals.

### Architecture Component 20: Change Strategy
The architecture should describe a strategy for handling changes. It should show possible enhancements and which are easiest to implement. It should also show how likely changes have been anticipated and can be handled by the architecture with any code changes limited to a small number of classes.

The architecture may specify that hard-coded data is instead moved to an external file/DB to maximise how many changes can be made without coding.

<br>

---
### Checklist: Architecture

The below is a checklist that can be used to sanity check the architecture. **Not all questions will apply to a given project and this list is not exhaustive**.


#### Specific Architectural Topics
- Is the overall organisation of the program clear, inlcuding a good architectural overview and justification
- Are major buildling blocks well defined, including their areas of responsibility and their interfaces to other building blocks?
- Are all the foundations listed in the requirements covered sensibly, by neither too many nor too few building blocks?
- Are the most critical classes described and justified?
- Is the data design described and justified?
- Is the database organisation and content specified?
- Are all key business rules identified and their impact on the system described?
- Is a strategy for the user inteface design described?
- Is the UI modularised so that changes won't affect the rest of the system?
- Is a strategy for handling I/O described and justified?
- Are resource-use estimates and a strategy for resource management described and justified for scarce resources like threads, database connections, handles, network bandwith, etc?
- Are the security requirements described?
- Does the architecture set space and speed budgets for each class, sub-system or functionality area?
- Does the architecture describe how scalability will be achieved?
- Does the architecture address interoperability?
- Is a strategy for internationalisation/localisation described?
- Is a coherent error handling strategy provided?
- Is the approach to fault tolerance provided?
- Has technical feasibility of all parts of the system been established?
- Is an approach to overengineering specified?
- Are necessary buy vs. build decisions included?
- Does the architecture describe how reused code will be made to conform to architectural objectives?
- Is the architecture designed to accommodate likely changes?

#### General Architectural Quality
- Does the architecture account for all the requirements?
- Is any part overarchitected or underarchitected and are expectations around this set out explicity?
- Does the whole architecture hang together cohesively?
- Is the top-level design independent of the magine and language that will be used to implement it?
- Are the motivations for all major decisions provided?
- Are you, as a programmer, comfortable with the architecture?

---
<br>

# Chapter 4 - Key Construction Decisions

### Choosing a Programming Language
The choice of progamming language affects productivity and code quality in several ways:
- Research has shown that programmers who are familiar with a langugage for 3 years or more are 30% more productive than those with equivalent experience but who are new to the language.
- High-level languages also provide greater productivity than low-level langugaes.
- Programmers are influenced by the programming language in a similar way that the Sapir-Whorf hypothesis states that your ability to think a thought depends on knowing the words capable of expressing said thought. In other words, the capabilities of a language may determine the way you think.

### Programming Conventions
It is important before construction begins that the programming conventions are spelled out such as guidelines for variable names, class names, formatting and commenting.

### Your Location on the Technology Wave
When technologies are new (early-wave), documentation will be poor with little help available online. A lot of time will be spent debugging. New versions will break your code. Integrations with external tools will be unavailable.

Mature technologies will benefit from a rich ecosystem including comprehensive error checking, powerful debugging tools, reliable performance optimisation and bug-free compilers. There will be tons of documentation available and lots of online help when needed.

It can be beneficial to work with early-wave technologies as you'll take less for granted and will develop a greater understanding of how the language works. But most importantly, you'll learn to not be "controlled" by the language - rather than limiting yourself to what the language recommends, you'll learn to first decide what you want to do and then figure out how to use the tools to achieve that.

<br>

---
### Checklist: Major Construction Practices

The below is a checklist that should be used to determine what construction practices you will follow.

#### Coding
- Have you defined how much design will be done up front and how much will be done while coding?
- Have you defined conventions for names, comments and layout?
- Have you defined practices that are implied by the architecture such as how error conditions will be handled, how security will be addressed, conventions for class interfaces, standards for reused code, how performance will be considered when coding, etc?
- Have you identified your location on the technology wave and adjusted your approach to match?

#### Teamwork
- Have you defined a version control procedure?
- Will pair programming be used and if so, how?

#### QA
- Will programmers follow TDD or if not, when will they write test cases?
- Will programmers write unit tests for all their code?
- Will programmers step through their code in a debugger before merging their code?
- Will programmers perform integration tests before merging their code?
- Will programmers perform code reviews?

#### Tools
- Have you selected a version control system?
- Have you selected a language and version?
- Have you selected a framework?
- Have you decided whether to allow use of nonstandard language features?
- Have you identified other tools you'll be using such as linters, debuggers, test frameworks, etc?

---
<br>
<br>
<br>

# **Part II - Creating High-Quality Code**
<hr>
<br>

# Chapter 5 - Design in Construction
In small, informal projects, design might look like:
- Writing a class interface in pseudocode before writing the details
- Drawing class diagrams of a few class relationships before coding
- Asking another programmer which design patterns seem like a better choice

### Design Challenges

Design has numerous challenges:

- Design often requires an initial solution in order to truly define the problem and then another solution to solve it.
- Design is a very sloppy process as its hard to know when your design is "good enough" - whether you have enough detail, what decisions to leave to at-the-keyboard, when to stop, etc...
- Design will consist of tradeoffs e.g. if a fast response rate is more important than minimising dev time, one design will be chosen whereas if quick dev time is the priority, another design will be chosen.
- Design also deliberately imposes restrictions to force simplifications of the solutions that ultimately improve the solution.
- Design is nondeterministic - there are multiple acceptable design approaches to any given program (multiple ways to skin a cat).
- Design requires trial and error, often following "rules of thumb" and techniques that might work in one project but not in another.
- Design is "emergent" - they don't spring up fully formed by someone. Rather, they evolve and improve through design reviews, informal discussions, experience writing code, changes after initial development, etc...

### Managing Complexity
Managing the complexity of a software project is critical. The reason being is that no human can possibly contain an entire program in their head. So the code should be organised in such a way that we can focus on just one part at a time. The more independent systems are, the safer it is to work on a single part.

Overall, managing complexity should be software's primary goal.

### Desirable Characteristics of Design
- **Minimal complexity**: Avoid clever, hard-to-understand designs. You should be able to safely ignore most other parts of the program when working on a specific part.
- **Ease of maintenance**: Design the system to be self-explanatory such that a maintenance programmer has no questions
- **Loose coupling**: Minimise connections between different parts of the program. Use abstractions in class interfaces, encapsulation and information hiding to design classes with minimal interconnections.
- **Extensibility**:  You should be able to enhance a program without causing problems to the underlying structure. One part should be extendable without changing other parts.
- **Reusability**: Allow for re-use of code in other systems.
- **High fan-in**: This means a high number of classes use a given class. This implies that has a system has made good use of utility classes at lower levels in the system.
- **Low-to-medium fan-out**: A given class should use a low-to-medium number of other classes. High fan-out (approx >7 classes) implies that a class is overly complex. This also applies to functions.
- **Portability**: A system should easily be moved to another environment.
- **Leanness**: Design a system so it has no extra parts. "*A book is finished not when nothing can be added but when nothing can be removed*". A programmer should never say: "*It's easy, so what harm would it cause by adding it in*".
- **Stratification**: The program should be designed such that viewing it at a particular level without needing to dip into other levels. For example, if you have some classes that each abstract away some complex code, you shouldn't need to dip into that complex code, rather you should be able to stay at the same level of abstraction across the program. The benefits of a stratified design are: 1) It compartamentalises messy code and 2) if the abstracted code requires modification, no other code should need to be modified as the interface should stay the same.
- **Standard techniques**: Use standardised, common approaches to give the system a familiar feeling and reduce intimidation for coders unfamiliar with the system.

### Levels of Design
Design should be separated into multiple levels as follows:

#### Level 1: Software System
This is the design of the entire system.

#### Level 2: Division into Subsystems or Packages
Here, all major subsystems are identified. These could be database, UI, business rules, reporting engine, etc. How subsystems are allowed to use other subsystems is decided. 

How subsystems communicate should also be decided and this should be restricted as much as possible. Otherwise the entropy of the system will increase. It's better to be too restrictive early on and relax it than vice-versa. Avoid circular relationships.

##### Common Subsystems
Below are some of the most common subsystems that tend to appear in most projects:
- **Business rules**: The laws, regulations, policies and procedures that are encoded into a system. This is the core logic of the system. For example, a Facebook business rule would be that you need to be logged in to add friends.
- **UI**: The UI should be isolated such that it can be changed without damaging the rest of the system. Typically, a UI will have several of its own subsystems.
- **Database access**: Hide the implementation details of accessing a DB to minimise low-level messiness. Centralise DB operations in one place. Make it easy to change the DB without affecting most of the program.
- **System dependencies**: Package OS dependencies in its own subsystem. For example, Windows-specific calls should be limited to the Windows environment. Then, if you move to Linux or Max, only that subsystem needs to be changed.

#### Level 3: Division into Classes
At this level, all the classes in each subsystem should be indentified. Details of how each class interacts with the rest of the system are specified and the class interface is defined. 

#### Level 4: Division into Functions
At this level, classes are divided into functions. Level 3 will define the public functions exposed in the class interface so at this level, private functions will be defined. Sometimes design at this level will result in optimisations at level 3.

#### Level 5: Internal Function Design
This involves laying out the functionality of each function. This is typically left to the programmer and may involve activities such as pseudocode and researching algorithms.

### Design Building Blocks: Heuristics
Because design is non-deterministic, it requires skillful application of heuristics i.e. ways to think about a design that may be applicable for a given project. Here are some heuristics:

#### Design Heuristic 1: Find Real-World Objects

Follow an object-oriented approach which focuses on identifying real-world and synthetic objects. The following steps can be done to design objects:

**1. Identify the objects and their attributes (methods and data)**
Typically programs are built on real-world objects. For example, a company billing system might have employees, clients, timecards and bills. Each with their own attributes e.g. employees might a name, title and billing rate.

**2. Determine what can be done to each object**
Determine the functions of each object e.g. in the billing system, the employee might have changeTitle() and changeBillingRate() functions.

**3. Determine what each object is allowed to do to other objects**
Which objects can *contain* other objects. Which objects can *inherit* other objects? For example, in a billing system, a bill would contain multiple timesheets.

**4. Determine the parts of the object which will be visible to other objects (public vs. private)**
Self-explanatory

**5. Define each object's public interface**
Define the methods and data exposed to every other object. Also think about the parts exposed to child objects via a protected interface.

#### Design Heuristic 2: Form Consistent Abstractions
Use abstractions to minimise complexity e.g. you refer to an object as a "house" rather than a collection of wood, glass and nails. On a higher level of abstraction, you might refer to a collection of houses as a "town". Classes are abstractions that allow you to ignore the detail of that class. A programmer could create abstractions at the routine-interface level, class-interface level and package-interface level

#### Design Heuristic 3: Encapsulate Implementation Details
Make it forbidden to access the details of a class.

#### Design Heuristic 4: Inheritance
Use inheritance to simplify programming. For example, if your system had part-time and full-time employees then you could have a base employee class to handle general employee operations. Then, have both a part-time and full-time employee class that inherits from that base class.

#### Design Heuristic 5: Hide secrets (Information Hiding)
This is the idea of a "black box". Esentially, a class should reveal as little as possible about its inner workings.

**Example of Information Hiding**

Suppose you had code to give each object a new ID, auto-incrementing by 1 for each new object created. You could do something like `id = ++maxId` where `maxId` is a global variable. But what if you wanted to change the logic so the IDs weren't sequential? What if you wanted to reserve ranges of IDs for special purposes? The problem is that `id = ++maxId` could turn into something much more complex in the future and then `id = ++maxId` would have to be changed everywhere its used. Instead, we could create an ID class such that the statement becomes `id = new ID()`. Behind the constructor could simply be `++maxId` at first. But if in the future the logic becomes more complex (perhaps even tens of thousands of lines long), only the code within the ID class needs to change.

Furthermore, you may later decide to change the type of ID to string. Rather than declaring the type of ID as `integer`, you could instead create a custom type defition like `IdType` which resolves to `integer`. 

#### Design Heuristic 6: Identify Areas Likely to Change

Great designers have the ability to anticipate change. Accommodating changes is one of the most challenging aspects of design. The goal is to isolate unstable changes such that the effect of change will be limited to a small part of the code. Here are the steps to prepare for change:

**1. Identify items that seem likely to change:** Good requirements will list areas that are likely to change and the probability of that. 

**2. Separate items that are likely to change:** Compartmentalise each component of step 1 into its own class.

**3. Isolate items that seem likely to change:** Design interfaces to limit the affect of change outside of the class. Ideally, external classes should be unaware of any changes inside the class. 

The system should be designed such that areas where changes are likely are easy to change. Extremely unlikely areas to change may be permitted to have more drastic consequences.

The areas typically most likely to change are:

- **Business rules:** Business rules frequently change e.g. congress changes its tax structure or an insurance company changes its rate tables. If code is designed correctly, business rules should not be strewn throughout the program but rather contained within a small part of the system.
- **Hardware dependencies:** Hardware interfaces such as screens, printers, disk drives, speakers, microphones, etc. are subject to change. Write software that can emulate the hardware and then allow the hardware/software emulator to be swapped in-and-out at any time.
- **Input and output**: File formats regularly changfe. User input fields on forms also often change.
- **Nonstandard language features:** If nonstandard extensions are used in your programming language, hide those extensions in their own class so they can be easily replaced when needed.
- **Difficult design and construction areas:** These are likely to be done poorly so its best to compartmentalise them so they can be redone and so any negatice impact on the rest of the system is minimised.
- **Status variables:** In a typical scenario, you might indicate an error with a boolean. However, you might later decide that it requires a more sophisticated implementation such as with an `enum` type e.g. `ErrorType_None`, `ErrorType_Warning` and `ErrorType_Fatal`. This can be solved by a) not using booleans but rather using `enum` and b) by using access routines rather than checking the variable directly.
- **Data-size constraints:** Don't define constants in the code e.g. `100`. Instead, use constants such as `MAX_EMPLOYEES = 100`.

#### Design Heuristic 7: Keep Coupling Loose
Coupling describes how tightly a class or routine is related to other classes or routines. An example of loose coupling in the real world is train carriages. Only a single link couples them together and beyond that, each carriage is independent and interchangeable with one another.

Here's some criteria to evalulate how coupled modules are:
- **Size:** How many connections exists between modules? A routine that takes a single parameter is less coupled that one that takes six. A class with 4 public methods is more loosely coupled than one with 40.
- **Visibility:** The more visible/obvious the connection between modules the better. Passing data as a parameter is very obvious and therefore good. Whereas modifying global data so that another module can use it is bad.
- **Flexibility:** How easy can the connections between modules change. You want something like a USB connection rather than wire and a soldering gun. An example of a poorly flexible function is `getVacationDays(employee: Employee)` which calculates the vacation days based on the employees `hiringDate` and `jobFunction`. This function is not flexible because it requires an employee to be passed in. A more flexible version would be `getVacationDays(hiringDate: Date, jobFunction: JobFunction)`.

Here are the most common types of coupling:
- **Simple-data-parameter coupling:** Two modules are simple-data-parameter coupled if all the data passed between them are primitive data types and all data is passed via function parameters. This is normal and acceptable.
- **Simple-object coupling:** A module is simple-object coupled to an object if it instantiates that object. This is fine.
- **Object-parameter coupling:** Two modules are object-parameter coupled to each other if `Object1` requires `Object2` to pass it an `Object3`. This is tighter coupling as it requires `Object2` to know about `Object3`.
- **Semantic coupling:** This is the worst kind of coupling and occurs when a module makes use of some semantic knowledge of another module's inner workings. They are undetectable by the compiler and make debugging a nightmare. Examples:
  - Module1 passes a control flag to Module2 that tells Module2 what to do. This requires Module1 to make assumptions about the inner workings of Module2. If Module2 defines a specific data type for the control flag, this is probably OK.
  - Module2 uses global data after being modified by Module1. The requires Module2 to assume that Module1 modified the data correctly and at the right time.
  - Module1's interface states that `initalise()` must be called before `routine()`. But Module2 knows that `initialise()` is called within `routine()` and so just called `routine()` without calling `initialise()` first.
  - Module1 passes `Object` to Module2. Because Module1 knows Module2 uses only three of `Object`'s seven methods, it only initalises `Object` partially.
  - Module1 passed `BaseObject` to Module2. Because Module2 knows that Module1 is actually passing a `DerivedObject` of `BaseObject`, it casts `BaseObject` to `DerivedObject`.

#### Design Heuristic 8: Look for Common Design Patterns
Design patterns provide ready-made solutions to common problems. They have several benefits:
- **Patterns reduce complexity by providing ready-made abstractions:** If you mention to another programmer that this code uses, say, the Factory Pattern, that programmer immediately understands the code without needing to spell out each line.
- **Pattern reduces errors by institutionalising details of common solutions:** Design patterns embody wisdom accumulated over years of attempting to solve problems and are thus very solid whereas novel solutions tend to contain problems.
- **Patterns provide heuristic value by suggesting design alternatives:** A designer can easily cycle through a list of patterns and check which ones fit the problem. This is easier than developing a solution from scratch.
- **Patterns streamline communication by moving the design dialog to a higher level:** Design patterns allow designers to quickly jump to a higher level of granularity e.g. two programmers could discuss whether it would be better to use a Creator or Factory pattern in some code as opposed to diving into the details of the code for each pattern before discussing.

**Common Design Patterns**
Common design patterns can be found [HERE](https://refactoring.guru/design-patterns/catalog)

#### Other Design Heuristics
- **Aim for Strong Cohesion:** All routines in a class should be centered around a single purpose. The more cohesive a class is, the less complex it will be.
- **Build Hierarchies:** A house is designed in a hierarchical manner. First the outline of the house is drawn, then windows, then doors, then more details. Hierarchies are useful in software as they allow you to focus on the level of detail you're concerned with.
- **Formalise Class Contracts:** It can be good to think of a class's interface as a contract. Typically, a contract might look like: *"If you promise to provide data x, y and z, and you promise they'll have characteristics a, b and c, I promise to perform operations 1, 2, 3 within constraints 8, 9 and 10"*. The promises clients of the class make to the class are called "preconditions" and the promises the object makes to the client are called "postconditions".
- **Assign responsibilities:** Think through how responsibilities should be assigned to objects. Asking what each object is responsible for is similar to asking what information it should hide but it can produce broader answers.
- **Design for Test:** Think about how the system will look if its designed to be tested. Do you need to separate the UI? Do you need to organise each subsystem such that dependencies are minified? Designing for test generally results in better design.
- **Avoid Failure:** Consider the ways code can fail. Don't just copy the attributes of other successful designs.
- **Choose Binding Time Conciously:** Binding time refers to the time a specific value if bound to a variable. Code that binds early tends to be simpler but less flexible. It can be beneficial to ask questions like: What if I bound these values earlier? What if I bound them later? What if I initialised the table right there in the code? What if I read the value of this variable from the user at run time?
- **Make Central Points of Control:** There should be "One Right Place" to look for any nontrivial piece of code and "One Right Place" to make a likely maintenance change. Control can be centralised in classes, routines, etc. The few places you have to look, the easier and safer code will be to change.
- **Consider Using Brute Force:** Sometimes its best to use a brute force solution rather than an elegant one that takes a long time to get right. Brute force is often sufficient.
- **Draw a Diagram:** A picture can often represent a problem far better than words and can allow you to work at a higher level of abstraction.
- **Keep your Design Modular:** The goal of modularity is to make each class a "black box". You should only need to know what goes in and what comes out. Sometimes it helpos to think about a system as a set of black boxes.

### Design Practices
Here are some best steps to yield good results.

#### Design Practice 1: Iterate
It pays to re-do the design a few times. When you come up with a first design that seems good enough, don't stop. The second attempt is nearly always better. In many instances, solving the problem one way will produce insights that will enable you to use another approach that's even better.

#### Design Practice 2: Divide and Cpnquer
Divide the program into different areas of concern and then tackle each individually.

#### Design Practice 3: Top-Down vs. Bottom-Up
With top-down, you start at a high-level of abstraction and work down. This way, your brain isn't forced to focus on too many details at once. Top-down is naturally iterative as you start with the top level and then iterate through each level.

Sometimes, the top-down approach is so abstract that it can be easier to think about it from the bottom-up. You can ask yourself "What do I need the system to do?". You might find a few responsibilities of classes e.g. you might know that a report needs to be able to print() and displayOnScreen(). After identifying some low-level responsibilities, it can then be easier to switch back to a top-down approach. 

In some cases, some low-level system will dictate the design of the entire program such as a hardware device. In which case, a bottom-up approach will be required.

Overall, they are not competing strategies but rather are mutually beneficial.

#### Design Practice 4: Exerpimental Prototyping
Sometimes, proptyping is helpful to better understand some implementation details. For example, you might need to know if a database framework will support 1,000 transactions per second under conditions X, Y and Z. A prototype could answer this. However, it's important to write the *absolute minimum* code needed and it's important that the code is treated as throwaway code, not future production code.

#### Design Practice 5: Collaborative Design
Often two heads are better than one. Collaboration could look like:
- Walking over to a colleagues desk and bouncing some ideas around
- Sitting with a colleague in a meeting room
- Do detailed design in a pair programming environment
- Schedule a formal inspection of your design
- Leave the design for a week and then come back so you'll have forgotten about it and can review it yourself
- Ask people external to the company

#### Design Practice 6: How Much Design Is Enough?
Generally, the amount of design needed is dependent on multiple of these factors:
- The experience of the programmers
- The knowledge of the programmer in the application's area
- The turnover rate of the team
- How safety-critical the application is
- How mission-critical the application is
- The project size
- The expected lifetime span of the project

Generally though, it's best to err on the side of more detail and under-polished documentation than vice-versa.


<br>

---
### Checklist: Design in Construction

#### Design Practices
- Have you iterated, selecting the best of several attempts rather than the first?
- Have you tried decomposing the system in several different ways to see which will work best?
- Have you tried both top-down and bottom-up approaches?
- Have you prototyped risk or unfamiliar parts of the system, creating absolute minimum, throwaway code as needed?
- Has your design been reviewed, formally or unformally, by others?
- Have you driven design to the point that its implementation seems obvious?
- Have you captured your design using an approriate technique such as a wiki, email, UML, code comments, etc?

#### Design Goals
- Does the design adeqately address issues that were identified at the architectural level?
- Is the design stratified into layers?
- Are you satisfied with the way the program has been decomposed into subsystems, packages and classes?
- Are you satisfied with the way the classes have been decomposed into routines?
- Are classes designed for minimal interaction with each other?
- Are classes and subsystems designed so that you can use them in other systems?
- Will the program be easy to maintain?
- Is the design lean? Are all parts of it strictly necessary?
- Does the design use standard techniques and avoid exotic, hard-to-understand elements?
- Overall, does the design minimise both accidental and essential complexity?

---
<br>

# Chapter 6 - Working Classes