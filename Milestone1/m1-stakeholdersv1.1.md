#Stakeholders of PMD

##Classes of Stakeholders

The stakeholders of the PMD project can be divided into the following classes:

1. Acquirers
2. Documentation Writers (These can be considered a subcategory of Communicators. Since PMD is such a small open-source project, it does not truly have any clear communicators and many of their roles are played by documentation writers, both official and non-official)
3. Contributors (PMD, being a small open-source team, has contributors acting as developers, maintainers, system administrators, testers and support staff)
4. Users (commercial and individuals)

##Acquirers
Acquirers are the business sponsors and senior tiers of management which fund the project. PMD being an open-source project relies heavily on its acquirers which include:

1. DARPA which has funded the Ultra*Log and Cougaar effort which spawned PMD [1]. PMD was initially written in support of Cougaar, a Defense Advanced Research Projects Agency (DARPA) project billed as "An Open Source Agent Architecture for Large-scale, Distributed Multi-Agent Systems." DARPA eventually agreed that PMD could be open sourced [2].

2. QA-Systems ships PMD inside their QStudio product. QStudio incorporates both the PMD and its own engine. In addition to all PMD capabilities, QStudio for Java provides symbol table support allowing cross-file analysis, 200 default rules many of which are customizable and an explict ISO standard Quality Model. PMD users can seamlessly extend their own rule sets into QStudio for Java. [17] 

##Documentation Writers
Documentation writers provide documentation and training materials in order to give stakeholders a proper understanding of the system. For PMD, the main documentation writers include:

1. Members and contributors who have documented the system on the web
2. Lead developer Tom Copeland wrote "PMDApplied: Easy to use guide"  [3]

Some issues have been raised related to documentation on Sourceforge:
Absence of reports in new version (Issue 1365 - Aggregated javadoc missing in PMD-5.3.3 [4])

##Contributors
The PMD team is comprised of Members and Contributors. Members have direct access to the source of a project and actively evolve the code-base. Contributors improve the project through submission of patches and suggestions to the Members. The number of Contributors to the project is unbounded [5].

PMD also has several enterprise-level contributors (different from individual-level contributors) such as:
1. AE for the JSP integration and especially for writing the JSP grammar [1].
2. RefactorIT for letting their software be used free-of-charge on PMD code [1].
3.  Cenqua for giving PMD a free Clover license and doing a nice FishEye run [1].

Since the PMD team is small with only 20 active developers having commit privileges to the Github repository (out of 38 total contributors [6]), developers, maintainers, testers, system administrators and support staff all fall in the same class which we have chosen to name “Contributors”. 

Below are some issues raised on Sourceforge by the class of Contributors. 

1. By Developers:

a. Issue 1406 (Passing a concatenated string to the “error” method of a non-logger class accidently invokes the logger class [7]): The developer here is trying to raise a concern about unnecessary invocation of logger classes by non-logger code. This issue has been labelled as "False Positive" and still in open state. 

b. Issue 1390 (The SignatureDeclareThrowsException rule has been duplicated in two different rule sets which apparently provides the same functionality and hence creates confusion for the user [8]): Here, the concern, that has been raised, is related to inconsistency in the source code of PMD. The developer, alongwith raising the concern, also provides suggestions on how this issue can be handled.

Pull Requests :-

a. A rule is added to look for fields,methods and nested classes that have a default access modifier.(#PullRequest 57-This rule helps the code analyser to analyze default members with the help of a required appropriate comment.[9])

b. This request targets extensibility of the system by adding a new ruleset in the existing structure(#PullRequest  54-A new ruleset is added for maven’s POM file[10]).


2. By Testers:

a. Issue 1374 (No warning is raised for the assertions without specifying a message string inside the method [11]): In this issue, the tester is concerned with the runtime execution of the tests in a specific case.

b. Issue 1373 (The new version of Junit ruleset defined for Junit is not compatible with TestNG anymore [12]): Here, the tester is concerned with the compatibility of the newly designed tests and seeks information about the feasibility of the suggestion he is providing.

Pull Requests:

a. #PullRequest 59- In order to distinguish literal booleans from boxed booleans,a new rule is added to have  a check on the boxed booleans used for testing. This rule is added into UseAssertTrueInsteadOfAssertEquals rule class[13].


All the issues raised on Sourceforge are addressed and fixed by the contributors. They also have frequent releases (nearly once every 2 months), which contain a batch of fixed bugs and added functionalities (raised as feature requests). 

As observed from the last 2-3 years, Andreas Dangel is addressing all the issues raised on Sourceforge related to PMD. He also has 948 commits on the PMD project at GitHub, which is approximately 12% of the total number of commits [6].
 
##Users

Stakeholders in the Users Category can be either:

1. Individual users. PMD's individual users are primarily from the developer community. In a study of Java developers sourced through the NL-JUG group (a Dutch Java user group) and OWASP-NL group (a Dutch application security community), 42% of the respondents who had ever used a Static Source Code Analyzer had used PMD [14]. With over 34,000 downloads on Sourceforge every week, it is clear that PMD is one of the preferred tools in the developer community. 

2. Commercial organizations such as Vanward Technologies which uses PMD in their Convergence Product and QA-Systems which uses PMD inside their QStudio product [1]. Also DARPA which uses PMD in their Cougaar project.

Users are predominantly concerned with issues of functionality, performance, security and user-friendliness i.e. quality properties of the system. Since the product is designed to cater to them, it is important to give them a platform to raise their concerns and to receive their feedback during development.

Users play an essential part in raising bug issues which might escape the developers’ attention. Users raise issues on Sourceforge and Github and some examples of issues they have raised and their corresponding concern include:

1. #Issue 1196 (CPD GUI fails to load directory in OSX Mavericks [15]): Concern - Lack of user friendliness in the GUI
2. #Issue 1402 (Windows-only bugs [16]): Concern - Errors in cross-functionality
3. #Issue 1350 (PMD  does not take into consideration the global settings and runs unnecessarily [17]): Concern - Performance

Users can also raise feature requests which can be taken into account in future versions of the system:
 
1. Installation Requirements (#Issue 1193 - No way to install PMD on Ubuntu/Debian through the command line [18])
2. Functional Requirement (#Issue 1377 - PMD does not provide any method to turn off parsing of the files included by user [19]).

PullRequests:

1. Functional Requirement(#PullRequest 63- Rule CheckResultSet should be changed to allow the results to be returned from one of the navigation methods(next,first,last,previous)[20])
2. Performance improvement.(#PullRequest 75- Performance of RuleSetFactory is enhanced by setting the ruleset in PMD configuration and re-check it before generating it in MonothreadProcessor,MultiThreadProcessor and PMDRunnable classes.[21])
 


##Bibliography
[1] https://pmd.github.io/pmd-5.3.4/overview/credits.html

[2] http://www.onjava.com/pub/a/onjava/2003/02/12/static_analysis.html

[3] http://pmdapplied.com/

[4] http://sourceforge.net/p/pmd/bugs/1365/

[5] https://pmd.github.io/pmd-5.3.4/team-list.html

[6] https://github.com/pmd/pmd/graphs/contributors

[7] http://sourceforge.net/p/pmd/bugs/1406/

[8] http://sourceforge.net/p/pmd/bugs/1390/

[9] https://github.com/pmd/pmd/pull/57

[10]https://github.com/pmd/pmd/pull/54

[11] http://sourceforge.net/p/pmd/bugs/1374/

[12] http://sourceforge.net/p/pmd/bugs/1373/

[13] https://github.com/pmd/pmd/pull/59

[14]http://www.cs.ru.nl/bachelorscripties/2008/Fabian_van_den_Broek___0012815___Static_Code_Analysis_In_Java.pdf

[15] http://sourceforge.net/p/pmd/bugs/1196/

[16] http://sourceforge.net/p/pmd/bugs/1402/

[17] http://sourceforge.net/p/pmd/bugs/1350/

[18] http://sourceforge.net/p/pmd/bugs/1193/

[19] http://sourceforge.net/p/pmd/bugs/1377/

[20] https://github.com/pmd/pmd/pull/63

[21]https://github.com/pmd/pmd/pull/75

