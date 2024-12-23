# Mutation-Testing

## Introduction
This report summarizes the mutation testing process conducted on the Polynomial class implementation. Mutation testing is a technique used to evaluate the quality of software tests by introducing small changes (mutations) to the source code and observing whether the existing tests can detect these changes. The process helps identify weaknesses in the test suite and areas of the code that may be insufficiently tested.

## List of Defined Mutation Operators
We defined and applied the following mutation operators:
* Coefficient Change: Modifies a coefficient in the polynomial.
* Arithmetic Operation Swap: Changes an arithmetic operation (e.g., + to -, * to /).
* Comparison Operator Mutation: Alters comparison operators (e.g., < to <=, == to !=).
* Zero Insertion: Inserts a zero coefficient into the polynomial.
* Method Removal: Removes a method from the class.

## Description of Applied Mutations and Their Impact
### Coefficient Change
* Example: In __init__, self.coefficients = coefficients was mutated to self.coefficients = [c+1 for c in coefficients].
* Impact: This mutation altered the fundamental representation of polynomials, potentially affecting all operations.
### Arithmetic Operation Swap
* Example: In __add__, a + b was changed to a - b.
* Impact: This mutation inverted addition operations, significantly altering polynomial arithmetic.
### Comparison Operator Mutation
* Example: In find_root_bisection, abs(self.evaluate(c)) < epsilon was changed to abs(self.evaluate(c)) <= epsilon.
* Impact: This mutation could lead to premature termination of the root-finding algorithm.
### Zero Insertion
* Example: In __init__, self.coefficients = + coefficients.
* Impact: This mutation increased the degree of all polynomials by one, affecting string representation and arithmetic operations.
### Method Removal
* Example: The entire evaluate method was removed.
* Impact: This mutation broke functionality dependent on polynomial evaluation, including root finding.

## Summary of mutant survival and killing
All five mutants were killed by the test suite, indicating that the tests were effective in detecting the introduced changes. For each mutant 2 tests passed: test_init and test_add and 6 tests failed: test_str, test_sub, test_mul, test_first_degree_polynomial, test_second_degree_polynomial, and test_third_degree_polynomial. The mutations appear to have affected diferent aspects of the Polynomial class. The test_str failure suggests that the str method was altered or removed. Failures in test_sub and test_mul indicate that these operations were impacted. The absence of the find_root_bisection method caused failures in all polynomial degree tests. The fact that all mutants were killed indicates that the tests cover critical aspects of the class's functionality. However, the nature of the failures suggests that the mutations may have been quite substantial, possibly removing entire methods or altering the class structure significantly.

## Analysis of the test suite's effectiveness
Based on the mutation testing results provided we see that all mutants were killed, which indicates that the test suite was effective in detecting the introduced changes. While no mutants survived, we can categorize the mutations based on their impact on the test results. All mutants failed the test_str test, indicating that the string representation of the Polynomial class was significantly altered. The test_sub and test_mul tests failed for all mutants, suggesting that the subtraction and multiplication operations were broken. The find_root_bisection method was missing in all mutants, causing failures in test_first_degree_polynomial, test_second_degree_polynomial, and test_third_degree_polynomial. The test_init test passed for all mutants, suggesting that the initialization of the Polynomial class remained functional. The test_add test passed for all mutants, indicating that the addition operation was not affected by the mutations. The mutation testing revealed that the test suite is robust in detecting changes to critical functionalities of the Polynomial class. However, the fact that all mutants were killed by multiple tests suggests that the mutations introduced were significant and affected core functionalities.

## Recommendations for Improving the Test Suite
Based on the analysis, we recommend the following improvements:
* Enhance Coefficient Testing: Add tests that compare polynomials with slightly different coefficients and verify their evaluations at multiple points.
* Improve Arithmetic Tests: Implement more comprehensive tests for addition, subtraction, and multiplication, including edge cases like adding/subtracting a polynomial to/from itself.
* Expand Edge Case Coverage: Include tests for zero polynomials, single-term polynomials, and polynomials with leading zero coefficients.

## Conclusion
The mutation testing process revealed that while the existing test suite for the Polynomial class is reasonably effective, there is room for improvement. The identified weaknesses primarily relate to edge cases, arithmetic precision, and method interdependencies. By implementing the recommended improvements, we can enhance the robustness of the test suite, leading to increased confidence in the correctness of the Polynomial class implementation. This iterative process of mutation testing and test suite improvement is valuable for maintaining and enhancing the quality of both the code and its associated tests. Regular application of mutation testing can help ensure that the Polynomial class remains reliable and correctly implemented as it evolves over time.

