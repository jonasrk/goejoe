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