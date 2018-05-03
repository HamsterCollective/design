# System Level Design

The intent with this document is to define the system level components, there interaction and interfaces between them. The purpose is to enable a decoupled development model where each member can contribute to the whole without needing a detailed understanding of other components.

The goal is that the design herein described clearly set the responsibility and boundary between the components. Each component shall be replaceable without affecting other components as long as the agreed upon interface is kept intact.

A interface is at this level is the data and flow between the components. This is kept separated from the behavioral responsibility of a component.

## Mutant State Transitions

For a mutation testing framework to be useful a mutants *state* must, by the design, change from undiscovered to classified. If this isn't possible then the design is useless.

State:
 * undiscoverd. A mutant that is residing in the raw data from the user.
 * unknown. A mutant that is discovered by the analyzer is moved to the unknown state.
 * classified. A mutant that has been determined as being survived/killed/equivalent/stillborn etc.

The design should try to maximize the throughput of undiscovered -> classified.

## Components

This chapter describe the components in the system architecture and their responsibility.

Minimal required components:
 * Mutant Analyzer. Analyze source code for mutations test requirements.
 * Single SrcCode Mutator. Produces mutations of the original software.
 * Single Tester. Test mutants to determine their status such as survived/killed by compiling+running the test suite
 * Coordinator. Coordinates the internal flow between the components to move a mutant from discovered (Mutant Generator) to classified (Tester).

Additional components that add useful features:
 * Equivalent Detector.
 * Coverage Analyser. Analyze coverage information for *interesting* data such as what mutants are covered by the test suite.
 * Report Generator. Generate mutation reports for the user.
 * Schema Tester. Classify the mutants in a schemata mutated program which contains multiple mutants that are toggled.
 * Schemata Producer. Produce a schemata mutated program

# Overview

This chapter contains the structural overview of the components, how they are connected and their interfaces.

[![Overview](https://hamstercollective.github.io/design/pics/structure.png)](https://hamstercollective.github.io/design/pics)

# Use Case

This chapter contains how the components interact with each other and there responsibility when fulfilling the use cases.

## Single Mutant

The operator wants to use the minimal required components for mutation testing of a C++ code base.

## Analyze

The operator wants to analyze the source code for the program to perform mutation testing on.

**Note**: This is how the framework will probably work from at the start. This may change in the future.

[![Single Mutant Analyze](https://hamstercollective.github.io/design/pics/uc_single_mutant_analyze.png)](https://hamstercollective.github.io/design/pics)

## Classify

The operator wants to perform a classification of the unknown mutants that where found by the analyzer.

[![Single Mutant Classify](https://hamstercollective.github.io/design/pics/uc_single_mutant_classify.png)](https://hamstercollective.github.io/design/pics)

## Report

The operator wants to see the mutation score, survived mutants and other useful data that has been found by the classifier.

[![Single Mutant Report](https://hamstercollective.github.io/design/pics/uc_single_mutant_report.png)](https://hamstercollective.github.io/design/pics)
