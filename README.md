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

## Recommendations for Improving the Test Suite
Based on the analysis, we recommend the following improvements:
* Enhance Coefficient Testing: Add tests that compare polynomials with slightly different coefficients and verify their evaluations at multiple points.
* Improve Arithmetic Tests: Implement more comprehensive tests for addition, subtraction, and multiplication, including edge cases like adding/subtracting a polynomial to/from itself.
* Expand Edge Case Coverage: Include tests for zero polynomials, single-term polynomials, and polynomials with leading zero coefficients.
