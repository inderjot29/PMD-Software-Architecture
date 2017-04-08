#Architectural Overview of PMD
##Introduction
PMD is an open-source project. It consists of a static source code analyzer (analyzes code via rulesets to identify common programming flaws) and a copy-paste detector (for the detection of duplicate code). 

The stakeholders towards whom this documentation is primarily targeted are the class of **developers** i.e. technical stakeholders who can potentially modify PMD themselves and who would be familiar with most of the technical concepts covered here. 

We have chosen to document its software architecture because:
* It is one of the most popular source code analyzers online, with over 30,000 downloads on Sourceforge every week
* It is very easy to modify - new languages and rules can be added to PMD by virtually anyone, while the overall architecture maintains a common structure
* Lack of documentation currently available that clearly explains how PMD works and is constructed

Our Architectural Design is modelled after the precepts suggested by Rozanski and Woods in their book **"Software Systems Architecture: Working with Stakeholders Using Viewpoints and Perspectives"**. In this context, we have tried to document PMD's architecture by focusing on its:

1. Stakeholders: The audience which is affected by PMD's performance and architecture.
2. Viewpoints: Knowledge on how PMD is architecturally structured.
2. Perspectives: Knowledge on PMD's non-structural quality properties. 

##Viewpoints
1. **Context View:** PMD’s scope of responsibility, its key performance requirements and the external entities on which PMD depends and their responsibilities are defined here. 
2. **Functional View:** We define the functional capabilities, external interfaces, internal structures, functional design philosophy and dominant architectural style of PMD here.
3. **Information View:** We define the Data Flow through the system implementation and the Information Processing Life-Cycle of PMD here. 
4. **Development View:** We define the module dependencies and organization, commonalities in the design model and codeline organization here. 

##Perspective: 
**Evolution Perspective:** We define the dimensions of change and the evolution tradeoffs of PMD here.

A glossary of commonly-used terms has also been provided.

##Links to Artifacts
1. [Stakeholder Groups](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone1/m1-stakeholdersv1.1.md)
2. [Context View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone1/m1-contextv1.1.md)
3. [Functional View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone3/m3-functional.md)
4. [Information View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone2/m2-information.md)
5. [Development View](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone3/m3-development.md)
6. [Evolution Perspective](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone3/m3-evolution.md)
7. [Glossary of Terms Used](https://github.com/McGillCOMP529F2015/PMD/blob/master/Milestone4/Glossary.md)
