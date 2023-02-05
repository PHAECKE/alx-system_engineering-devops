Postmortem


![postmortem](https://user-images.githubusercontent.com/105058306/215735776-7a04bf06-38cc-42c9-ae7c-91434131b98b.gif)






Any software system will eventually fail, and the reasons for this failure can be numerous: bugs, spikes in traffic, security flaws, hardware failures, natural disasters, and human error Failing is normal, and it's actually a great chance to learn and improve. To avoid making the same mistakes again, a great software engineer must learn from them. Failing once due to the same issue is acceptable, but failing twice is not.

A postmortem is a tool widely used in the tech industry. After any outage, the team(s) in charge of the system will write a summary that has 2 main goals:

* To provide the rest of the companys employees easy access to information detailing the cause of the outage. Often outages can have a huge impact on a company, so managers and executives have to understand what happened and how it will impact their work.
* And to ensure that the root cause(s) of the outage has been discovered and that measures are taken to make sure it will be fixed.

Timeline
* July 9, 2021 - It is reported that remote collection points are constantly failing in the process of collecting taxes and that the system does not allow retrying collection.
* Julu 10, 2021 - It is identified that the collection model for which the system was originally designed is not suitable from the architectural point of view for the new collection model.
* July 11, 2021 - Return to the previous collection model while developing new functionality to support the desired model.
* October 26, 2021 - The new functionality that supports the new tax collection model will be released.

Root cause
The way the tax is collected should represent a change in the software architecture and this change was not made.

Previous modality

* To pay their taxes, the citizen had to go to the municipal administration office.
* Once in the collection office, stand in line and wait for your turn
* Each transaction was processed by the collection officer while they waited for the system's response, and when that happened, the transaction went on to the next person in line.

New modality

* The citizen approaches a lottery collection point and informs that he is going to pay the municipal tax.
* The collection officer processes the payment online and notifies the citizen of the result.

In the previous model, since citizens lined up, the processing for the central system was linear.

On the other hand, in the new modality citizens went to the different collection points and these, in turn, were connected in parallel to the central system to process the collection of the tax.

It was this parallel processing that caused the server to crash and cause loss of transactions.

Corrective and Preventive Measures
The demand processing architecture was changed and the published/subscribed messaging pattern was implemented.

On the other hand, it went from waiting for the confirmation of the collection waiting on the file to collect immediately and notify the processing once it has been done in the central system.

This enabled the system to withstand peak processing demand of up to 10,000 transactions in one hour with no changes to the hardware, operating system, or database engine.
