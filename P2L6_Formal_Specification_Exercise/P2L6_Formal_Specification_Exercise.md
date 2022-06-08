# Formal Specification Exercise

## Specification
- Need to know what a program is supposed to do before you begin to write it
- Might come from customer, the end user or the analyst team
- Informal text, in a structured document or using a formal methematical notation
- This lesson focuses on precise specification using mathematical notations

## FOL
- Use two notations: mathematical logic and OCL
- First order logic (FOL)
	- Enables you to precisely express propositions, combine them, and quantify them
- Object constraint language (OCL)
	- Part of UML
	- Provides a syntax for FOL that can be used to annotate UML diagrams

*Risk of circular definition - FOL avoid these kinds of problems*
## Process
Break the specification into three pieces:
- Signature
	- The name of the program
	- The names and types of the input arguments
	- The name and type of the results
- Precondition
- Postcondition
	- What must be true about the output produced by a function
	- Typically: expressing how the output related to the input

*Pure v.s. Impure functions*
- *Pure function*: One in which the output is completely determined by the input*
- *Impure function*: In addition to describing how the output relates to the input, you should also indicate any side effects (changes to global variables, side effects like input / output that are not reflected in the results of the function)

## Sorting
- Example: 
	- Specify a program that could sort vectors of integers in ascending orderss
	- SORT takes an input argument named X and it returns another vector of integers Y
- Describe in English:
	- Input type: given is a vector of integers named X
	- Output type: produced is a vector of integers named Y
	- Output vector Y must be ordered
	- Contents of Y must be the "same as" the contents of X
		- Everything in X must be in Y
		- Everything in Y must have come from X
		- The number of occurrences of each item in Y must be the same as its number of occurances in X
- FOL
	- **Signature**: Vector<int> Y = SORT(Vector<int> X)
		- Sort takes a single argument named X that has the datatype Vector<int> and produces a result Vector Y
		- X and Y have explicit names so we can use them in the pre and post conditions
		- int could actually be any data type which supports a comparison (>) operator
	- **Precondition**: True (always holds)
	- **Postcondition**:
		- Ordered:
			- Signature: Vector <int> Y = ORDERED(Vector<int> X)
			- Precondition: True
			- Postcondition: ∀i: 1 <= i < |Y| • Y[i] <= Y[i+1]
				- For all positions in Y from the first through the one before the last, the value stored in the vector at that position is no greater than the value stored at the next position
				- ∀: for all
				- []: vector indexing (indexing starts from 1)
				- |Y|: length of Y
				- •: it must be the case
		- Same Elements As:
			- Signagure: BOOL Z = SAMEELEMENTSAS(Vector <int> X, Vector<int> Y)
			- Precondition: |X| = |Y|
			- Postcondition: (discussed in Permutation)
		- Permutation: X has the same elements as Y if the elements of X are a permutation of the elements of Y (a well-defined mathematical property)
			- Signature: BOOL Z = PERMUTATION(Vector <int> X, Vector<int> Y)
			- Precondition: |X| = |Y| 
			- Postcondition (break down into special cases):
				1. both vectors are empty: True
					2. If vectors do have elements:
					2.1 First element in X and Y are identical -> whether or not the tails of X and Y are permutations (recursive definition: defining permutations in terms of themselves)
					2.2 First element in X and Y are not identical
						Divide Y up into three pieces, depending on where in the Vector Y the first element of X occurs (position j, where j >= 1 and no larger than |Y|)
							- First piece of Y: all elements from first up to but not including jth
							- Second piece of Y: just the jth element
							- Third piece: all of the remaining elements of Y
							︵: concatenation operation on Vectors
			```
			PERMUTATION(X,Y) <=>
			|X| = 0 ⌵
			( |X| > 0 =>
				(X[1] = Y[1] ⌃ PERMUTATION(tail(X), tail(Y))) ⌵
				(X[1] ≠ Y[1] ⌃
					(∃j: 1 < j < |Y|) • (X[1] = Y[j]) ⌃
					PERMUTATION(tail(X), (Y[]1..j-1) ︵ Y[j+1..|Y|]))
				)
			)
			```
- OCL
	- context Vector:: ORDERED () : Boolean
		- Note that the method has no argument! As with all OCL like UML, the object to which a message is sent serves as an implied argument
	- pre: true
		- If the precondition is true, you don't need to specify it - Leave this constraint out of the specification
	- post: self->forAll(i : Interger | i >0 and i < self.length implies self.at[i] <= self.at[i+1])
		- Notes:
			- Use the vertical bar "|" to separate the designation of the variable i from the proposition
			- The limitations on the value of i appear as part of the proposition
			- The limitations on the value of i are separated from the proposition itself by the use of the implies OCL keyword
			- Use OCL's built in SEQUENCE class instead of Vectors

## Summary
- Sometimes you need a means to precisely express exactly what functionality is required by a system
- A variety of formal languages and tools exists for writing such specifications
- The effort can save a lot of rework resulting from misunderstood requirements