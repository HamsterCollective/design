# System Level Design

The intent with this document is to define the system level components, there interaction and interfaces between them. The purpose is to enable a decoupled development model where each part can contribute to the whole without needing a detailed understanding of other components.

The goal is that the design herein described clearly set the responsibility and boundary between the components. Each component shall be able repleable without affecting other components as long as the agreed upon interface is kept intact.

A interface is at this level is the data and flow between the components. This is kept separated from the behavioural responsiblity of a component.

## Components

This chapter describe the components in the system architecture and their responsibility.

These are the minimal components for a mutation framework:
 * Mutant Generator. Analyze source code for mutations test requirements.
 * Single SrcCode Mutator. Prodcues mutations of the original software.
 * Single Tester. Test mutants to determine their status such as survived/killed by compiling+running the test suite
 * Equivalent Detector. Symbolic execution (?)
 * Coordinator. Coordinates the internal flow between the components to move a mutant from discovered (Mutant Generator) to classified (Tester).

Additional components that add useful features:
 * Coverage Analyser. Analyze coverage information for *interesting* data such as what mutants are covered by the test suite.
 * Report Generator. Generate mutation reports for the user.

# Overview

This chapter contains the structural overview of the components, how they are connected and their interfaces.

[![Overview](structure.png)](http://github.com/HamsterCollective/design/tree/master/doc/uml)
