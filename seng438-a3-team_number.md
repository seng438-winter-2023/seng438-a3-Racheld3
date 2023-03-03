**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#: 10              |  
| ------------------------- |
| Student Names:            |     
| Saina Ghasemian-Roudsari  |     
| Ana Perrone               |     
| Rachel Dalton             |     
| Isaiah Lemieux            |

# 1 Introduction
In this lab our group was introduced to application of white-box testing.

# 2 Manual data-flow coverage calculations for X and Y methods

DataUtilities.calculateColumnTotal
---------------------------------------
Data flow graph:

Def-use sets per statement:
- DEF(123) := {data, column}, USE(123) := {}
- DEF(124) := {}, USE(124) := {data}
- DEF(125) := {total}, USE(125) := {}
- DEF(126) := {rowCount}, USE(126) := {data}
- DEF(127) := {r}, USE(127) := {r, rowCount}
- DEF(128) := {n}, USE(128) := {data, r, column}
- DEF(129) := {}, USE(129) := {n}
- DEF(130) := {}, USE(130) := {total, n}
- DEF(131) := {}, USE(131) := {}
- DEF(132) := {}, USE(132) := {}
- DEF(133) := {r2}, USE(133) := {r2, rowCount}
- DEF(134) := {n}, USE(134) := {data, r2, column}
- DEF(135) := {}, USE(135) := {n}
- DEF(136) := {}, USE(136) := {total, n}
- DEF(137) := {}, USE(137) := {}
- DEF(138) := {}, USE(138) := {}
- DEF(139) := {}, USE(139) := {total}

All DU-pairs per variable:

Please note numbers refer to the relative line numbers of the method. 

Data:
1. du(0, 1, data) = {[0, 1]}
2. du(0, 3, data) = {[0, 1, 2, 3]}
3. du(0, 5, data) = {[0, 1, 2, 3, 4, 5], [0, 1, 2, 3, 4, 5, 6, 7, 8, 4, 5]}
4. du(0, 11, data) = {[0, 1, 2, 3, 4, 10, 11]}

Column:
5. du(0, 5, column) = {[0, 1, 2, 3, 4, 5], [0, 1, 2, 3, 4, 5, 6, 7, 8, 4, 5]}
6. du(0, 11, column) = {[0, 1, 2, 3, 4, 10, 11]}

//Add other variables?? total, n, r, r2...


For each test case show which pairs are covered:

- calculateColumnTotalForTwoValuesFirstColumn(): 1, 2, 3, 5
- calculateColumnTotalForThreeValuesLastColumn(): 1, 2, 3, 5
- calculateColumnTotalForOneValue(): 1, 2, 3, 5
- calculateColumnTotalForNoValues(): 1, 2, 3
- calculateColumnTotalForInvalidColumn(): 1, 2, 3, 5

Calculate the DU-Pair coverage:


Range.combine
-----------------------------------------
Data flow graph:

Def-use sets per statement:
- DEF(238) := {range1, range2}, USE(238) := {}
- DEF(239) := {}, USE(239) := {range1}
- DEF(240) := {}, USE(240) := {range2}
- DEF(241) := {}, USE(241) := {}
- DEF(242) := {}, USE(242) := {range2}
- DEF(243) := {}, USE(243) := {range1}
- DEF(244) := {}, USE(244) := {}
- DEF(245) := {l}, USE(245) := {range1, range2}
- DEF(246) := {u}, USE(246) := {range1, range2}
- DEF(247) := {}, USE(247) := {l, u}

All DU-pairs per variable:



For each test case show which pairs are covered:


Calculate the DU-Pair coverage:

# 3 A detailed description of the testing strategy for the new unit test
We created a test plan which is in our github for planning the unit tests required, as with any testing to be done, to begin with, a plan must be created. After writing the unit tests for each method we used EclEmma to view the instruction, branch, and method coverages. Since we did do paired testing we also got the other pair to review eachothers tests. We kept reviewing tests and making changes until we were at a coverage which we felt was excelent.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)
DataUtilities Initial Coverage
------------------------------------------------------------------------------
Initial Coverage for Statement Coverage on DataUtilities is 48.7%:
<img width="866" alt="Screenshot 2023-03-01 at 10 21 27 AM" src="https://user-images.githubusercontent.com/76859857/222215570-36372536-635b-4cb6-b4d1-be48f921d4de.png">

Initial Coverage for Branch Coverage on DataUtilities is 29.7%:
<img width="886" alt="Screenshot 2023-03-01 at 10 37 27 AM" src="https://user-images.githubusercontent.com/76859857/222219008-1e5d6661-22db-44cf-9b13-dfccac74e6bd.png">

Initial Coverage for Method Coverage on DataUtilities is 60%:
<img width="827" alt="Screenshot 2023-03-01 at 10 41 57 AM" src="https://user-images.githubusercontent.com/76859857/222219497-799e5893-304f-4225-b087-9a427a6c1771.png">

DataUtilities Coverage Achieved
--------------------------------------------------------------------------
Coverage for Statement Coverage on DataUtilities is 91.7%:
<img width="945" alt="Screenshot 2023-03-03 at 8 53 55 AM" src="https://user-images.githubusercontent.com/76859857/222766499-155f4a84-b1b1-478e-9559-ba0d59489117.png">

Coverage for Branch Coverage on DataUtilities is 87.5%:
<img width="969" alt="Screenshot 2023-03-03 at 8 58 57 AM" src="https://user-images.githubusercontent.com/76859857/222767490-a3d7388e-2889-46c4-b531-1cb59121d986.png">

Coverage for Method Coverage on DataUtilities is 100%: 
<img width="974" alt="Screenshot 2023-03-03 at 9 01 51 AM" src="https://user-images.githubusercontent.com/76859857/222768005-3baef5e7-6e40-4131-b370-22df7448ce47.png">


# 6 Pros and Cons of coverage tools used and Metrics you report

EclEmma does not provide a condition coverage metric, so we used analyzed the method coverage. 

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.
Requirments based test generation has the advantages of allowing the tester to be more creative in the creation of tests for methods. It is also very simple to create tests with requiremets-based test generation, as the tester just follows the requirements. The disadvatages of requirements-based test generation include a lack of confirmation to the person testing as they are not able to tell how much of the method was tested. 
Coverage-based test generation on the other hand has the advantage of the tester being able to confirm how much of the method they are covering with their tests. As well it has an advantage of having metrics to use to measure the improvement of your tests. The disadvantages of coverage-based testing is much more time being required to ensure we are reaching full coverage, and the tester must have a strong understanding of the source code to ensure they are testing all branches.

# 8 A discussion on how the team work/effort was divided and managed
We divided the manual measure data flow calculations (section 2 of report) by assigning each section of the requirments from the lab handout to one team member then getting other team members to check each others work after completion. We also divided writing unit tests for the test suite development section by Saina to write the org.jfree.data.DataUtilities tests to reach the minimum coverages required, and Rachel, Isaiah and Ana to write the org.jfree.data.Range tests to reach the minimum coverages. Then we swapped and checked over eachother work and as well helped eachother through challenges faced. As well, upon completion of the tests, we helped eachother review the tests, looking for any inconsistencies or defects in the tests.

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab
We realized as we began the creating unit test process that we had to re think our original strategy of splitting into pairs to complete org.jfree.data.DataUtilities and org.jfree.data.Range unit tests. Since Range had much more methods then DataUtilities. We found it best that one member tackle DataUtilities and get other team members to help when required and the other three memebers focus on Range methods.

# 10 Comments/feedback on the lab itself
This lab was a great way for us to expand our knowledge and apply what we have learned in class about white-box testing. It was very beneficial for us to use a coverage tool (EclEmma) and see how that worked when unit testing. Using Branch coverage really showed us how we could better write more detailed unit test to test flaws in the program we may not have recognized without using a coverage tool.
