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

A metaphor that works brilliantly in most cases is that of property building. 

### Property building phases are analagous with software building phases

To start with, the phases of building a house have numerous paralells with building software:

- First, the owner will decide what sort of house they want. This is like a problem definition in software.
- Then an architect will be called in to create the design and get it approved. This is analagous with software architecture.
- Next, detailed blueprints are created specifying exactly how the house should be built. This is similar to the detailed software design phase.
- Then the builders are called in to lay foundations, frame the house, set the roof, do the plumbing and the wiring. This is like the software construction phase.
- When the builders are done, decorators, painters and landscapers and called in to beautify the property. This is similar to software optimisation.
- Throughout the entire process, various inspectors will check the state of things. This is similar to software reviews and QA.

To take the metaphor further, the size of the property that is being built affects how much time is spent on prerequisites such as architecture and design:

### The size of the project affects how much planning is needed in both activities

- If you're building a dog house, architecture and design might take up just 10 minutes before you start construction. Similarly if you're building a little hobby software project, you might start coding almost immediately.
- However, if you're building a skyscraper, much more extensive planning is needed and this phase alone might take just as long as the construction phase itself and involve hundreds of people. Similarly, if a large application is being built, it would be expected that the requirements specification would be thousands of pages long alone, with design documentation perhaps 2-3 times more extensive than that.

Another parallel is how both domains make use of pre-built items where it makes sense to do so:

### Both activities make use of pre-built items
When building a house, you'll buy prefabricated cabinetry, a dishwasher, a refrigerator, etc rather than building them yourself. Similarly, when building software, it can be enormously cost-effective to use existing libraries and tools rather than building them from scratch.

There are numerous other parallels between property construction and software development making it a useful go-to when explaining software processes.

<br>

# Chapter 3 - Measure Twice, Cut Once: Upstream Prerequisites
