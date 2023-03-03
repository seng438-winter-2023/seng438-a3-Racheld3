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
This lab gave us our third opportunity to review and apply the different concepts and practices we have been covering in lectures, in once again, a very hands-on and interactive approach. Our goal was to continue using unit testing, but now building off of the tests created in Assignment 2 for the JFreeChart System. As we were given the code for each of the methods to be tested, this enabled us to use the white-box coverage criteria technique. This lab allowed us to gain exposure to code coverage tools in order to measure test adequacy all while designing test cases that would improve the coverage of our code.

# 2 Manual data-flow coverage calculations for X and Y methods

DataUtilities.calculateColumnTotal
---------------------------------------
Data flow graph:

![Screenshot_2023-03-03_at_9 25 10_AM](https://user-images.githubusercontent.com/101215683/222774328-73f12daa-869b-4351-89b1-c79736a74f57.png)

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

r:
7. du(4, 4, r) = {[4]}
8. du(4, 5, r) = {[4, 5]}

n (in scope of first for loop): 
9. du(5, 6, n) = {[5, 6]}
10. du(5, 7, n) = {[5, 7]}

r2: 
11. du(10, 10, r2) = {[10]}
12. du(10, 11, r2) = {[10, 11]}

n (in scope of second for loop):
13. du(11, 12) = {[11, 12]}
14. du(11, 13) = {[11, 12, 13]}


For each test case show which pairs are covered:

Please note these reference the numbers from the above DU-pair list.

- calculateColumnTotalForTwoValuesFirstColumn(): 1, 2, 3, 5, 7, 8, 9, 10
- calculateColumnTotalForThreeValuesLastColumn(): 1, 2, 3, 5, 7, 8, 9, 10
- calculateColumnTotalForOneValue(): 1, 2, 3, 5, 7, 8, 9, 10
- calculateColumnTotalForNoValues(): 1, 2, 3
- calculateColumnTotalForInvalidColumn(): 1, 2, 3, 5, 7, 8, 9, 10

Calculate the DU-Pair coverage:

    Total DU-pairs: 14
    DU-pairs covered by tests: 8
    DU-pair coverage = 8/14



Range.combine
-----------------------------------------
Data flow graph:

![Screenshot_2023-03-03_at_9 34 59_AM](https://user-images.githubusercontent.com/101215683/222805312-ef9ff8c8-a737-4c51-89c9-cafaffac5b2c.png)

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

Please note numbers refer to the relative line numbers of the method. 

range1:
1. du(0, 1, range1) = {[0, 1]}
2. du(0, 5, range1) = {[0, 1, 4, 5]}
3. du(0, 7, range1) = {[0, 1, 2, 3, 7], [0, 1, 4, 5, 6, 7], [0, 1, 4, 6, 7]}
4. du(0, 8, range1) = {[0, 1, 2, 3, 7, 8], [0, 1, 4, 5, 6, 7, 8], [0, 1, 4, 6, 7, 8]}

range2: 
5. du(0, 2, range2) = {[0, 1, 2]}
6. du(0, 4, range2) = {[0, 1, 4]}
7. du(0, 7, range2) = {[0, 1, 2, 3, 7], [0, 1, 4, 5, 6, 7], [0, 1, 4, 6, 7]}
8. du(0, 8, range2) = {[0, 1, 2, 3, 7, 8], [0, 1, 4, 5, 6, 7, 8], [0, 1, 4, 6, 7, 8]}

l:
9. du(7, 9, l) = {[7, 8, 9]}

u:
10. du(8, 9, u) = {[8, 9]}


For each test case show which pairs are covered:

Please note these reference the numbers from the above DU-pair list.

- testCombineWithFirstRangeNull(): 1, 3, 4, 5, 6, 7, 8, 9, 10
- testCombineWithSecondRangeNull(): 1, 2, 3, 4, 6, 7, 8, 9, 10
- testCombineWithTwoRanges(): 1, 3, 4, 6, 7, 8, 9, 10


Calculate the DU-Pair coverage:

    Total DU-pairs: 10
    DU-pairs covered by tests: 10
    DU-pair coverage = 10/10

# 3 A detailed description of the testing strategy for the new unit test
We created a test plan which is in our github for planning the unit tests required, as with any testing to be done, to begin with, a plan must be created. After writing the unit tests for each method we used EclEmma to view the instruction, branch, and method coverages. Since we did do paired testing we also got the other pair to review eachothers tests. We kept reviewing tests and making changes until we were at a coverage which we felt was excelent.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

DataUtilites.equals: Test Case- testTwoEqualArraysEqual()
This test case was designed to improve the testing for the method Equals in DataUtilities. Prior to writing this test the statement and branch coverage was 0%. But after writing just that one test branch coverage improved to 50%. This test case check the loop if (a.length != b.length) to see if the arrays had equal length, by going into this loop we were able to improve the coverage.

Range.constrain: Test case - testConstrainLowerValueNotContained()
This test case improved coverage for the constrain() method in Range. Prior to writing this test case, the statement, branch and method coverages were 0%. The test case tested the constrain method when the value to be constrained is less than the lower bound of the range. This test case alone increased the statement coverage to 84.0%, branch coverage to 50%, and method coverage to 100%. We used the coverage information to write two additional test cases to bring the coverage to 100% in every category. 

Range.shift: Test case - testScaleWithFactorGreaterThanZero()
This test case addresses the coverage for the scale() method. Prior to writing this test the statement, branch and method coverage for this method were all at 0%. After writing this test and running the new test suite, this coverage was increased to 79.2%, 50% and 100% for statement, branch and method coverage, respectively. Additional test cases were created in order to increase these coverage measures enough to meet assignment requirements.

Range.scale: Test case - testShiftWithTwoParams()
This test cased improved coverage for the shift(Range base, double delta, boolean allowZeroCrossing) method. Prior to writing this test the statement, branch and method coverage for this method were all at 0%. After writing this test and running the updated test suite, this coverage was increased to 58.6%, 50% and 100% for statement, branch and method coverage, respectively. Additional test cases were created in order to increase these coverage measures enough to meet assignment requirements.

Range.expandToInclude: Test Case - testExpandToIncludeUpper()
This test case significantly improved the coverage of the test for the expandtoInclude method inside of Range. Prior to writing this test case the statement/instruction, branch and method coverages were all at 0%, as this method was not tested in the previous assignment. This test case creates a range and calls the expandToInclude method with a value higher than the range. This will test that the method accurately expands the upper bound of the given range. Doing this greatly improved the coverage as this test uses a value which will cause the method to go through the first two conditional statements of the method before entering the third conditional statement: else if (value > range.getUpperBound()). This test increases the statement coverage to 55.9%, the branch coverage to 50.0% and lastly the method coverage to 100%. After this test case was created by testing the other conditions in the method we were able to achieve 100% coverage in all categories.


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

**Initial Range Coverage**
--------------------------------------------------------------------------
Initial Coverage for Statement Coverage on Range is 12.7%:
![image](https://user-images.githubusercontent.com/101215683/222776190-451c8bb7-5f4d-4f7e-b60d-228a8ec280e3.png)

Initial Coverage for Branch Coverage on Range is 9.2%:
![image](https://user-images.githubusercontent.com/101215683/222776509-e22eb2da-99dc-49d6-b5f0-a833563746f9.png)

Initial Coverage for Method Coverage on Range is 26.1%:
![image](https://user-images.githubusercontent.com/101215683/222776660-50e381b5-349d-40b8-aab8-2b7fad3cbfae.png)

**Range Coverage Acheived**
-------------------------------------------------------------------------
Coverage for Statement Coverage on Range is 99.6%:
![image](https://user-images.githubusercontent.com/101215683/222777716-32ddb069-210b-4ba0-97b9-f7a13e172711.png)

Coverage for Branch Coverage on Range is 93.4%:
![image](https://user-images.githubusercontent.com/101215683/222777966-a192858c-f4b8-44c3-af12-63e373f414d1.png)

Coverage for Method Coverage on Range is 100%:
![image](https://user-images.githubusercontent.com/101215683/222777804-9fc1bedc-ec57-413a-8781-27e25a06af3e.png)


# 6 Pros and Cons of coverage tools used and Metrics you report

EclEmma was very easy to use as it is directly integrated into Eclipse IDE, making test coverage extremely easy to improve. While EclEmma did not provide metrics for condition coverage, it does have the option to show method coverage. While this metric does show which methods in each class under test was missed, it does not provide much more information. This metric may also prove to be redundant as it is very likely that all methods in a class have tests written for them. 

The other two metrics we used were statement/instruction coverage and branch coverage. Statement coverage is great for giving a general sense of how well each class/method was covered. However, it does not provide all information, this includes conditional statements. Statement coverage will consider a line with a conditional state to be "covered" once any of its branches are covered. Because of this, statement coverage may show a misrepresentation of the actual depth of the coverage of a test suite. Branch coverage however does represent the coverage of all possible results of conditional statements in a class under test, creating a deeper understanding of test suite quality. 

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.
Requirments based test generation has the advantages of allowing the tester to be more creative in the creation of tests for methods. It is also very simple to create tests with requiremets-based test generation, as the tester just follows the requirements. The disadvatages of requirements-based test generation include a lack of confirmation to the person testing as they are not able to tell how much of the method was tested. 
Coverage-based test generation on the other hand has the advantage of the tester being able to confirm how much of the method they are covering with their tests. As well it has an advantage of having metrics to use to measure the improvement of your tests. The disadvantages of coverage-based testing is much more time being required to ensure we are reaching full coverage, and the tester must have a strong understanding of the source code to ensure they are testing all branches.

# 8 A discussion on how the team work/effort was divided and managed
We divided the manual measure data flow calculations (section 2 of report) by assigning each section of the requirments from the lab handout to one team member then getting other team members to check each others work after completion. We also divided writing unit tests for the test suite development section by Saina to write the org.jfree.data.DataUtilities tests to reach the minimum coverages required, and Rachel, Isaiah and Ana to write the org.jfree.data.Range tests to reach the minimum coverages. Then we swapped and checked over eachother work and as well helped eachother through challenges faced. As well, upon completion of the tests, we helped eachother review the tests, looking for any inconsistencies or defects in the tests.

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab
We realized as we began the creating unit test process that we had to re think our original strategy of splitting into pairs to complete org.jfree.data.DataUtilities and org.jfree.data.Range unit tests. Since Range had much more methods then DataUtilities. We found it best that one member tackle DataUtilities and get other team members to help when required and the other three memebers focus on Range methods.

# 10 Comments/feedback on the lab itself
This lab was a great way for us to expand our knowledge and apply what we have learned in class about white-box testing. It was very beneficial for us to use a coverage tool (EclEmma) and see how that worked when unit testing. Using Branch coverage really showed us how we could better write more detailed unit test to test flaws in the program we may not have recognized without using a coverage tool.
