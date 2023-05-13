Server Outage Incident report
![68747470733a2f2f74332e667463646e2e6e65742f6a70672f30342f39322f30392f37322f3234305f465f3439323039373234365f79616745387839556b384d3949656b50793747427545307831556f61376573442e6a7067](https://github.com/MaziFebechi/alx-system_engineering-devops/assets/111000547/44b36f79-7ea7-43c4-9491-59566c472be5)

13th May 2023, we experienced server outage on all our server infrastructure which resulted in our clients inability to use our services and we sincerely apologize for the financial loss our clients have incurred during this period.

Issue Summary
![68747470733a2f2f7777772e6369656e6f7465732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031392f30372f73756d6d617279626c61636b626f6172642e6a7067](https://github.com/MaziFebechi/alx-system_engineering-devops/assets/111000547/48f07c8c-f9e5-414f-856e-1b27890a8f9d)

On 13th May 2023 (2:00PM GMT + 1), we experienced a server outage (downtime) on all of our server infrastructure which lasted for 15 minutes. As a result of this, our clients experienced a http 500 error which had a 100% impact on their business as they were unable to access our services. The root cause was not properly testing out all implemented upgrades before pushing to production servers.

Timeline (all time in GMT + 1)

![68747470733a2f2f7777772e6e636261722e6f72672f77702d636f6e74656e742f75706c6f6164732f323032322f30322f54696d656c696e652d56697375616c2d333030783134352e706e67](https://github.com/MaziFebechi/alx-system_engineering-devops/assets/111000547/e247fe10-2eb6-4e89-b2c2-c0b9a78aa1d6)


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
![68747470733a2f2f626c6f672e73797374656d73656e67696e656572696e672e636f6d2f68732d66732f68756266732f626c6f672d66696c65732f526f6f7425323043617573652e6a70673f77696474683d363030266e616d653d526f6f7425323043617573652e6a7067](https://github.com/MaziFebechi/alx-system_engineering-devops/assets/111000547/16f0a903-fdc1-421a-8684-30db182d3177)

At 1:55PM (GMT + 1) server upgrade was initiated across all our production servers without first releasing on our test environments and performing all necessary unit testing. Part of the upgrade being shipped to production server required an authentication from a 3rd party software, this new implementation is not supported on the current version present on our servers which resulted in the downtime experienced. We were able to resolve this quickly by first performing a rollback the severs previous state thereafter upgrading the current version on our servers.

Preventive measures


Pushing all intended changes 1st to our test environments before shipping to live server.
Increase the performance metrics threshold to alert on-call engineers on the event of possible server crash
