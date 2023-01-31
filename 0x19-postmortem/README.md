Postmortem
postmortem


https://user-images.githubusercontent.com/105058306/215726489-4b6df178-7f9f-4a78-b4ba-e33a92c32bb9.mp4


Any software system will eventually fail, and that failure can come stem from a wide range of possible factors: bugs, traffic spikes, security issues, hardware failures, natural disasters, human error Failing is normal and failing is actually a great opportunity to learn and improve. Any great Software Engineer must learn from his/her mistakes to make sure that they wont happen again. Failing is fine, but failing twice because of the same issue is not.

A postmortem is a tool widely used in the tech industry. After any outage, the team(s) in charge of the system will write a summary that has 2 main goals:

1. To provide the rest of the companys employees easy access to information detailing the cause of the outage. Often outages can have a huge impact on a company, so managers and executives have to understand what happened and how it will impact their work.
2. And to ensure that the root cause(s) of the outage has been discovered and that measures are taken to make sure it will be fixed.

Timeline
* March 2, 2019 - It is reported that remote collection points are constantly failing in the process of collecting taxes and that the system does not allow retrying collection.
* March 3, 2019 - It is identified that the collection model for which the system was originally designed is not suitable from the architectural point of view for the new collection model.
* March 4, 2019 - Return to the previous collection model while developing new functionality to support the desired model.
* March 25, 2019 - The new functionality that supports the new tax collection model will be released.
