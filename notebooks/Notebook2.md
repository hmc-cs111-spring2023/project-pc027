# Design notebook entry

## Last week's critique

**TODO:** Fill in this part with a summary and reflection on the critique you received for
last week's work. Answer questions such as:  How, specifically, did the feedback help
improve the project? Did the feedback point out or offer something you hadn't considered?
Did it help you make a design decision? Was it helpful in addressing the most pressing
issues in your project? How will you incorporate the feedback into your work? Will you
change something about the design, implementation, or evaluation as a result?

My critique partner, Everett, made insightful comments about the tie-breaking within the semantics of my DSL. To recap, I intend for my DSL to be limited in the types of configurations end-users can program, so deciding the answer to "at which point does a segment belonging to a keyword start or end?" would require many dafaults, currently documented in `/docs/default-configs.md`. Everett commented that repeated information in an output file may actually be helpful to end-users, so a conservative approach to place sentences that seem to fit multiple keywords in multiple places is a viable (though less ideal) strategy.

My partner also agreed that an external DSL would be better suited for this project, that getting a functional parser working was a good goal this week, and that .docx file types are a good starting point for systems work after the parser works. 

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

My main goal for this week was to implement a functional parser for basic syntax (something that parses /doc/examples/ideal-sample.txt). If I had enough time left, I would work on the semantics for loading and getting information from a .docx document. 

I was able to make a working parser for ideal-sample.txt.
<img width="847" alt="Screen Shot 2023-04-10 at 7 39 27 AM" src="https://user-images.githubusercontent.com/63136975/230923514-9c024ec1-f67d-4ff8-8866-401ee3114ee1.png">

Here is a screenshot of my AST and parser files.

<img width="638" alt="Screen Shot 2023-04-10 at 7 39 52 AM" src="https://user-images.githubusercontent.com/63136975/230923599-21a02b60-b9f6-4156-9b5e-06886e28ebdd.png">
<img width="615" alt="Screen Shot 2023-04-10 at 7 41 44 AM" src="https://user-images.githubusercontent.com/63136975/230924004-bf6b0116-fd1d-4ca4-8618-f1db7e59be76.png">

Last week, I chose the Apache POI Java library to help parse word documents. I also gave an additional attempt on parsing .docx, but I did not have enough time to make significant progress on this aspect.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I believe the next logical step in my project is to implement the "backend" for the basic workflow - parsing a .docx document for its text, create the system to divide the text into keyword segments, and generating a .docx document with those segments. I foresee this taking the entirety of my time this week.

The feedback on tie-breaking from last week helped very much in imagining the outputs of my system - it would be minimally successful as long as all text in the document gets parsed, and sentences 5-7 lines away from keywords are grouped into segments. 

Some lingering implementation issues I will need to figure out this week are figuring out (1) how to add optional fields for my parser for the more advanced workflows, (2) how to best parameterize my system to be easily compatible with the configurations that end-users can specify, and (3) think of an easier way (intermediate step to creating a GUI of some sort) to feed files into my project outside of running commands in the terminal (which currently requires relative pathing, and I am not sure if all of my end-users are familiar enough with terminal to run this command easily). 


**What questions do you have for your critique partners? How can they best help
you?**
If my critique partner is at the step to parse excel documents, I would love to hear any initial errors/problems that occured - I am running into issues with parsing sample documents provided in the library (Scala is unable to find those files in the imported libraries, even though they exist in the library's GitHub repo).

Any feedback on my AST, parser, or plan for this coming week would also be fantastic!

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent 4 hours outside of class for the project this week. I will attempt to do 2 extra hours this coming week (for a total of 8 outside class hours) to make up for the lost working time.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

I was able to achieve the main goal in my contract - implement parsers to generate the AST for the basic workflow. Nonetheless, I am behind in terms of implementing systems aspects of the project in comparison to my contract. I am still optimistic about the state of my project compared to my contract, as long as I make up for the hours I did not do this coming week.
