# Design notebook entry

## Last week's critique

**TODO:** Fill in this part with a summary and reflection on the critique you received for
last week's work. Answer questions such as:  How, specifically, did the feedback help
improve the project? Did the feedback point out or offer something you hadn't considered?
Did it help you make a design decision? Was it helpful in addressing the most pressing
issues in your project? How will you incorporate the feedback into your work? Will you
change something about the design, implementation, or evaluation as a result?

Last week, I paired up with Everett to do peer reviews for the rest of this project as our
project description felt similar. While looking through my project pitch, Everett notes that
finding a balance between a natural language-like syntax with more traditional programming-like
symbols will be an insightful part of the project. This was a priority for me this week to
get a better idea of how writing in my DSL should look like.

Another note was made that my domain seems relatively niche and is described in terms of "mind-mapping", which was helpful to me to try looking up additional references. Everett also thought my timeline from the contract last week seems feasible. 

Here is a link to my [project plan repo](https://github.com/hmc-cs111-spring2023/cs111-project-pitch-pc027) for easy reference.

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

I have decided on creating an external DSL with Scala. The main reason for creating an external DSL is
because I wanted flexibility in designing the syntax, especially since my project is geared towards
people who may not have a programming background. I also wish I had more experience with the parsing
libraries in the Piconot assignment and go through the process of identifying any 
ambiguities in my language more thoroughly, and external DSL solve these goals better.
I picked Scala because I did want to build upon the experience I gained on the language
through this course and to have a good starting mental model of how external DSLs may 
be implemented. Crucially, there are several Java and Scala libraries that allows for 
parsing through different types of documents, such as the Java Apache POI library
for Microsoft Word documents and Scala-native libraries such as flipper and FS2 for pdfs. I have
spent some time this week setting up sbt and made sure that the Java library can be used in my
project repository.

Most of my time spent this week is creating and iterating on a few example programs written out 
in my project repo, under the /docs folder. These programs are focused on text-only inputs.
Particular observations I noted myself throughout this process is that there are a
lot of assumptions made for the simplest program written and that my syntax is very
configuration-file like. For the first point, I also included a default-config.md file under
the same folder to list out my thoughts so far on the semantics of the program. This 
also helps organize my thoughts on dealing with any tiebreakers necessary in parsing
the document using the end-user's instruction.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue for my project is getting feedback on my first syntax drafts
and working out what is the most intuitive ways that tie-breaking happens for my end-users.
Since this DSL is intended to be a coarse-grained organizer, I think it make sense that most
tie-breakers should be done within the DSL rather than through explicit syntax by the end-user.
Nonetheless, some parts will be necessary and intuitive for end-users to configure.

Another risk I would like to resolve by the end of next week is parsing and generating
a word document through the Java library. I seem to be able to import it for use, but
actually using it to do the operations I need will require digging through more
examples and documentation. Doing this part of the implementation in parallel with the design
decisions mentioned in the previous paragraphs will give me a better picture of what 
default configurations should exist and any tie-breakers that must be done explicitly
by end-users.

**What questions do you have for your critique partners? How can they best help
you?**

I would love to have a second pair of eyes on my initial design. I am worried that there
are needs by end-users that I may have missed in this initial draft, and that my syntax
leans too natural-language-like because of that. 

I would also love feedback on the default configurations I have listed so far. Is it intuitive
to you that those were the defaults? Do you think that this documentation (default-config.md)
is written in a way that makes sense for non-programmers? Are there things in default that you
believe would be more suitable as a required, explicit decision that end-users need to make
in their program?

I wrote out my examples with .txt, but I think that I should start with .docx files because
my end-users will more likely need organizing in that format. Going off my timeline, I will
complete a first draft of the AST and fill out the functions and parsers needed for my most basic 
ideal program. Do you think that these are reasonable steps to take for next week?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent 6 hours on the project this week, about 2 hours on setting up the project repo,
1 hour looking at references for design and documentation for implementation, 
and 3 hours on syntax design.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

My contract listed the following goals for the week of April 2nd:
- **create first draft of ideal dsl syntax and AST**
- deeper research into libraries for operations to parse documents in Scala and Java
- **set up project and test functions**: writing the necessary operations in GPL with the help of imported libraries, ex. I/O: open and read file in (format) + generate new file in same format
- design start symbol, production rules, terminals from ideal syntax to formalize the DSL

I was able to create a first draft of the ideal DSL, gathered extensive documentation to 
libraries that parse .doc,.docx,.pdf style documents, and began setting up my project with
test functions using the Java library for .docx formats. I did not start writing an AST and spent
more time drafting the ideal syntax instead due to the conundrums I listed earlier in this notebook,
and because of this I was unable to start "formalizing" my DSL.
