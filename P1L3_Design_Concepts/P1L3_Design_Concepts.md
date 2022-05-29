# Design Concepts

## Definitions
- **Design**: Deliberative, purposive planning
- **Engineering**: Skillful or artful contrivnce applying scientific and mathematical principles
- **Craft**: Skilled occupation
- **Art**: Use of skill, taste, and imagination in the production of aesthetic objects

## Differences between software design and programming
- Scale
- Emphasis on non-functional requirements

## Software design
The process of building a program while satisfying a problem's functional requirements and not violating its non-functional constraints

## Two parts of software design
- Architectural design:
	- The process of identifying and assigning the responsibility for aspects of behavior to various modules or components of a software
- Detail design:
	- The process of specifying the behavior of each of the system components that you've identified during architectural design
	- Primary activity: select logical representation of data objects identified during the requirements definition and specification phase. (Wasserman)

## Design annotations
- Pseudo code; program design language (PDL)
	- Keywords, free syntax of natural language, data declaration, subprogram definition and calling
- Structured programming
	- Sequence, condition, repetition, chunking
- Flowchart; call graphs
	- Directed graphs: node is computational unit; arc is flow of control
- Decision tables
	- Rules, conditions, action

## Three aspects of design
- Design method
	- Design trade off: Long-term maintainability v.s. Short-term schedule
- Design representation
- How the design is going to be validated
	- Issues with design validation
		- Independence of validators
		- Dependence on design method
		- On-going versus after-the-fact
## Other design issues
- Architectural versus detail design
- Functional behavior versus non-functional constraints
- Specification/what versus design/how
- Application specificity

## Design documentation
- Traditional design documentation
	- Subcomponents
		- Processes / activities
		- Data / data flows
	- Control flow
		- Control regime
	- Performance
	- Resources
- Other
	- IEEE standards
	- Leonardo Project at MCC (1980s)

## Design rationale
- Design decisions: explicit choices of how to trade off two non-functional aspects of a design, such as speed versus size

## Key design concepts
- Conceptual integrity
- Coupling & cohesion
	- **Coupling**: the extent to which two components depend on each other for successful execution
		- Low coupling is good
	- **Cohesion**: the extent to which a component has a single purpose or function
		- High cohesion is good
- Information hiding: encapsulating the capabilities that a particular module has behind an abstract interface
- Abstraction & refinement
	- Abstraction mechanisms
		- Declarative: what, not how
		- Aggregation: container, not contents
		- Generalization: class, not individuals
		- Parameterization: binding details later
		- Non-determinism: leaving choices unspecified
- Aesthetics

## Design philosophy
- Descartes - analysis; use of models
- Marx - understanding the social context of design solutions; user-centered design
- Heidegger - tools for accomplishing goals; CASE, IDE
- Wittgenstein - language games (desktop metaphor)


