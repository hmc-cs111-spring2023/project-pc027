# Design notebook entry

## Last week's critique

**TODO:** Fill in this part with a summary and reflection on the critique you received for
last week's work. Answer questions such as:  How, specifically, did the feedback help
improve the project? Did the feedback point out or offer something you hadn't considered?
Did it help you make a design decision? Was it helpful in addressing the most pressing
issues in your project? How will you incorporate the feedback into your work? Will you
change something about the design, implementation, or evaluation as a result?

I struggled a lot with parsing word documents with the Java library last week. Gabriel, the class grutor, provided a potential solution to use command-line tools to turn docx into HTML or txt for easier parsing. Fortunately, I was able to pinpoint the problem to I/O issues with Prof. Wiedermann's help in Wednesday class. I planned to focus on the system aspects of the project this week, and my review partner agreed that this is the next priority. 

During Monday's critique session, I presented the AST/parser I have for the basic program to my group. I am happy to report that they did not find any glaring problems with either of the files. 

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

My work this week revolved around the system aspects of the project. I spent about a third of my time debugging I/O issues, another third on parsing word documents line-by-line and generating a docx file output, and the last third making progress on sorting lines by the rules defined in `default-config.md`.

Here is an image of the sample input:

<img width="583" alt="Screen Shot 2023-04-16 at 11 18 48 PM" src="https://user-images.githubusercontent.com/63136975/232400560-191bc122-5bd3-4666-a1d7-00f4e61c2637.png">

Currently, the system outputs the following:

<img width="495" alt="Screen Shot 2023-04-16 at 11 19 57 PM" src="https://user-images.githubusercontent.com/63136975/232400844-a951de7f-ae22-4871-8a98-c8c12bc83d73.png">
<img width="512" alt="Screen Shot 2023-04-16 at 11 20 07 PM" src="https://user-images.githubusercontent.com/63136975/232400874-8cc65000-910b-4582-a0fb-d2c1093be30d.png">

Note that:
- bullet point styling is lost in the output
- If a segment has multiple keywords, they are placed in both sections. I initially thought to place each segent in only one section, but my reviewer made a good point that the redundancy might actually be helpful for my end-users. 


## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue for my project is to link my parser with my backend. Currently, the actual sorting algorithm is parameterized, but runs on a set of default, hardcoded. keywords. Additionally, successful parsing of my end-users code gives me a `Configuration` object with a file path and a list of keywords for organizing a document. In other words, I now have the structure and data to bridge the front/middle with the back of my system together. I will start this week by mending this gap to create a complete workflow for the basic program (`ideal-simple.txt` on `sample-input.docx`).

The next issue is the sorting algorithm. I decided on doing the majority of sorting per `XWPFParagraph` (which is generated when text is separated by line breaks or bullet points) because leaving the text in this data structure as is would automatically satisfy more rules in `default-config.md` than placing the text in any Scala-based structure first. I have edge cases remaining in this sorting portion that I will tackle this week (ex. text in the paragraph that did not get selected for a keyword segment needs to go into 'uncategorized', consider bullet points as part of a previous paragraph, etc.) 

I believe I will have a bit of time remaining after tackling these two tasks. If this becomes true, I will spend the remaining time parsing the remaining symbols for my DSL (`ideal-synonyms` and `ideal-fancy`). Parsing the word document with teh additional data from these sample programs should not be difficult - the functions are already parameterized to take in configurations from those workflows. 

**What questions do you have for your critique partners? How can they best help
you?**

If my critique partner is doing I/O things with excel files this past week, I would love to see how it is being done in your system. While I was able to get reading a file working, it requires a very specific file structure. It would not be very end-user-friendly of me to require files in a specific folder, especially since my audience are non-programmers. 

I would also appreciate feedback on my current sorting approach described in the previous question. I can also discuss the code in more detail during Monday's critique session.

Finally, something I have not investigated enough, but would appreciate any early insights, is how I would get the parameter values of an object of a case class. Right now, I store everything I need from parsing under the parameters of a Configuration object. I might just need to restructure the final "output" of my AST or look into Piconot homework a little more.


**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent 8 hours outside of class for the project this week. Here is the breakdown:
- 3 hours on .docx input issues
- 4 hours on parsing .docx and generating .docx with organized output
- 1 hour refining organizing/sorting algorithm to my ideal specs


**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

My contract states that I will complete the basic deliverables for this week. I am behind this goal (I think I am about 70% complete). My contract timeline was a little ambitious, but I am confident that I can finish the basic requirements by the end of this week.
