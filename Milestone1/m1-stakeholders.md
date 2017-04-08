#Classes of Stakeholders

The stakeholders of the PMD project can be divided into the following classes:

1. Acquirers
2. Communicators
3. Contributors (PMD, being a small open-source team, has contributors acting as developers, maintainers, system administrators, testers and support staff)
4. Suppliers
5. Users (commercial and individuals)

#Acquirers
Acquirers are the business sponsors and senior tiers of management which fund the project. PMD being an open-source project relies heavily on its acquirers which include:

DARPA which has funded the Ultra*Log and Cougaar effort which spawned PMD[1].

#Communicators
Communicators provide documentation and training materials in order to give stakeholders a proper understanding of the system. For PMD, the main communicators include:

1. Members and contributors who have documented the system on the web
2. PMDApplied: Easy to use guide written by lead developer Tom Copeland[2]

Some issues have been raised related to documentation on Sourceforge:
Absence of reports in new version (Issue 1365 - Aggregated javadoc missing in PMD-5.3.3[3])

#Contributors
The PMD team is comprised of Members and Contributors. Members have direct access to the source of a project and actively evolve the code-base. Contributors improve the project through submission of patches and suggestions to the Members. The number of Contributors to the project is unbounded[4].

Since the PMD team is small with only 20 active developers having commit privileges to the Github repository (out of 38 total contributors[5]), developers, maintainers, testers, system administrators and support staff all fall in the same class which we have chosen to name “Contributors”. 

Below are some issues raised on Sourceforge by the class of Contributors. 

1. By Developers:

a. Unnecessary invocation of non-logger classes by logger code (Issue 1406 - Passing a concatenated string to the “error” method of a non-loffer class accidently invokes the logger class[6])

b. Inconsistency in the source code of PMD(Issue 1390 - The SignatureDeclareThrowsException rule has been duplicated in two different  rule sets which apparently provides the same functionality and hence creates confusion for the user[7])

2. By Testers:

a. Issue 1374 - No warning is raised for the assertions without specifying a message string inside the method[8].

b. Issue 1373 - The new version of Junit ruleset defined for Junit is not compatible with TestNG anymore[9].

All the issues raised on Sourceforge are addressed and fixed by the contributors. They also have frequent releases (nearly once every 2 months), which contain a batch of fixed bugs and added functionalities (raised as feature requests). 

As observed from the last 2-3 years, Andreas Dangel is addressing all the issues raised on Sourceforge related to PMD. He also has 948 commits on the PMD project at GitHub, which is approximately 12% of the total number of commits[5].

#Suppliers
The class of stakeholders which supplies hardware, software or infrastructure are suppliers. Following are the main suppliers of PMD:

1. Sourceforge.net for providing hosting services for PMD [1].
2. There are many dependencies needed for compile, test, runtime etc. For example, Junit for testing, Ant for compilation etc.
3. AE for the JSP integration and especially for writing the JSP grammar[1].
4. RefactorIT for letting their software be used free-of-charge on PMD code[1].
5. QA-Systems for sending in some handy utilities for PMD and shipping PMD inside their QStudio product[1].
6. Cenqua for giving PMD a free Clover license and doing a nice FishEye run[1].
 
#Users

Stakeholders in the Users Category can be either:

1. Individual users
2. Commercial organizations such as Vanward Technologies which uses PMD in their Convergence Product and QA-Systems which uses PMD inside their QStudio product[1] 

Users are predominantly concerned with issues of functionality, performance and security i.e. quality properties of the system. Since the product is designed to cater to them, it is important to give them a platform to raise their concerns and to receive their feedback during development.

Users play an essential part in raising bug issues which might escape the developers’ attention. Users raise issues on Sourceforge and Github and some examples of issues they have raised include:

1. Lack of user friendliness in the GUI (#Issue 1196 - CPD GUI fails to load directory in OSX Mavericks[10])
2. Errors in cross-functionality (#Issue 1402 -  Windows-only bugs[11]) 
3. Performance issues (#Issue 1350 - PMD  does not take into consideration the global settings and runs unnecessarily[12])
4. Users can also raise feature requests which can be taken into account in future versions of the system: 
5. Installation Requirements (#Issue 1193 - No way to install PMD on Ubuntu/Debian through the command line[13])
6. Changes to the GUI (#Issue 1357 - Eclipse Import Window needs a Select All button[14])
7. Support for more languages (#Issue 572 - Python syntax checker[15])
8. Functional Requirement (#Issue 1377 - PMD does not provide any method to turn off parsing of the files included by user[16]).

PMD’s users are primarily from the developer community. In a study of Java developers sourced through the NL-JUG group (a Dutch Java user group) and OWASP-NL group (a Dutch application security community), 42% of the respondents who had ever used a Static Source Code Analyzer had used PMD[17]. With over 34,000 downloads on Sourceforge every week, it is clear that PMD is one of the preferred tools in the developer community. 

#Bibliography
[1] https://pmd.github.io/pmd-5.3.4/overview/credits.html
[2] http://pmdapplied.com/
[3] http://sourceforge.net/p/pmd/bugs/1365/
[4] https://pmd.github.io/pmd-5.3.4/team-list.html
[5] https://github.com/pmd/pmd/graphs/contributors
[6] http://sourceforge.net/p/pmd/bugs/1406/
[7] http://sourceforge.net/p/pmd/bugs/1390/
[8] http://sourceforge.net/p/pmd/bugs/1374/
[9] http://sourceforge.net/p/pmd/bugs/1373/
[10] http://sourceforge.net/p/pmd/bugs/1196/
[11] http://sourceforge.net/p/pmd/bugs/1402/
[12] http://sourceforge.net/p/pmd/bugs/1350/
[13] http://sourceforge.net/p/pmd/bugs/1193/
[14] http://sourceforge.net/p/pmd/bugs/1357/
[15] http://sourceforge.net/p/pmd/feature-requests/572/
[16] http://sourceforge.net/p/pmd/bugs/1377/
[17]http://www.cs.ru.nl/bachelorscripties/2008/Fabian_van_den_Broek___0012815___Static_Code_Analysis_In_Java.pdf

