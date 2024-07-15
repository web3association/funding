---
description: >-
  Considerations about the data structures used for handling funding process
  data
---

# Funding process data handling

<figure><img src="../../.gitbook/assets/funding-process-data-handling-title.png" alt=""><figcaption></figcaption></figure>

Knowledge, priorities, ideas and execution cover the four key processes involved in funding. Contributors handle the step of execution. There is a many to many relationship between knowledge and priorities, priorities and ideas and ideas and contributors:

* Knowledge & priorities - Many pieces of knowledge can be relevant to the importance of many different priorities.
* Priorities & ideas - Many different priorities can have many different ideas that could help with addressing each of those priorities.
* Ideas & contributors - Many different ideas can have many different contributors that are helping to execute those ideas.



<figure><img src="broken-reference" alt=""><figcaption><p>Many to many relationships between knowledge, priorities, ideas and contributors</p></figcaption></figure>

In relational databases, data normalisation is a process in database design that helps with organising data to minimise redundancy and dependency. The principles behind data normalisation are relevant for how a funding process can handle and process its data due to the amount of duplicated data that can emerge because of the numerous many to many relationships. A funding process could need to handle an ever increasing amount of data being stored and used across the different systems and processes involved in funding.



### Importance of separate but interlinked data structures

Storing the funding processes data separately whilst also allowing this data to reference data from the other processes is one way that a funding system can increase its usability, scalability, maintainability and composability.



**Usability**

If data from each process is handled separately but can be interlinked with each other it will make it easier for voters in the funding process to review one piece of data such as an idea and then see all of the related and linked priorities that this idea could help with and also what contributors are involved in executing that idea. A key outcome that the end user benefits is being able to more easily see and traverse through the data to more easily understand what other ideas are tackling those same priorities and what other ideas those same contributors might be working on. All of this information is highly beneficial for the voter when making more informed decisions during funding. If this data was all bundled into the same data structure the issue of duplication could make it far more difficult for a user to find all of the related information about a priority, idea or contributor. Another benefit of having the data for these processes stored and verified separately is that contributors would be able to more easily submit information about any of the processes immediately. For instance a contributor might submit information about themselves so everyone else in the ecosystem can immediately see what skills and background they have and how they’re interested in supporting the ecosystem. This can help speed up the matchmaking between new contributors and emerging project teams. Another contributor could submit a priority the moment they believe it could be of high importance. This separation of concerns in the data structure allows the contributors to more easily submit the relevant information for each funding process. The community can then more immediately consider and respond to this information.



**Scalability**

Ensuring that data can be referenced and used in other processes can help with reducing the amount of duplicated data being stored. Achieving this can help decrease the storage cost of maintaining the funding process as it scales. If the data is not interlinked in any way it could also become more difficult to find the relevant surrounding data, such as which ideas share the same priority. If priorities were stored as copies and not written or maintained in the same way then identifying where there is overlap becomes increasingly difficult. If the principles of data normalisation are considered and integrated into a funding processes data structure another concern that could emerge is whether the read performance of that data is scalable. If faster read performance is required then the data layer could be treated as a source of truth and solutions could be built on top of that data layer to cache this data and potentially denormalise it for those specific use cases that require a faster read performance.



**Maintainability**

If data is not consistent across the funding process there is a higher risk that the system becomes harder to maintain as it tries to scale. For instance if priority and idea data was stored in a single structure the amount of duplicated priorities could easily increase over time. If there was new information relevant to that priority that meant updating the existing information then that could require updating every idea that has some form of variation of that priority. If this priority is normalised and managed in one place then this information could have been shared across many ideas and updated by itself. Due to the variation in how people document and update their own priority and idea submissions it could be difficult to even try and automate this process. Even if the process was automated in some capacity it would still be far more costly than maintaining a single priority separately that each idea can then reference. The faster and easier it is for the funding process to maintain and update important information the quicker a community can become at responding to that information.



**Composability**

How data is stored and linked with other data influences how easily it can be used. If data is stored independently it can still be combined to create a new data set such as a decision proposal. A proposal could combine information about priorities, ideas and contributors and then be put to the voters for a decision if this was required. Alternatively that same data could also be used in completely separate proposals. Maintaining this data in independent structures whilst allowing each process to easily reference data from other processes can help with making it easier for proposals to be created that bring together any of this relevant information from different sources. For example, there could be a range of different priorities and contributors that already exist in the ecosystem. A new idea being submitted could then reference the relevant priorities and contributors that are relevant to this new idea. Only the new idea information is needed and can be stored in the funding system independently from the other priorities and contributors. Those same priorities and contributors being referenced in one idea can then also be referenced in any other future idea that gets submitted in the future.
