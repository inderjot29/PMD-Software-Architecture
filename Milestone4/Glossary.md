#Glossary
**Abstract Syntax Tree (AST)**

This is the tree representation of the abstract syntactic structure of the source code which is to be analyzed by PMD. 
 
**JavaCC**

This is a parser generator and lexical analyzer written in Java. 
In PMD, the JavaCC converts the source code (which is to be analyzed for flaws by PMD) into its Abstract Syntax Tree representation. 

**JJTree**

JJTree is a preprocessor for JavaCC. JJTree augments JavaCC: it makes the generated parser build a syntax tree, without you having to program the tree-building yourself.[1]

**Data Flow Analysis (DFA)**

Data-flow analysis is a technique for gathering information about the possible set of values calculated at various points in a computer program.[2]
It relates to PMD in that the implementation of several rules requires the use of a Data Flow Analysis Layer.

**Dependency Structure Matrix (DSM)**

In software architecture a Dependency Structure Matrix (DSM) can be used to understand dependencies between groupings of classes i.e. packages in Java.[3] An upper triangular DSM means that there is no cyclical dependencies among the packages and is an indicator of a stable architecture. 

##References
[1] http://www.j-paine.org/dobbs/jjtree.html
[2] https://en.wikipedia.org/wiki/Data-flow_analysis
[3] http://erik.doernenburg.com/2010/04/dependency-structure-matrix/
