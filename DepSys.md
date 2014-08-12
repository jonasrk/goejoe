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
	* Reliabilty: "Doing something as long as required without interruptions"
* Fault-tolerant computer system: Continues correct service provisioning in the presence of faults
	* Fault-tolerance: "We accept the fact that something breaks, but system is designed to deal with this"
* Realt-time computer system: Deliver a service given time constraints.
	* Typical: Safety controllers

# DepSys - Dependability Threats & Faults - 1 System Integration Levels
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