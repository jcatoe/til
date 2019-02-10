# Reliability

> **reliablility:** the system will continue to work correctly even when something within the system goes wrong or a user performs an action incorrectly

Sometimes we may need to sacrifice reliability such as when developing a prototype product or when providing a service with a narrow profit margin, but you should **always** be aware of when you are cutting corners.

## Faults
> **fault:** when a condition deviates from the standard expectation at the component, equipment, or sub-system level but does not cause the entire system to crash

> **fault-tolerant:** when a system can handle faults without human intervention

A fault is _not_ the same as a failure because a failure occcurs when the system as a whole has stopped providing the required service to the user.

To ensure that a system is fault-tolerant, it can be helpful to deliberately trigger faults by incorporating fault injections into the test suite.

### Types of faults:

* Random fault: a fault that occurs as a result of wear or other deterioration.

A hardware fault cannot be predicted, but measures do exist that calculate the rate at which hardware will fail. For example, mean time to failure (MTTF) is a calculation for a hard disk's lifespan. It is expected that most hard disks will experience failure within 10-50 years so if you had 10,000 disks, you should _expect_ one disk to die per day.

To protect systems against hardware faults, it is common to add redundancy to the individual hardware components. Examples include setting up RAID configurations, having dual power supplies, adding hot-swappable CPUs, having batteries and diesel generators for backup power.

* Systematic fault: a fault that occurs as a result of a software bug, a runaway process, slow services, or cascading failures

A software fault is much harder to anticipate because the software is usually making some kind of assumption about its environment and sometimes that assumption stops being true.

Humans are responsible for most outages so it is helpful to always think about assumptions and interactions in the system. A strong test suite can be used to catch a lot of these situations and adding checks to the code can ensure that incoming data is as expected. When designing an application, make it easy to do the right thing and discourage the wrong thing; however, you must find a balance as humans tend to create workarounds if something is too difficult to use. During the development phase, make sure sandboxes are available so that ideas can be tested before touching production. When making changes to the application, roll out the changes slowly. Make it easy to revert back if something goes wrong. Setup monitoring and alerts for unexpected behaviour. Tests. Tests. Tests.

Failures in hardware can be caused by random faults _or_ systematic faults, but failures in software are _always_ systematic.


-------------------------
**Further Readings:**
* [ ] A theory of software reliability and its application, John D. Musa , Bell Laboratories, Whippany, N.J. 07981

**Sources:**

¹ Kleppmann, Martin. _Designing Data-Intensive Applications: the Big Ideas behind Reliable, Scalable, and Maintainable Systems._ OReilly Media, 2018, pp 6
