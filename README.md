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
