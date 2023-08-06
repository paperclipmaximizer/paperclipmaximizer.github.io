---
layout: post
slug: Students struggle with recursion
category: cs-education
---
## Introducing the issue
*Abstract mathematical concepts can be a challenge for many undergraduate computer science learners.** Some of the most common areas of difficulty include self-similarity, parametric types and reasoning about types, recursion, recursive thinking, recursive data types, graphs, trees, cases, pattern matching, and using logic and reasoning about code.

*Even after successfully completing a hard recursion exercise or course, some learners may still feel like they don't fully understand the concepts involved.** This can be frustrating and discouraging, and it can lead to feelings of inadequacy or a desire to skip future courses that involve abstract mathematical concepts.*
- "I've done the How to Code courses, but I don't know if they worked out for me."
- "I got a 'All 20 test passed!', so thanks! I do still have difficulty understanding what I did exactly..."
- "I've made it this far (to PLB), I've spent months but I'm not improving at all."
- "I'm so tired of getting stuck on each problem for hours. I just want to move on." _(hey I've been there!)_
- "I'm just gonna get through this material quickly, or skip it if it takes too much time."
- "Who cares about these languages anyway? Why should I even use recursion? I'm not convinced."
- "After all this SML/Racket crap, ..."
- i did do htc but i struggled with it a lot, i didnt want to waste time so i moved on with intent to revisit it, i saw how valuable the course was...
- "this class almost made me quit OSSU after i forced myself to do the first part, so i skipped the second one"
- I've been stuck on this course for so long, I've read the comments and I understand it should be done but I really can't focus on it. I tried using the book instead too, but it feels like dragging myself through mud.
- Every time I tried to think about all the steps in a list with more than 2 items, my head just explode.
- With more simple problems I can imagine all the calls and the stack being built and returning values, but for this problem in particular, no way! its normal or I am missing something?
*See [here](https://github.com/ossu/computer-science/issues/1094) for context*


---
## Background
Open Source Society University (OSSU) is a self-paced, open-source curriculum for computer science education and community of learners. The curriculum is designed to provide a comprehensive and well-rounded grounding in the fundamental concepts of computer science. The OSSU curriculum is based on the degree requirements of undergraduate computer science majors, but it does not include general education requirements. This is because it is assumed that most learners will already have a foundation in these subjects.

OSSU is more than just a curriculum. It is also a community of self-learners. The community is organized on Discord, where learners connect with each other, ask questions, and get help. It is an excellent resource for learners who are struggling with a particular concept or who are looking for advice on how to approach a problem, in or outside of the curriculum. The discord provides a place for find study groups and to connect with other learners who are interested in CS or related topics and is run mostly by learners themselves in a generally very welcoming and supportive manner.

---
## The Problem
On the OSSU discord, it has become commonplace to hear students complain about the first two core CS subjects (How To Code: Simple Data and How To Code: Complex Data). A key complaint relates to learners struggles with recursion, recursive data types, and reasoning about code. This difficulty is not limited to the OSSU curriculum, but is a common problem in computer science education. Some learners report feeling like they are not making progress, or that they do not understand what they are doing correctly. They may also repeat mistakes or exhibit misunderstandings that they had in previous courses.

This difficulty can be attributed to a lack of exposure to the underlying abstract mathematical concepts, such as logic, proofs, reasoning, induction, recursive definitions, and structural induction. These concepts are often not taught in high school, and as a result, learners may not have the foundation they need to understand recursion.  In addition, the languages used in these OSSU courses, Racket and SML, can be difficult for learners who are not familiar with them. These languages use a lot of parentheses and have a different syntax than many other programming languages. This can make it difficult for learners to understand the code and to reason about how it works.  The OSSU courses do a good job of teaching the concepts of recursion and recursive data types. However, it has been argued that the curriculum could do more to prepare learners for the mathematical concepts that are necessary to understand recursion. 

This problem and a novel solution for the OSSU context was proposed [here](https://github.com/ossu/computer-science/issues/1094). In sum, it was argued that there is a strong overlap between the topics covered in Mathematics for Computer Science (MCS, offered by MIT, in the OSSU core maths curriculum) and the concepts that learners struggle with in the Core Programming courses. For example, both Unit 1 of MCS and the Core Programming courses cover recursion, recursive data types, cases, and pattern matching. By requiring Unit 1 of MCS as a prerequisite, learners would be better prepared to understand these concepts when they encounter them in the Core Programming courses. I would like to outline and propose an alternative perspective and possible solution. In my next post I will rehearse a perspective on computer science grounded in a theory-first approach to the topic relevant to learners experience.

---
## References
1. https://ieeexplore.ieee.org/document/8068262
2. https://vtechworks.lib.vt.edu/handle/10919/64249
3. The post will provide an overview and hopefully some way approach consistently recurrent issue in computer-science pedagogy. 
4. This was first raised here [https://github.com/ossu/computer-science/issues/1094]
