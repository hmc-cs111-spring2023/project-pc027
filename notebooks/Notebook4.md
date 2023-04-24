# Design notebook entry

## Last week's critique

**TODO:** Fill in this part with a summary and reflection on the critique you received for
last week's work. Answer questions such as:  How, specifically, did the feedback help
improve the project? Did the feedback point out or offer something you hadn't considered?
Did it help you make a design decision? Was it helpful in addressing the most pressing
issues in your project? How will you incorporate the feedback into your work? Will you
change something about the design, implementation, or evaluation as a result?

I mainly asked about the sorting implementation for my document last week. My reviewer, Everett, also looked at the basic output I had last week and offered valuable insights to prioritize handling single-bullet-point-paragraphs and making the uncategorized info section less cluttered. I investigated these two threads further, and I believe that these are related issues. Consider the case where a sentence and the bullet points underneath it are considered the same "module" of information (think evidence/analysis pieces in a thesis). If the sentence contains the keyword but none of the bullet points contains the keyword, the current implementation sorts the sentence into the proper category but not the bullet point.

Therefore, I decided to simplify my ideal output slightly. Implementing a system that dynamically splits texts into segments is easy to do when the text is a Scala String, but the system would lose any styling information associated with the text. On the other hand, pre-processing the text before sorting for keywords into Word-style Paragraphs of reasonable lengths will keep any styling information, but sorting will be less nuanced because of assumptions we make in pre-processing. I asked my interviewee that helped me conceptualize this projects and friends on which they would prefer - there seems to be a slight preference for keeping stylings relatively similar. Preprocessing the information is also an easier implementation task for the remaining time.

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

I decided to pre-process the word document into segments based on the following rules to keep text segments readable:
If a Word Paragraph is a bullet point, combine them with other bullet points. There will be at most 7 bullet points per Paragraph.
If a Word Paragraph contains more than 14 lines, split sentences in the middle until there are less than or equal to 7 lines per Paragraph.

With this implementation choice, I can keep my current sorting code the same, and create a function before passing it into the sorter. The preprocessing function is currently in progress - I am currently trying to find in the documentation where I would check for bullet point styling. Figuring these decisions did take some time, and I got stuck on actually implementing it because I was very tired while doing this part. So to continue making some progress on this project, I pivoted to implementing the rest of my parser for the "fancy" syntax - optional settings like matching segment length, file output name, and synonyms.

Overall, I completed a basic implementation of my project. I can type `run ../docs/examples/ideal-fancy.txt` in `sbt` to parse required and optional configurations and generate a word document result that all required, and 1/3rd of the optional configurations within a single command. The other 2 optional configurations are implicated with preprocessing (segment length) and sorting (synonymize), both of which are a work in progress. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue for my project is figuring out where to find bullet point styling (or guess/deduce that a sentence is a bullet point based on its text). I will give this task another hour before implementing something that guesse whether something is a bullet point (lowercase start, no periods, etc.). 

Other things I would like to accomplish this week is parsing images in documents and user testing with a friend or my interviewee. In my contract, I said a low-hanging extension of this project would be to parse different document types. However, another conversation with my interviewee this weekend made it seem like at least the .pdf extension is antithetical to my project goals, which generates a documentation that would be more beneficial for end-users if they can make more changes.

I will also finish the sorting and preprocessing steps, and create a video demo before Wednesday.

**What questions do you have for your critique partners? How can they best help
you?**

Please sanity check my plan for this week!

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent about 4 hours working on the project this week. About 2 hours on preprocessing and 2 hours on finishing parsing.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

My contract expected me to do extension tasks this week, but I am behind. At least I finished the basic tasks for the project though!
