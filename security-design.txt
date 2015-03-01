# Security by design

By Bennett Todd <bet@rahul.net> 2015-02-27
Some thoughts on creating and maintaining secure computer systems. 

## Scope

Security can only be defined in the context of what you intend to have happen, and what you don't. For example, if you intend to keep data private, extralegal surveillance constitutes a security breach.  Therefore, to make rational choices, you must define goals and environment. Define who should be able to do what, early, and review the definition periodically, to make sure it, and the design that flows from it, continue to match your intentions. 

## Definition 

Security is a subset of reliability. There are many things that can cause a system to fail; unless you have adversaries with more resources than the omnipresent threats of mischance and random failure, security threats are unlikely to be the most likely source of expensive failures. The design techniques to avoid the losses from random hardware failures and human error also make a system resistant to intentional attack. 

## Security Policy

A security policy is the foundation on which security is built. It must state clearly the scope of the system, its users, its value, and the risks to be avoided; these risks are traditionally enumerated via the mnemonic CIA, for Confidentiality, Integrity, and Availability. These list the attributes threatened. 

All measures to ensure security come with some cost, but if the costs are fairly balanced against the costs and likelihood of failure, the result can be sound and justifiable. 

## Change management

Change must happen; new things must be done, bugs must be fixed, needs change. But making changes is an easy way to break things. To take the pain out of changes, they must be managed. A good approach is to have different people (or groups) responsible for development and testing, and to package up releases of software with both automatically generated descriptions of what has changed, and manually written explanations of why; at each stage of the installation, e.g. from development to testing,  or from testing to production, the folks responsible for creating the change should discuss with the folks who will be blamed when it fails, and both should sign off approving that install. 

## Testing

If we could write programs that always did what we want, regardless of the environment, life would be much easier. Since we can't, we should write, document, and maintain automated tests to confirm that the program still works as intended. These we run early and often. 

Any time the environment changes, you want to be able to confirm that you didn't just break something. 

## Inventory

You need to know your systems, and your users. For each system, you need to know its hardware, and the exact software installed on it. For each user, you need to maintain accurate details of what they should be permitted to do, and whether they still should be permitted. These catalogues should be populated with as much automation as possible, periodically updated to track changes, and used as the basis for automation. If the procedure for adding a computer, or a user, consists of adding them to the database, then running an automated procedure, the database can be complete and correct first, and subsequent surveys only need to pick up changes, made intentionally or not, legitimately or not, to the environment. Thus monitoring the changes caught by automated surveys can be a valuable security alert system. 

## Backups 

If you can always restore every system to its functional state with no warning, you can respond to various failures, from disks crashing to ransomeware. Needless to say the backups cannot introduce a breach to access control. In the days of paper records, secure off site storage was a routine business expense. It still should be. Shredders are a worthwhile idea too, data you don't keep can't be stolen from you. 

## Automation 

If you do something that takes more than one step, it shouldn't be done by hand, unless you're fiddling about in development. Everything done in production should be automated. Foresight is imperfect, there must be a way to fix things unexpected. Call such procedures "break the glass", and document every use. Repeat use is a good case for more automation.

## Documentation

New administrators must be hired, and trained; and if the environment isn't prevented from growing too complex and diverse, even experienced staff will want to be able to confirm the steps to do routine tasks.  The cost of high quality documentation is perhaps the clearest justification for improved automation. 

If your new hire training document fits on one page of large type, you're doing well. 

## Redundancy

Hardware fails, and so does software.  A relatively simple defense against hardware failure is duplication of hardware; and it can be done in a way that allows more devices, each individually cheaper, to work together to scale up the capacity of the system as the workload increases; this in turn is a great help both for reducing service outage from hardware failure, and improving resiliency in the face of load based attacks (DDoS). 


## Monitoring 

You need to know what's happening to your systems. When hardware is added, or fails, when the configuration changes, or performance is lost, you would rather be the first to know. 

### real-time alerts

Some things, like the correct function of your network and the components of which it's built, are cheap and easy to monitor in near real-time, and are important enough to merit the effort of responding to alerts. 

### periodic audits

Other things, like the inventory of software installed on every machine, and the continued match between the documentation of file size, permission, and contents with the data actually on the disks, is sufficiently costly to compute and sufficiently voluminous to read, that it might be better suited to a manual operation. Even if you don't run that audit on any regular schedule, it's comforting to have when something breaks. For example, if someone alerts you to a security breach, it's one of the first things you'll want to reach for. 

## Access control

Even the easiest systems, those only intended to publish read-only copies of public data for free to anyone, still need to be updated; other systems have more elaborate and complex needs. The first half of such control involves enumerating and then identifying permitted users. Identification is hard; passwords are a weak protection and yet impose a burden on users; better techniques tend to increase both monetary cost and inconvenience (which aren't entirely distinct). 

Every user should have a distinct login, with distinct credentials, else your authentication fails to identify the user; sharing passwords is a direct attack on the integrity of the system. 

## Entitlement management

Once a user is identified, and they have proven their identity, you must determine what they should be permitted to do, and see. 

## Partitioning

Firewalls control traffic between networks with different security policies, access databases, or entitlements. 

It can be urgently important to partition your network to accommodate such distinct zones. For example, a network on which users exchange executable programs (like pdf documents) via Internet email should be a separate network from one with devices that control expensive industrial processes, or manage security credentials for customers. 

## Intrusion Detection System (IDS)

An IDS can be useful for characterizing traffic. The process of tuning an IDS involves documenting all legitimate categories of traffic, and can reveal firewall configuration flaws. An IDS can also expose "doorknob twisting", the probes that are the first stage of recognizance in an attack. 

## open source
Is better, because every user has incentive to improve the system

