# Architecture Evaluation of Apache Spark by Team PMD
## Comments on the Stakeholders
The Stakeholder Classes for Apache Spark have been identified properly. However, the separation of concerns for these classes is not clear from the documentation. 

For example: it would have been better if the issues identified were related to a specific concern like “user-friendliness”. Currently, these relations are implied but making them explicit would have made the AD better.

Considering the nature of the project and size of the team, it is clear that the stakeholder classes are not mutually exclusive. Relating the identified concerns to the stakeholder class would have provided a better understanding of the stakeholders’ concerns and responsibilities. 

The stakeholder class ‘Acquirers’ is mentioned in the classes identified but their concerns and responsibilities are not clearly defined. The following lines provide a reason for not relating any issues and pull requests to the acquirers:

”Acquirers of Spark, who we also identified as main stakeholders, benefit indirectly, since they are not strictly concerned with the code and these pull requests. However, Spark’s continuous improvements leads to larger success overall, which is certainly of concern to them”

However, the term “continuous improvement” is a bit vague here. It could have been made clear by showing how the integration of new resources impacts the cost and quality properties of the project.

The issue no. “9” is a documentation issue which has been considered as a concern for the developer class whereas according to the book Rozanski & Woods (R&W), this type of concern is more appropriate to the class of Maintainers. 

The links provided for “m1-issues.md” [1] and “m1-pull-requests.md” [2] do not exist, which makes the Architectural Description **incomplete**. 

Overall, the document is well-structured. The checklist mentioned in the book has been followed thoroughly which is definitely a plus point.

## Comments on the Functional View and Context View
**Functional View**

The idea to share the scripts used to extract the dependencies among the packages and their analysis is really great. It shows that the view is taking the actual structure into consideration. This is certainly going to help during conformance checking.

It is mentioned that Figures 1, 4 and 5 are meant to be sketches and UML notation is only loosely followed. But, the notations used aren’t explained. It is not clear in Figure F.1 and F.4, what the arrows indicate. It would have been better if a legend was included for the models.

Some packages present in the model in figure F.5 are never explained in the view. The packages “mlib” and “streaming” are not a part of the core packages but they are providing some extra functionalities similar to “sql”, “graphx” and “yarn” (which are explained in the view). It would have been better if a simple introduction of the remaining two packages (mlib and streaming) were also included.

Design philosophy can be improved by providing some references pointing to the source code or some specific way of structuring classes etc. which will help the reader understand why Spark exhibits properties like loose coupling and high cohesion.

Overall it is a very well documented view and clearly targets every aspect related to the functionality of the system. However, the few points discussed should be taken care of.

**Context View**

Scope of the system has not been defined. Context view shows all the necessary external and internal entities but without the scope definition, it looks poorly structured. Defining scope would have helped the reader map the purpose of the external and internal entities to their responsibilities. 

Although internal entities are not to be shown as part of context view, their inclusion would have provided additional knowledge. A brief definition about each of them would have been better.
 
## Comments on the Information View
“Spark works by performing either transformations or actions on a given RDD (resilient distributed dataset), all within memory.”

What does the phrase “all within memory” refer to? Does this mean Spark’s in-built database storage or does Spark retrieve data from separate sources and only store it temporarily, as long as it is required to process it? Clarification on this issue would be beneficial. 

“Operations can only be performed on RDDs which are not only fault-tolerant, but can also be be operated on in parallel.”

It is not immediately evident whether the operations themselves are fault-tolerant or whether the RDDs are fault-tolerant (is this a property of an RDD?)

Are ‘lineage’ and ‘checkpointing’ terms used within the Spark documentation itself or are they also used when referring to operations in systems similar to Spark such as Hadoop? A reader not familiar with standard terms used in big data would be confused - a brief explanation would have been beneficial at this stage. 

“The RDD can either be removed from memory manually using the RDD.unpersist() method or by Spark”

What is the RDD.unipersist() method? Is it automatically a property of every RDD? 
In figure I.2, the acronym DAG should have been explained in a legend. Also, what an “operator” is exactly is not clearly explained and renders the rest of the diagram incomprehensible. 

In Figure I.4, “bundle task processes” were mentioned but it was not clear what they referred to - does this mean the set of lazy transformations that have yet to be computed and are to be computed together as an action? 

This view is not properly documented. For instance, we come across the following line:
“Transformations create a new dataset based on an existing one, whereas actions “return a value to the driver program after running a computation on the dataset.” (Spark documentation).”

An actual link to the part of the Spark documentation, cited at the bottom of the view, to which this refers would be helpful.

To conclude, the static information structure of Apache Spark was well-presented, however the other points emphasized were not very clear or understandable, even for a suitably-versed technical audience. 
## Comments on the Deployment View

“Apache ZooKeeper™ solves this problem by providing leader election and state storage, which allows another idle Master node to recover the crashed Master node state and become the new leader.” 

The purpose of Apache Zookeeper and how it relates to Apache Spark is not made clear. Is this a separate open-source software, a subsystem within Spark or something else entirely? How does it tie into and coordinate with the inner workings of Spark to help it recover a crashed Master node? 

While the Main Deployment Diagram D.1 adheres to standard design practices, there are some problems with it:
What are the Zookeeper servers? Can other types of servers not be used as processing nodes?
Non-standard acronyms such as ‘LDE’ have not been explained with a legend
In the diagram, it is not obvious which is the ‘scheduler’ that is supposed to communicate with the Master Node, as mentioned in the description before D.1. Is the scheduler the <<processing node>>Driver Program? Since this is an important part of the deployment process, it would be helpful if this was explicitly demonstrated in the diagram created for the reader. 

In the beginning, the following line is mentioned:
“We explore two scenarios: one typical deployment that is often used in the cloud, usually adopted by enterprises, and another simpler deployment, usually adopted by users who want to familiarize themselves with Spark.”

However, in the ensuing documentation it is not made explicitly clear whether both diagrams D.1 and D.2 refer to both scenarios or whether D.1 applies to only the first scenario and D.2 to the second scenario. This is a serious issue since it does not give the reader any clarity of understanding considering that both the scenarios are extremely different.

While a helpful line is mentioned at the end of the Local Deployment Scenario:
“This kind of deployment will be mainly useful for users to want to familiarize themselves with Spark's framework and with the different configurations options.”

This clarifies the issue but it would be better if it were mentioned in the beginning how the different diagrams relate to the different scenarios. 

There are several points in the Deployment View where references have not been properly attributed. For example:
“It is not recommended to go beyond 200GB of RAM as JVMs do not always behave properly with such an amount. Above 200GB, it is recommended to run multiple Worker JVMs per machine;”

“In order to maximize Spark's performances, it is highly recommended to run Spark on the same nodes as HDFS. If this is not possible, make sure that at least the Spark nodes are in the same LAN as the HDFS.”

Ideally, these should be cross-referenced to the official Spark documentation (https://spark.apache.org/docs/1.2.1/hardware-provisioning.html). They are not written in exactly the same way but they borrow very heavily from the documentation, as a cursory Google search reveals. 

Overall a strong grasp and good picture of the Deployment View was demonstrated, with a few minor problems.

## Comments on the Performance and Scalability Perspective
In the “Practical Testing Analysis” section, various benchmark tests and graphs are included but there are no references attributed in the document itself. It is written in the introduction “They are all be found in the references”. All the resources used in the Architecture Description of Apache Spark are collectively included in “m3-references.md” file. The reader is required to skim through every resource to see if the data for the aforementioned section was picked up from one of those resources. It would have been better if the resources were referenced in the section itself.

The concept of “peak load behavior” in the “Relevant Architecture Components” section is not explained properly: 

“The more hardware available, the more likely the system will have enough resources to effectively divide tasks. Should the system be unable to do so, this would be an example of peak load behavior.” 

It is also mentioned that processing will not stop but it will be less efficient. What is the meaning of “system being unable to effectively divide tasks”? How can the “effectiveness” be measured? If the processing will not stop, then how is the user going to know that the peak load behavior has been reached? Many such questions are left unanswered. 

It would have been better if a proper measurement of threshold efficiency was included, which could have helped the user to judge whether the system performance is slower than expected. Hence, they could determine whether peak load was reached.

The improvements done after the application of Performance and Scalability perspective on Context View, Functional View and, Information View are shown properly by providing links to the difference file. This helps the reader understand what has been optimized in each of the views and hence leads to better understanding of the effect of this perspective on the overall architecture.

As a whole, the perspective is effectively documented with a few issues as pointed above.

## Comments on the Architectural Style of Apache Spark
Architectural Style has been created as a different document and it is clearly mentioned in the document that this is just an extension of the existing functional view and not a replacement, which is a good way to link it to the functional view without overcrowding the view itself.

The abstract diagram in “Understanding the Pipes and Filters Style” is supposed to be a clear abstraction of the sequence diagram in “Annotated Sequence Diagram” section. But, the filter “TaskSchedulerImpl” isn’t present in the abstract diagram. It is not explained whether it is included in some other filter component or just missed from the diagram.

“iExecutor” component in the sequence diagram isn’t considered as a filter, but there is no explanation given as the reason to do so. Also, which part can be considered as the pipe between “ConcreteBackEnd” filter and “TaskRunner” filter (which has been clearly shown in the abstraction of this diagram but not so obvious in the sequence diagram)? “TaskRunner” filter is explained to be taking task as input. According to the sequence diagram, “iExecutor” component provides the task while, as per the abstract diagram, “ConcreteBackEnd” filter provides the task. This is a bit confusing and should be clarified.

This document provides an almost clear overall idea of the dominant architectural style used, with a few confusing areas as discussed above.
