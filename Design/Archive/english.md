To make a course for complete beginners to learn how computers really work.

I tried my best to adhere to the guidelines layed out in the [course guidebook](https://github.com/PaperPrototype/Course-Guidebook)

One notable guideline that helped a lot was [detail_guideline_013](https://github.com/PaperPrototype/Course-Guidebook/blob/main/Guides/Details/english.md#detail_guideline_013) It's titled "Don't name it till you've explained it". This helped me make explanations less painful for people who aren't familiar with the Jargon. Lol, I even managed to explain functions and variables without using the word function or variable initially.

This course is very low level. It teaches you everything as you use it. We don't tell you to "trust us". We just show you the "Why". This leads to an intense amount of information but also a very good understanding of how everything works.

I also had to be conscious about not Over Explaining simple concepts. Like Big O Notation. The original explanation was... long and hard to read. After the suffering of onw of my in person students I reduced the explanation to a few paragraphs.

EDIT: I have thrown away most of the previous work form the lectures. The explanation of Big O Notation was not only bad, the diagrams were completely wrong!

I also focus more on getting the IDE and tooling set up on yur own computer than most CS courses, since I found that I had to figure this out myself (and it took awhile). This will also help with future courses that use C (aka "Intro to Plugins for OurMachinery").

Rather than giving you a high level explanation using abstractions, to later reveal that something is actually more low level and what we taught you was vague, I just explain things how they really are. Yes this requires low llevel explanations. But it makes understanding complex things easier since we have less to peel away and re-learn since we taught you how things *really work*. This results in everything high level making sense in *how they work* since you understand things at such a low level, you can connect the dots.



Note to Contributers.
- If you are going to add a topic to the course, don't just throw it in there and then never talk about it again. Make sure to incorporate it with the rest of the course.

- Also, if you are making a course wide change make it a pull request, so that it can be reviewed.
    - It is better to moke changes to a specific files and make pull requests for each file. This way if one change is rejected, your other changes can still be merged. 
    - If you make one big courswide change then make sure it is good! Just know coursewide changes may have a mistake, and as a result the whole pull request gets denied.


TO CONSIDER
- function pointers
- compression
- bitwise operators
- I can't remember what I wanted to cover