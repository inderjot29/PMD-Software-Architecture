#Evolution Perspective
In our Evolution Perspective we consider the following concerns:

* Dimensions of Change
* Evolution Tradeoffs

We also perform the following activities while we address these concerns:

* Assess current ease of evolution
* How applying the Evolution Perspective to PMD affects its architecture

##Dimensions of Change

####Functional Evolution:

PMD provides three main functions which can be used to evolve its architecture. 

**Addition of a new language**: 

This change can be implemented in three different scenarios, when:
* Users (or Developers) want to add a copy-paste detector and static code analyzer implementation for a particular language
* They want to implement only CPD functionality for the new language.
* They want to add static code analyzer only without implementing the CPD functionality for that language. 
		
**Addition of new rules and/or rule sets for an already existing language**:

* Static source code analyzer functionality works on the basis of defined rules. The source code is being traversed by these rules to find the violations.
* Each rule belongs to a ruleset XML file. User has to select a ruleset file, that he/she would like to run and all the rules belonging to that particular ruleset run on the source code.
* User/Developer should be able to add a new rule or a ruleset or both depending on his/her requirements.
	
**Magnitude of functional changes:**

We have categorized the magnitude of changes in PMD into three levels - **High**, **Medium** and **Low**. 

* Addition of both CPD and static source code analyzer (**high**): This change requires the developer to add a new module and extend all existing functionalities.
* Addition of a static source code analyzer (**high**): Developer needs to extend a major chunk of existing functionalities along with the creation of a new module. 
* Addition of CPD (**medium**): Addition of CPD module needs less effort than adding a static code analyzer. The developer only needs to extend the classes present in the CPD module of PMD-Core.
* Addition of new rules and rule set (**low**): The creation of new rules and their addition into the existing rule set needs little effort. It can be easily done by adding a new class or a XML file (rule set) along with the new rule classes. These changes do not have much impact on the architecture.

**Likelihood of functional changes:**

* Addition of a new language: Currently PMD as static source code analyzer supports 6 languages and as CPD supports 17 languages [1]. it is expected that developers will add new languages in the future as per demand. These additions are requested by patches and feature requests. For e.g., Patch# 274: PLSQL Language for PMD[2]
* Addition of new rules and rule set: Custom rule addition can be either localized (which means that the user has created a rule or ruleset for his/her personal usage and so, this change won’t be available for all) or global (new rule or ruleset is requested as a patch/feature request and hence is available for all). Likelihood of a localized addition will depend on the user’s needs.  Global additions could be tracked through the patches and feature requests. For e.g., Feature Request# 534, which led to addition of a new rule.[3]
* As per the data present on Sourceforge, a total of 574 feature requests (226 open and 348 closed) and 275 patches (7 open and 268 closed) have been raised.[4][5].

**Ease of evolution for functional changes:**
PMD’s architecture allows easy extensibility. It has a highly modularized architecture and follows good design practises like extensible interfaces, loose coupling (supported by the visitor design pattern implementation) and low inter-module dependencies between non-core modules. Users can easily extend PMD’s functionality for any new language. 

####Platform Evolution:

Considering the nature of PMD’s main task, it has to be implemented in a way so that it can be evolved easily in terms of software platforms. So, Java was chosen as the main language of implementation in PMD, which makes it platform independent.

####Integration Evolution:
Most of the developer community uses IDEs (Integrated Development Environment) to develop applications. So PMD should have the ability to be integrated easily with these IDEs. In order to provide this integration, PMD supports plugin creation. A new plugin is created for every IDE with which the user wants to integrate PMD.

**Magnitude of Integration changes (high):**
In order to integrate PMD into a new IDE, the developer will have to create a new project. The new project will use the .jar file of PMD to automatically run PMD in the required environment. Considering the effort needed to make this change, it will come under the category of high magnitude of change.
		
##Evolution Tradeoffs

To provide flexibility as described in dimensions of change, we need to identify the tactics that are being used in PMD and also the reason for choosing them.

**Tactics and their Assessments**

* **Contain Change**: 
A change becomes a problem when it starts affecting different parts of the system simultaneously. So change should be contained only within the module where it is needed. There are various design principles that help to achieve this. The following are the ones used in PMD to contain the change:

	* **Separation of Concerns**: 
The main elements in PMD are languages and their parsers, rules and application of rules on source files. We can treat them as three different concerns. So, if these concerns are kept separate in PMD, then all the evolution needs mentioned above can be contained. For e.g., adding a new language is only going to affect the part implementing the concern of “language”, addition of rules will only affect the part implementing the concern of “rules”.

	* **Single Point of Definition**:
The input source file for PMD can be in any included language. So it is important to use a common definition for the source and convert the source file into that common format. This in turn helps PMD reuse the same process to apply the rules on all kind of inputs.

* **Apply Design Techniques that facilitate Change**: Some techniques can be used while designing the architecture to make it more flexible. PMD has used the following technique:
	
	  * **Generalization Pattern**:
Generalization is the process of extracting shared characteristics from two or more classes, and combining them into a generalized superclass [6]. This pattern helps in making evolution easier for PMD as we can have superclasses for Language and Rule implementations.

##How the Evolution Perspective affected the Architecture
We have identified the dimensions of change needed and some of the tactics used by PMD to facilitate the evolution perspective. Now, we try to map the effect of this perspective on different views in our Architecture Description.

####[Context View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone1/m1-contextv1.1.md)
	
Two of the external entities identified in PMD are IDEs and IDEs’ PMD plugins. IDEs’ PMD plugins are separate Open Source projects, which uses PMD in their libraries and provide integration of PMD with IDEs. These entities represent the Integration evolution needed in PMD and in future, users/developers can easily create a PMD plugin for any new IDE without affecting the basic functionality of PMD.

####[Functional View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone3/m3-functional.md)

* In this view, “Handling of new languages” and “Addition of Rules and Ruleset” have been included as Internal Structures. These represent the Functional Evolution possible in PMD.
* Functional view also shows how the identified tactics are utilised in the core architecture of PMD.
  * **Application of Tactics**:

      As discussed in the functional view, there are two modules: pmd-core (which contains the general implementation of a language, general implementation of rules, the main flow of application of rules on an input file to get violations and the main flow for copy-paste detector) and pmd-specific language module (which contains the extension of Language and Rules from core module for that specific language). This modular organisation separates the concerns (source files, rules and application of rules on source files) and hence, **contains the change** in the specific modules. 

      Also, as the general structure of language and rules are defined in the core module, any new language or rule extends the same, hence maintaining the overall coherency. This use of **Generalization Pattern** makes the evolution process less error-prone.

####[Information View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone2/m2-information.md)
	
As PMD deals with a wide variety of languages, a flexible information model plays an essential role in evolution. In the Information View’s implementation details, the use of AST parser is explained: “In PMD, an AST parser for a language is implemented, ideally as a jjt file. This parser converts the incoming source code to an Abstract Syntax Tree and passes it as a reference for the static source code analyzer part of PMD.” So, addition of any new language means implementing an AST parser for that language, which allows PMD to get a common input (Abstract Syntax Tree) for all the current and future languages hence preserving the core flow. This explains the use of **Single Point of Definition** principle to **contain the change**.

##References
[1] https://pmd.github.io/
[2]http://sourceforge.net/p/pmd/patches/274/
[3]http://sourceforge.net/p/pmd/feature-requests/534/
[4]http://sourceforge.net/p/pmd/patches/stats/
[5]http://sourceforge.net/p/pmd/feature-requests/stats/
[6]https://sourcemaking.com/uml/modeling-it-systems/structural-view/generalization-specialization-and-inheritance
