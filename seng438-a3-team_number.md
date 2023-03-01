**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#: 10              |  
| ------------------------- |
| Student Names:            |     
| Saina Ghasemian-Roudsari  |     
| Ana Perrone               |     
| Rachel Dalton             |     
| Isaiah Lemieux            |

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction
In this lab our group was introduced to application of white-box testing.

# 2 Manual data-flow coverage calculations for X and Y methods
DataUtilities.calculateColumnTotal:
Data flow graph:

Def-use sets per statement:

All DU-pairs per variable:

calculateColumnTotal:
du(1, 1, data) = {1}
du(1, 3, data) = {1, 2, 3}
du(1, 5, data) = {1, 2, 3, 4, 5}, {1, 2, 3, 4, 5, 6, 7, 8, 4, 5}
du(1, 5, column) = {1, 2, 3, 4, 5}, {1, 2, 3, 4, 5, 6, 7, 8, 4, 5}


For each test case show which pairs are covered:


Calculate the DU-Pair coverage:

---------------------------------------------------------------------------------------

Range.combine:

Data flow graph:

Def-use sets per statement:

All DU-pairs per variable:

calculateColumnTotal:
du(1, 1, data) = 

For each test case show which pairs are covered:


Calculate the DU-Pair coverage:

# 3 A detailed description of the testing strategy for the new unit test
We created a test plan which is in our github for planning the unit tests required, as with any testing to be done, to begin with, a plan must be created. After writing the unit tests for each method we used EclEmma to view the instruction, branch, and method coverages. Since we did do paired testing we also got the other pair to review eachothers tests. We kept reviewing tests and making changes until we were at a coverage which we felt was excelent.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)
Initial Coverage for Statement Coverage on DataUtilities is 48.7%:
<img width="866" alt="Screenshot 2023-03-01 at 10 21 27 AM" src="https://user-images.githubusercontent.com/76859857/222215570-36372536-635b-4cb6-b4d1-be48f921d4de.png">

Initial Coverage for Branch Coverage on DataUtilities is 29.7%:
<img width="886" alt="Screenshot 2023-03-01 at 10 37 27 AM" src="https://user-images.githubusercontent.com/76859857/222219008-1e5d6661-22db-44cf-9b13-dfccac74e6bd.png">

Initial Coverage for Method Coverage on DataUtilities is 60%:
<img width="827" alt="Screenshot 2023-03-01 at 10 41 57 AM" src="https://user-images.githubusercontent.com/76859857/222219497-799e5893-304f-4225-b087-9a427a6c1771.png">


# 6 Pros and Cons of coverage tools used and Metrics you report

Text…

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Text…

# 8 A discussion on how the team work/effort was divided and managed

Text…

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

Text…

# 10 Comments/feedback on the lab itself

Text…
