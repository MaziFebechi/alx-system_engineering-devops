Server Outage Incident report


13th May 2023, we experienced server outage on all our server infrastructure which resulted in our clients inability to use our services and we sincerely apologize for the financial loss our clients have incurred during this period.

Issue Summary


On 13th May 2023 (2:00PM GMT + 1), we experienced a server outage (downtime) on all of our server infrastructure which lasted for 15 minutes. As a result of this, our clients experienced a http 500 error which had a 100% impact on their business as they were unable to access our services. The root cause was not properly testing out all implemented upgrades before pushing to production servers.

Timeline (all time in GMT + 1)


Time (GMT + 1)	Actions
1:55 PM	Upgrades implementation begins
2:00PM	Server Outage begins
2:00PM	Pagers alerted on-call team
2:05PM	On-call team acknowledgement
2:06PM	Rollback initiation begins
2:08PM	Successful rollback
2:08PM	Server restart initiated
2:10PM	100% of traffic back online
Root cause


At 1:55PM (GMT + 1) server upgrade was initiated across all our production servers without first releasing on our test environments and performing all necessary unit testing. Part of the upgrade being shipped to production server required an authentication from a 3rd party software, this new implementation is not supported on the current version present on our servers which resulted in the downtime experienced. We were able to resolve this quickly by first performing a rollback the severs previous state thereafter upgrading the current version on our servers.

Preventive measures


Pushing all intended changes 1st to our test environments before shipping to live server.
Increase the performance metrics threshold to alert on-call engineers on the event of possible server crash
