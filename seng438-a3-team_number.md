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

--------------------------------------------------------------------------

Range.combine:

Data flow graph:

Def-use sets per statement:

All DU-pairs per variable:

calculateColumnTotal:
du(1, 1, data) = 

For each test case show which pairs are covered:


Calculate the DU-Pair coverage:

# 3 A detailed description of the testing strategy for the new unit test

Text…

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

Text…

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
