**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group \#:      |     |
| -------------- | --- |
| Student Names: |     |
|                |     |
|                |     |
|                |     |

# Introduction


# Analysis of 10 Mutants of the Range class 
| **Mutant**                          | **Line** | **Description**                              | **Killed?** | **Reason**                                                                 |
|-------------------------------------|----------|----------------------------------------------|-------------|---------------------------------------------------------------------------|
| 1. Removed conditional              | 90       | Replaced `b0 <= b1` with `false`             | No          | No test for `b0 > b1` case in `intersects()`.                            |
| 2. Decremented double local var 1   | 90       | Decremented `b0` in `b0 <= b1`               | No          | No test where decrementing `b0` changes the condition outcome.            |
| 3. Incremented double local var 1   | 90       | Incremented `b0` in `b0 <= b1`               | No          | No test where incrementing `b0` changes the condition outcome.            |
| 4. Less or equal to greater or equal| 90       | Replaced `b0 <= b1` with `b0 >= b1`          | No          | No test for `b0 > b1` case in `intersects()`.                            |
| 5. Decremented double field lower   | 105      | Decremented `this.lower` in `value < lower`  | Yes         | Killed by `testConstrain_BelowLowerBound_AcceptsBug`.                     |
| 6. Decremented double field lower   | 123      | Decremented `this.lower` in `return lower`   | Yes         | Killed by `testConstrain_BelowLowerBound_AcceptsBug`.                     |
| 7. Incremented double field lower   | 123      | Incremented `this.lower` in `return lower`   | Yes         | Killed by `testConstrain_BelowLowerBound_AcceptsBug`.                     |
| 8. Decremented double field upper   | 132      | Decremented `this.upper` in `return upper`   | Yes         | Killed by `testConstrain_AboveUpperBound`.                                |
| 9. Incremented double field upper   | 132      | Incremented `this.upper` in `return upper`   | Yes         | Killed by `testConstrain_AboveUpperBound`.                                |
| 10. Substituted 1 with -1           | 144      | Substituted `1` with `-1` in some method     | No          | Likely in an untested method like `scale()` or `expand()`.                |

# Report all the statistics and the mutation score for each test class



# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process

# Explain the use of assertions and checkpoints

# how did you test each functionaity with different test data

# Discuss advantages and disadvantages of Selenium vs. Sikulix

# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
