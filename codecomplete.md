# Code Complete

Code Complete was written by Steve McConnell and was originally published in 1993 with a second edition published in 2004. These notes are based on the second edition.

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

## Prerequisite 1: Problem Defintion
The problem definition is a clear statement of the problem that the system should solve.  should be a statement and should not contain a solution. For example:

- Good problem definition: *"The server crashes when we have too many concurrent users"*
- Bad problem definition: *"We should increase the number of servers to prevent the server crashing when we have too many concurrent users"*

Without a good problem definition, you could end up solving the wrong problem.

## Prerequisite 2: Requirements (AKA Spec)
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

### Requirements Checklist

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

## Prerequisite 3: Architecture