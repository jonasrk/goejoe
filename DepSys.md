# DepSys - Introduction - 1 Dependability
## Dependability as Umbrella term
* for non-functional attributes
* costs vs. performance vs. dependability
* terminology very important (minimum to pass the course)
* different definitions, one e.g. by Laprie
    * "Dependability is the trustworthiness of a computer system such that reliance can be placed on the service it delivers to the user"
* Fault tolerance a perspective problem?
	* e.g. HTML: Browser is fault-tolerant
	* airplane? yes.
	* in software? exceptions? no - just go to statement. developer is implementing the fault tolerance.
* How to deal with unexpected events?

## Computers in Safety-Critical-Systems
* e.g. airplanes
* tendency towards that all kinds of systems or products use computer systems
	* what does this mean to safety?
	* software replaces human operators
	* this happens due to cost control

# DepSys - Introduction - 2 Examples
* Therac 25 Radiation therapy engine
* Patriot Missile Launcher
* Ariane 5

# DepSys - Introduction - 3 More Examples
* Mars Pathfinder
* Air France AF 447 (May 2009)

# DepSys - Introduction - 4 Importance of Dependability for Business
* estimate potential loss of an outage and the cost to prevent it
* this lecture will also be about distributed systems

## Tradeoffs
* Buy distributed System or Mainframe?
* Example: Boeing 777 Flight Controller
* p 1x10^-10 for degradation from "MIN-OP configuration"
	* How can you prove this?
* Example: VAX Hardware Redundancy
	* avoided single point of failure
* If you want to have something fault tolerant, make it redundant!
	* But how much and where and how?

## Terms
* "A seg fault can lead to system failure"
* we will have more and more software and safety critical systems

# DepSys - Introduction - 5 Course Topics
* Definitions and metrics
* Fault tolerance patterns
* Analytical evaluation

# DepSys - Dependability Threats & Faults - 1 Dependability
## Definitions and Metrics
* Dealing with unexpected events
* Reliability Engineering is job description
* IEC definition: reliability performancy, maintainability performance and maintenance support performance

* can you have low cost, high dependability and performance?
	* e.g. desktop computers: optimized for cost and performance
	* e.g. server systems: optimized for performance and dependability
	* where does performance not matter?
		* ICUs in cars? but at least a realtime system (minimum performance?)
		* performance matters almost everywhere
	* usual question: how much does a customer want to pay for dependability?
	
## System Type Examples
* Dependable (reliable) Systems: Delivers required service during its lifetime
	* Reliabilty: "Doing something as long as required without interruptions" -> "Car should not stop to drive."
* Fault-tolerant computer system: Continues correct service provisioning in the presence of faults
	* Fault-tolerance: "We accept the fact that something breaks, but system is designed to deal with this"
* Realt-time computer system: Deliver a service given time constraints.
	* Typical: Safety controllers

# DepSys - Dependability Threats & Faults - 2 System Integration Levels
* Where to start make a Java EE Application reliable?
	* Put it in a virtual machine?
	* We need to know what fails most often!
		* Rule out common cause failures!
			* Different hardware!
* You need to think about the whole stack.
	* Every layer makes it more difficult
	
## Dependability Stakeholders
* System: Entity with function, behavior, and structure
	* a number of components or subsystems, which interact under the control of a design
	* may be pure hardware or software
* Service: System behavior abstraction, as perceived by the user
* User: Human or pysical system that interacts with the systems service
* Specification: Definition of expected service and delivery conditions

* Reliance demands assessment of non-functional dependability attributes
* Provide ability for trustworthy service delivery by dependability means
* Undesired (maybe expected) circumstance form dependability threats

# DepSys - Dependability Threats & Faults - 3 Dependability Tree
* Tree is terminology framework
    * Attributes, means and threats
* security and dependability historically not too good friends
* security: CIA triangle
* dependability has a solid mathematical framework
* there is a tendency to put security in dependability attributes
* this stuff was invented when there was no internet

## Threats
* Fault is the origin
* Question: does fault lead to failure?
* with a fault the system may still work - fault tolerance
* most mechanisms prevent failures
* * failure: system does not work as specified
* error: "Fehlerzustand" - part of system state that can lead to subsequent failure, prevent with fault tolerance!

## Attributes
* measure your efforts

# DepSys - Dependability Threats & Faults - 4 Chain of dependability Threats
* example: one cpu fails - when does the computer fail?
	* how much memory can fail until the system breaks?

* subsystems failure becomes the root fault for a higher level
* activation, propagation, causation

## Netflix Software Architecture
* possible error propagation chain?
	* how does this architecture prevent it?
* go in each and every box and reason about what happens if this component fails, also probability

# DepSys - Dependability Threats & Faults - 5 Faults
## What kinds are there?
### Fault nature
* accidental faults (e.g. physical)
* intentional faults (e.g. attacks)

### origin
* physical/natural (prevention: higher quality hardware, cooling, EM-shielding)
* human-made (prevention: multiple eyes, testing, ...)

### system boundaries
* internal (part of system state)
* external (interference with environment)

### phase of creation
* design faults
* operational faults

### temporal persistence
* permanent faults (prevention: redundancy)
* temporary faults (you may even work without redundancy - e.g. retry)

# DepSys - Dependability Threats & Faults - 6 Observations on Faults
## Is an external fault a design fault?
* typical: operational conditions are underspecified.
* replacing broken version of same component leads to recurrent faults (bad in software - e.g. memory leaks)

* transient faults: temporary external accidental physical faults
* intermittent faults: temporary internal accidental faults (e.g. system overload)

* a fault is active when it produces an error
* a non-active internal fault is a dormant / passive fault
* Heisenbug, Bohrbug, Mandelbug

* Fault-tolerant system design is a contradiction

# DepSys - Faults & Errors - 1 Recap
## What is Dependability? / What is a dependable system?
* Dependable Systems are available and reliable.
* We have an expectation of how a system should work. If this expecatation is fullfilled, then we have a dependable system.
* Non-functional attributes: It is about how a system is doing something - not about what it is doing.
* Specification is needed! Dependability is about this.

## Threats
* Difference between faults, errors and failures?
	* originating fault (Fehlerursache)
	* errorous state
	* system failure

* Fault tolerance?
	* every activated fault leads to an error
	* then you have mechanisms to prevent failures
	
* Chain of Dependability Threats: Fault activates Error - Error propagates Failure - Failure causes Fault of higher level system

## Faults
* What are my threats? What has a high likelihood to happen?
	* permanent (e.g. real programming bug) vs. temporary (may go away by itself)? 
		* how to protect me from it?
			* retry or redundancy?
	* accidental vs. intentional
		* include malicous attacks
	* physical vs. human-made
		* temperature, humiditiy, ...
		* people not following manual
	* design vs operational
		* code-review, testing
		* bad data import
* transient faults is what happens to hardware
* intermittent are similar to transient but internal
* physical faults are always accidental

# DepSys - Faults & Errors - 2 Fault Characterization
## Laprie & Kanoun
* What can happen?

## Fault Model
* Research is all about hardware - does not exist about software
* physics, circuit level ...

## Physical Faults
* biggest problem: memory problems
	* energized particles from space
* lowest level possible: transistors

# DepSys - Faults & Errors - 3 Fault Model for Semiconductor Memories
* Who's responsible to deal with these faults?
	* MemCheck
	* but at runtime?
* any kind of fault tolerance costs you material, cycles or performance

## onion ring model
* what can happen on system level?
* fault model (should be called failure model)

* fail stop fault: system stops all operations, notifies the other ones
* crash fault: system looses internal state and stops without notifications
* omission fault, timing fault, computation fault
* byzantine fault: all-inclusive class / every possible fault

# DepSys - Faults & Errors - 4 Errors
* Errors maybe propagate through the system or even failures
* escaleates depend on redundancy, system activity and specification of the failure case

## Hardware Error Models
* hardware faults effect state information
* single data error or single code error

* same fault in different locations can have different fault classes
* avoid originating causes to avoid error cases

* in software?

* what software deals with error states internally?
	* operating systems deal with error situation
		* unplugged USB device?
	* file systems are really good in dealing with error states
	* version control systems?
		* fault model?
	
# DepSys - Faults & Errors - 5 Software Error Models
* syntactical and semantical errors
* under research in software engineering field - usually through field studies

## Error propagation
* same as before

* typical way of detecting an error?
	* log messages
* fault -> undetected -> detected -> error message

# DepSys - Failures - 1 Recap
## Dependable Systems
* Attributes we want to care about with dependability means
* Example for an error state?
	* BitFlip
* When do we know that we have a system failure? / Difference between fault and failure?

## Fault Models
* follow well defined principles to classify faults (e.g. onion model)
	* if you protect yourself from outer layers you protect inner layers for free
* vulnerabilities as security faults

# DepSys - Failures - 2 Hazards
* A hazard is a safety error
* active hazard situation is leading to loss event called accident
* harard analysis demands critical thinking
* example: water boiling kettle
	* what could go wrong?
		* water leakage
		* broken wire
		* overheating due to lack of water
		* ...
		
# DepSys - Failures - 3 Failures
* Fail-silent systems - incorrect results are not delivered
* fail-stop - constant value is delivered
* software can work well with fail-silent
* fail-silent is harder to implement
* fail mode domain - what is influenced
	* value failures - service results
	* timing failures - service timeliness
	* stopping failures - service availability
* thing in error states and build fault-tolerance around this

# DepSys - Failures - 4 Failure Severity
* How big is the problem?
	* What is critical and what is not critical?
* Catastropic failures
	* cost of failure mich larger than service benefit
* stopping failure: catastrophic in flying airplane - benign in train
* definition in airplanes:
	* catastrophic: loss of ability to continue safe flight and landing
	* major: reduced airplane or crew capability to cope with operating conditions
	* minor: no significantly reduced safety
	* no effect
* likelihood and severity matrix

## failure types

## swiss cheese model
* medical research
* not let errors propagate through

# DepSys - Failures - 5 Observations on Failures
* heavy loaded system -> higher activation chance
* system have wear out
* memory leaks in software = software wear out

## Means for Dependability
* fault tolerance should be error tolerance
* fault forecasting: think about what might happen

* fault intolerance techniques: fault prevention, removal
* fault tolerance techniques: fault forecasting, tolerance

# DepSys - Failures - 6 Fault Prevention
* Specific approaches for avoiding faults
	* general engineering procedures
	* software engineering procedures, ...
* Fault Removal
	* testing (test coverage: percentage of code covers)
* golden unit: reference system for comparison of output for a giving input (e.g. reference implementation)

* is easier to put a lot of effort in to software testing than later deal with the error states (hardware is different)

# DepSys - Fault Tolerance - 1 Means for Dependability
* offline techniques:
	* Fault removel: Take bug out that is already in there
	* prevention: make sure they get not introduced in the system
* online technique: tolerance - at runtime detect and react on error
* forecasting

* golden unit in software is reference implementation (e.g. old version)

# DepSys - Fault Tolerance - 2 Fault tolerance
* k-fault: how many faults can the system deal with at the same time?
* tolerance is the use of redudnancy (time or space) to achieve the desired level of system dependability

* redundancy in biology?
	* two kidneys
	
* when do you have enough fault tolerance?

* knowing is not possible - you can only make very good estimations

# DepSys - Fault Tolerance - 3 Phases of Fault Tolerance
* fault tolerance mechanisms has to detect errors (e.g. software raid)

* Latent fault - fault activation -> error - error detection -> error recovery / mitigation -> normal operation - fault treatment
* error detection - damage confinement - error processing recovery / compensation - fault treatment

# DepSys - Fault Tolerance - 4 Error Detection
* two redundant copies to see that you have a problem, three copies to know who has a problem

## replication check
* replication checks demand independent failures

## timing checks

## reasonableness checks
* semantics checks on the data

* replications checks are powerful and expensive