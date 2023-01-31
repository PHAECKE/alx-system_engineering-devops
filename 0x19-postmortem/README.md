Postmortem




![image](https://user-images.githubusercontent.com/105058306/215735407-5a6eebd8-c4ef-4ff3-b5d0-217f03da4a8d.png)





Any software system will eventually fail, and that failure can come stem from a wide range of possible factors: bugs, traffic spikes, security issues, hardware failures, natural disasters, human error Failing is normal and failing is actually a great opportunity to learn and improve. Any great Software Engineer must learn from his/her mistakes to make sure that they wont happen again. Failing is fine, but failing twice because of the same issue is not.

A postmortem is a tool widely used in the tech industry. After any outage, the team(s) in charge of the system will write a summary that has 2 main goals:

* To provide the rest of the companys employees easy access to information detailing the cause of the outage. Often outages can have a huge impact on a company, so managers and executives have to understand what happened and how it will impact their work.
* And to ensure that the root cause(s) of the outage has been discovered and that measures are taken to make sure it will be fixed.

Timeline
* March 2, 2019 - It is reported that remote collection points are constantly failing in the process of collecting taxes and that the system does not allow retrying collection.
* March 3, 2019 - It is identified that the collection model for which the system was originally designed is not suitable from the architectural point of view for the new collection model.
* March 4, 2019 - Return to the previous collection model while developing new functionality to support the desired model.
* March 25, 2019 - The new functionality that supports the new tax collection model will be released.

Root cause
The change in the way the tax is collected should represent a change in the software architecture and this change was not made.

Previous modality

* To pay their taxes, the citizen had to go to the municipal administration office.
* Once in the collection office, stand in line and wait for your turn
* The collection officer processed each transaction waiting for the response from the system and once it was completed, it passed to the next in line.

New modality

* The citizen approaches a lottery collection point and informs that he is going to pay the municipal tax.
* The collection officer processes the payment online and notifies the citizen of the result.

In the previous model, since citizens lined up, the processing for the central system was linear.

On the other hand, in the new modality citizens went to the different collection points and these, in turn, were connected in parallel to the central system to process the collection of the tax.

It was this parallel processing that caused the server to crash and cause loss of transactions.

Corrective and Preventive Measures
The demand processing architecture was changed and he publish/subscribe messaging pattern was implemented.

On the other hand, it went from waiting for the confirmation of the collection waiting on the file to collect immediately and notify the processing once it has been done in the central system.

This enabled the system to withstand peak processing demand of up to 10,000 transactions in one hour with no changes to the hardware, operating system, or database engine.
