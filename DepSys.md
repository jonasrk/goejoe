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

# DepSys - Fault Tolerance - 5 Damage Confinement
* System decomposition
* law-governed architecture
	* monitor program
* strongly typed languages

## Error Processing Through
* Forward error recovery
	* e.g. error correcting codes
	* e.g. non-journaling file system
	* error is masked to reach again a consistent state (fault compensation)
* Backward error recovery
	* Roll back to previous consistent state
	
* Forward & Backward Recovery is part of database systems

# DepSys - Fault Tolerance - 6 Fault Treatment
* Fault diagnosis - what is the orinating cause?
* Fault passivation - replace & or let system repair itself (automatic fault passivation)
	* complicated for memory
	* easy for storage
* Software rejuvenation
	* gracefully terminating and immediately restarting
		* works for every kind of ressource leakage
* Fault tolerant mindset
* second mindset: "fail-fast"
	* don't do fault-tolerance, let it crash as fast as you can
	* if recovery is to expensive, than its better to not try to recover
	
# DepSys - Architectural Patterns - 1 Phases of Fault Tolerance
* Fault tolerance is primary method of achieving reliable system
* each undetected bug in software is latent fault
* error state needs to be detected
* Hamner book is about design patters for this
* design pattern = template
* Architectural, detection, error recovery, error mitigation, and fault treatment patterns

# DepSys - Architectural Patterns - 2 Units of Mitigation
* build system of components, define modules, modules care for themselves
* e.g. web server, business logic, ...
* choice of granularity e.g. based on recovery possibilites
* unit is too small when you do not know what to do in error state

## Error Containment Barrier
* in nuke plant huge containment building
* protect unit of mitigation boundaries
* in software e.g. VMs or firewalls

### e.g. babbling idiot problem
* can bus in car
* broken guy that talks whatever he wants whenever he wants
* error containtment barrier = bus guardian

# DepSys - Architectural Patterns - 3 Correcting Audits
* Data element corruption
* audit: go over the data, find it and maybe even correct it
* correctnes criteria: structual criteria (linked list: does everyone have a link)
	* known correlations (every user should have email address)
	* sanity checks (checksum)
	* direct comparison (raid1)
* automatic correction is often easy

## Redundancy
* spatial (e.g. VAX)
* temporal: retry, roll-forward
* informational: checksum (not payload)

* redundancy for performancy improvement (e.g. scalability)

* Replication: Ensuring consistency between redundant resources
	* active replication: everyone is doing the same actions
	* passive: performs activity on one replica and transmits the delta
	* overhead to compute the delta? are same operations even possible (not with random numbers)?
	
# DepSys - Architectural Patterns - 4 Example: PostgreSQL 9 Redundancy
* shared disks or shared-nothing setup
	* in shared nothing many repliaction modes
* block-device
* Point-In-Time Recovery (PITR), ...

# DepSys - Architectural Patterns - 5 Humans
* Minimize Human Interaction
	* 
* Maximize Human Participation
	* Humans are good in finding originating problem
	
# DepSys - Architectural Patterns - 6 Maintenance Interface
* examples? BaseManagementProcessor gets own IP address, software interface into the hardware
* you need second entry point - completely decoupled from system

## Someone in Charge
* For every fault tolerance activity there must be a clearly identifiable responsible
* single failure point (vs. redundancy)

## Escalation
* escalate to higher level
* e.g. telephone switches

# DepSys - Detection Patterns - 1 Recap
## Redundancy
* three classes
	* temporal: retry
	* informational: additional peace of data that is not payload
### spatial
* replication
	* how to update?
		* active: do the same to all copies (must be deterministic)
		* passive: actions only on one copy, others get delta
	* table level vs. row level synchronization?
		* table: longer waiting time
		* tradeoff is frequency of updates cs. waiting time
		* typically smarter to have coarse grained synchronization (at least perfomance wise)
			* but you increase the chance to get out of sync
			
# DepSys - Detection Patterns - 2 Fault Correlation
* stop detecting single faults - instead try to categorize
	* detect classes of errors
* prepare your systems for bug that occured in testing
	* maybe runtime is on different machine that could lead to different errors
	* many times at runtime other problems occur
	
## System Monitor / Heartbeat
* seperate module that survails the system
	* typically through heartbeat
	
## Acknowledgment / Watchdog
* Alternative for Heartbeat
	* nowadays normal mechanism
* Piggybacking: ack info is included in response data frame

* Watchdog: passively look on results

# DepSys - Detection Patterns - 3 Realistic Threshold
* how much time before system monitor takes action?
* roughly how long it should take for a heartbeat to go over the wire
* then, how many heartbeats have to be missing?
* hypersensitive systems tend to jitter (permanent recovery)
* assume gaussian distribution?
* classical machine-learning mechanisms
	* hard thresholds do not work
* better avoid threshold and build systems that can say "i have a problem"

# DepSys - Detection Patterns - 4 Voting
* exact voting: correct result or uncertainty state notification
* with two out of three broken devices? unrealistic, because voting happens on numerical results
* typically devices stop delivering - therefore fail-silent
* inexact voting: 6 position after point may not matter -> maximum discrepency (e.g. temperature sensors)
* vote on megabytes of data? compare only checksums!
* what happens when the voter fails? cascaded voters! but in the end you still need one ultra-reliable voters

# DepSys - Detection Patterns - 5 Maintenance and Exercises
* Routine Maintenance
	* From time to time, trigger a failover - just to see if it works or not
* Routine Audits (scrubbing, e.g. memory scrubbing - test all memory cells)
* checksums - informational redundancy
* Leaky Bucket Counter
	* Units of mitigation -  distinguished between transient and intermittent faults
	* counter that counts faults
	* decrement counter from time to time
	* originally from networking, if transient, fault will reduce again
	* also works well for memory faults
	
# DepSys - Error Recovery Patterns - 1 Recap
* most important fault tolerance pattern? can't be a single one because of different phases
	* you need one good pattern in each phase

# DepSys - Error Recovery Patterns - 2 Error Recovery
* quarantine (e.g. state indicator from voting unit)
* concentrated recovery
	* downtime as short as possbile: use all ressources for recovery
	
# DepSys - Error Recovery Patterns - 3 Checkpoint
* useless for design faults
* great for transient faults (primary error recovery in high performancy computing)
* message passing (parallel) mechanisms hard to checkpoint, solved by Chandy & Lamport

## Individuals Decide Timing
* stop doing globally recovery but solve inconsistencies at recovery time

## Data Reset
* take initial values and approximate values (e.g. sensor values)

## Rollback / Roll-Forward
* Go to next valid system state and skip current computation

# DepSys - Error Recovery Patterns - 4 Remote Storage
* store checkpoints somewhere else
* in real-world over iSCSI

## Restart
* why don't we need checkpointing for software restart?
	* because often the problem is part of the state

## Limit Retries
* smartphone tries to connect over and over

## Failover
* What you do with your spatial redundant ressources
* active/active or active/passive better?
	* if input data is reason for error in active active both will likely fail
* dedicated spare vs. roaming spare vs. N + M

# DepSys - Error Recovery Patterns - 5 Redundancy Configurations for Failover
* N-to-1 and N+1 are special cases of Active/Passive
* Hot standby: On failover you need no ramp-up
* Cold standby: Standby system is off
* spare parts are a very cold way of a failover

## Dual Master Problem
* split brain: issues on interconnect could lead to several sub-clusters
	* typical solution: Quorum, count how many nodes you can reach
	
### Quorum approaches
* central arbitration: manual
* simple majority
* weighted majority
* tie-breaker

# DepSys - Error Recovery Patterns - 6 Examples
* Weighted Majority with Quorum (Sun)
* Windows File Server
* VMWare
* Error Migigation: IEEE Not a Number
	* also: Finish Wirk in Progress vs. Fresh Work Before Stale

# DepSys - Dependability Attributes - 1 Attributes of Dependability
* How to describe an measure dependability?
* you want numerical ways to talk about dependability
* problem with nun-functional attributes: fuzzy / weakly defined

## Reliability
* Reliability - how long is a system available without a problem
* today in IT more measures for availability
* difference between availabilty and reliability?
	* availability: lifetime - available or not available
	* availability: what percentage of time does it work?
	* reliability: for how long will it last without a problem?
	
# DepSys - Dependability Attributes - 2 Observations on Dependability Attributes
* avialability is always required
* reliability, safety, and security may be optional
* availability from system point of view (promise to the outside world)

## Reliability  Function R(t)
* Probability that a system is functioning properly and constantly over time period t

# DepSys - Dependability Attributes - 3 Probability of Events
* Instaneous availability and steady-state availability

## PDF & CDF
* PDF: discrete or continous random variable
* distribution functions
* Reliability function as continuous random variable
* general way of talking about reliability
* typically modelled as Poisson process

# DepSys - Dependability Attributes - 4 Failure Rate
* exponential distribution is memory-less and easy to compute

# DepSys - Dependability Attributes - 5 Failure Rate in Real World
* Hardware: Burn in, use, Wear out

## Weibull Distribution
* most widely used
* parameterized by lambda and k
	* k: shape
	* lambda: scale
* base failure rate modified by various factors
* also used: gamma and lognormal distribution

# DepSys - Dependability Attributes - 6 Steady-State Availability
* MTTF: Mean time to failure
* MTTR: Mean time to repair
* MTBF: Mean time between failures

* 5 nines = 5 minutes outage per year

* Example: Amazon - 3 nines
	* what happens if the promise is broken?
	
# DepSys - Steady-State Availability - 1 Recap
* What are reliability and availability?
	* reliability: continous availability over time. (mainly important for hardware)
	* availability: what percentage of time does system not have problem?
* PDF & CDF
* exponential distribution destribes failure rate with only the variable lambda

## unreliability function
* reliability is 1 - CDF

## steady-state availabilty
* we assume that a system can be repaired - up-down-up phases

# DepSys - Steady-State Availability - 2 Steady State Availability Example
* How do HDD vendors get the numbers?
	* historical data
	* test lab (run under stress condition)
* MTTR is provable, MTTF not
* Users like MTTR
* Define utility curve for recovery time

# DepSys - Dependability Modeling - 1 Dependability Modeling
* What now to do with the numbers?
* different standards for industry
* success space and failure space
	* it's usually easier to define a failure state
	
# DepSys - Dependability Modeling - 2 Inductive vs. Deductive
* Deductive: System has crashed, why did that happen?
	* Fault trees

## General rules
* binary states: either down or up (crash failure model)
* express failure probability
	* based on reliability or availability data
	
* basic idea: use boolean algebra
* talk about events
* calculate probabilities

* all other principles base on that idea

### serial case
* boolean AND
* multiply probabilities

# DepSys - Dependability Modeling - 3 Parallel Case

## K-of-N
* we have N components and need at least K running to have the whole system working
* serial system is N out of N
* parrallel is 1 out of N
* typical problem: people think that the dependability model is the system design

# DepSys - Fault Trees - 1 Recap
* inductive vs. deductive modelling
	* succes state and fail state modelling
* events need to be independent

# DepSys - Fault Trees - 2 Reliability Block diagrams
* Building blocks for serial and parallel structures
* also redundancy structure or k/n
* if there is a path from s to t the system is still working

* you can derive the structure formula from it

* lowest actionable item

## Complex RBDs
* serial and parallel parts not always obvious

* Coherent Structures: All components are crucial

# DepSys - Fault Trees - 3 Fault trees
* start model with system failure and deduct how this did happen
* root cause analysis, risk assessment, safety assessment

* RBD in success space and Fault trees in failure space
* you can derive structure formulas from both and translate

* how do you see single points of failure in tree?
	* direct connection to system failure event
	
# DepSys - Fault Trees - 4 Static Fault Trees
* Basic events: Initiating fault
* undevelop event: basic event with no information
* House event - failure might happen but we plan that to happen
	* e.g. maintenance
	
* repair in fault trees or RBDs?
	* not part of the model!
	
* voting or gate (k out of n)

# DepSys - Fault Trees - 5 Cut sets
* group of basic events that trigger a failure event

* minimal cut set
	* when all probabilites are equal cut set length is interesting
	
* singleton cut set - single point of failure

## Qualitative analysis
* helpful to find dominant minimal cut set

* event imporatance
	* ask yourself how important and event is for top event
	
## How to determine Cutsets
* Boolean reduction
	* computetionally complex
	* many heuristics
	
## Quantitave analysis
* put in probabilities

# DepSys - Fault Trees - 6 Assignment

# DepSys - State-Based Dependability Modeling - 1 Recap
* Fault trees
	* Boolean reduction
		* simple term to derive failure probability
		* derive cutsets
	* use cutsets for qualitative analysis
	* use probabilities for quantitative analysis

## MOCUS - Method for obtaining cut sets
* walk down the tree
* write and in seperate colums,
* write or gates as seperate rows

## Quantitative analysis of cut sets
* how to deal with AND gates?

* Fixing Cut Gates

## Dynamic Fault Trees (DFT)
* Functional dependency (FDEP) gate
* forces dependent events to occur on activation
	* for example good for power outage
	* or network fail
* can lead to circular dependencies
* Cold Spare (CSP) Gate
	* alternate inputs are not power initially but can function as replacement
	
# DepSys - State-Based Dependability Modeling - 2 Hypothetic Example Computer System
* Processors: Cold spare setup, dormancy factor 0 (cannot fail in passive mode)
* Memory: Broken interface triggers memory modules to fail immediately

## Fault Tree Contruction
* Identify Objective
* Define Top Event
	* precise and decomposable enough
	* not underspecify

### Errors
* Ambigous TOP event
* ignoring significant environment conditions
* inconsistent event names

* logic can be testet in succes domain by inverting all statements and gates

* Converting FTA to RBD

* Convert structures to RBDs in two different ways

# DepSys - State-Based Dependability Modeling - 3 Event Tree Analysis
* other tree based analyses method

# DepSys - State-Based Dependability Modeling - 4 State-Based Dependability Modeling
* you cannot capture state in Fault trees

## Dependability modeling
* component-based models: RBDs, FTAs
* State-based models: Markov chains, petri nets

* markov and petri are more powerful but harder to draw

# DepSys - State-Based Dependability Modeling - 5 Markov Chains
* markov property: next step depens only on the current stepseh

* Discrete-time and continupus-time

## Example
* k out of n system with n components

# DepSys - State-Based Dependability Modeling - 6 Petri Nets
* Graphical language to model systems
* conflicting transitions models not-determinism

* Example: Priority AND -> Stochastic Petri Net

* Token Game, Monte Carlo Simulation

# DepSys - State-Based Dependability Modeling - 7 Reliability tools
* overall procedure
	* System structure
	* Fault classes
	* Failure rates
	* Fault handling procedures
	* Repair procedures
	* Success criteria
	
* Real World Systems -> Model -> Solution Technique -> Evaluations

* Runtime Dependability Evaluation

# DepSys - State-Based Dependability Modeling Recap - 1 Markov Chains
## State-Based Dependability Modeling - Idea
### Basic Idea
* Petri nets and Markov chains

#### Types of Markov Chains
* DTMC? CTMC?
* What is this model supposed to tell us?
	* We model partial error states and their transitions
		* Either it's getting worse or better
		* How do be evolve to a system failure
		* transition probabilities
		* repair rates, spare components ... all can be expressed as states
* Rely on well known math -> Markov chains and petri nets

#### Markov property
* memoryless
* Discrete-time and Continuous-time
* Markov-simulator gives you statistical probabilities

# DepSys - State-Based Dependability Modeling Recap - 2 Petri Nets
* advantage: because of the tokens you don't have state explosion
* you can do model checking
* diversity: let different people do the same job
* MDD: model driven development
	* Audi does this for hardware all the time
	
## workflow
* real world systems -> model -> solution technique -> evaluations

# DepSys - FMEA - 1 Qualitative Dependability Investigation
* Qualitative modelling: We accept the fact that we have no probabilites or failure rates available

## Root cause analysis
* find originating fault

* investigation in entire organization

# DepSys - FMEA - 2 FMEA
* default when you don't have probabilites
* FailureModeandEffectsAnalysis
* from 1940s military usage
	* meanwhile in software and medicine
* get all engineers from different departments together and lock them in and ask them to fill out FMEA

## Goals
* prevent safety hazards
* avoid performance failure (e.g. production performance)
* preventing maintenance (how often)

# DepSys - FMEA - 3 FMEA Types
## SFMEA
* System FMEA
* Improve overall system design
* what are failure modes and results from failure modes

## DFMEA
* Design FMEA
* focus on failure modes reasoned by design deficiencies

## PFMEA
* Process FMEA
* analyze manufacturing and assembling processes
* how can the production fail?
* software: how can the development process fail?
* structurally analyze what can go wrong

* design: wrong specification - process: wrong usage

* Software FMEA, ...

## FMEA
* what are failure mode candidates?
* which effects are critical and which are not? prioritize
* Result is a list of failure modes and priorities

# DepSys - FMEA - 4 FMEA Worksheet
* The table
* First: items
* subjective severity numbers
* discuss causes
* probability 1 to 10
* multiplying values gives you risk priority
* detection probability may be left out, if you have no repair option

# DepSys - FMEA, FMECA & HAZOPS - 1 Recap
* idea behind quantitative analysis?
	* the numbers game
		* combine numbers to an overall number
* fault trees
* petri nets & markoc chains

## when do you use what?
* static vs. dynmic system
* fault trees: all events happen at once from the model approach
* stateful approaches: if you have repair in place

* FMEA: structural recipe what to do when you don't have numbers
	* derive severity ranking
	
# DepSys - FMEA, FMECA & HAZOPS - 2 Example: System FMEA of ATM
* RPN tells you what is the first thing to fix
* CRIT tells you what is the most nasty problem
* What about common cause failures?
* Starter questions
	* What is the consequence of failure?
	* What will the customer experience
	* Will the failure cause potential harm to the end user?
	* ...
	
# DepSys - FMEA, FMECA & HAZOPS - 3 Severity Rankings in Automobile Industry
* 1 No Effect, 2 - 4 Annoyance, 5 - 6 degration of secondary function, 9 - 10 safety and regulatory requirements
* Category 1 to 4 that effect mission

* Occurence Ranking

# DepSys - FMEA, FMECA & HAZOPS - 4 Software FMEA
* Difficult because software is moving much faster than hardware
* Failure to perform a function reliably, safely, when needed ...
* Prioritize FMEA Projects

## Common mistakes
* missing the forest for the trees
* team meeting attendance is crucial
	* 4 - 8 people is good
	
# DepSys - FMEA, FMECA & HAZOPS - 5 FMECA & HAZOPS
* Hazard & Operability Studies
* originally from chem plants
* secondary keywords (no, less, more, reverse, also, other, fluctuation, eary, late)
* you find all failure modes

## Hazops procedure
* do I have all keywords? ...

# DepSys - CMMI, Six Sigma & ITIL - 1 About the Assignment & Recap
* assignment 2: FMEA for flashlight in teamwork
* relationship between fault tree and FMEA
* Software FMEA about echo program

# DepSys - CMMI, Six Sigma & ITIL - 2 Root Cause Analysis
* take an existing failure that happen and find out what went wrong
* 5 Whys from Toyota manufacturing

## Why-Because graph (WBG)
* different events - find the links between them
* framwork to think in a structured way about possible event chains
* failure at top - at the bottom you end up with root events

# DepSys - CMMI, Six Sigma & ITIL - 3 RCA: Ishikawa/Fishbone Diagram
* head of fish is problem
* fish bones are differen factors (e.g. methods, place, manpower, procedures, ...)

# DepSys - CMMI, Six Sigma & ITIL - 4 CMMI
* CMMI Maturity Levels
	* Level 1: Initial
	* 2: process characterized but most parts are still reactive
	* 3: Processes are followed proactively
	* 4: Processes measured and controlled
	* 5: Optimizing, people are thinking on a daily basis how to improve processes
* How to achieve the levels?

# DepSys - CMMI, Six Sigma & ITIL - 5 Six Sigma
* Motorola trademark
* statistical metrics to improve output
* 7 six sigma levels

## DMAIC methodology
* Define, measure, analyze, improve, control
* not exact relevant

# DepSys - CMMI, Six Sigma & ITIL - 6 ITIL
* Information Technology Infrastructure Library
* Agile programming (Scrum) was counter development to ITIL
* no longer listen to engineer

## ITIL v3 Service
* someone is doing something and that costs money
* service value, level, assets, providers

* Service Lifecycle

* highest level of abstraction for dependability analysis

# DepSys - Reliability Prediction - 1 Predicting System Reliability
* where do you get initial probabilites from?
	* data harvesting
	
# DepSys - Reliability Prediction - 2 Reliability Data
## Field (operational) data
* from real world operation
* you have sensors in your devices
* it is still very hard to get data

## service data
* helpful in assessing time characteristics of reliability issues

* operational conditions many times unknown

* only way for prediction is to reduce variation

* recently: big data and only find correlations

# DepSys - Reliability Prediction - 3 Failure Probabily Sources
* original data, historical evidence, simulation or testing

## MIL-HDBK 217
* completely wrong
* emprirical failure rates for various electrical parts
* part count prediction

* Early estimate of a failure rate, given by
* part stress analysis prediction
	* part stress method
* environment factors well defined
* discontinued in `96
	* has been shown to be unreliable
	* failure rates in specification too high for todays electronic

## Telcordia (Bellcore)
* method 1: part count
* 2 1 extendend with lab test data
* 3: 2 including field failure data

* terlcordia more optimistic

# DepSys - Reliability Prediction - 4 Software Reliability Assessment
* Software bugs are transient faults

* Software Reliability Growth Models
	* When can we stop testing?
	* either concave or s-shape curve
	
# DepSys - Reliability Prediction - 5 Jelinski-Moranda Model
* tries to estimate failure rate for software
* assumption: all bugs are equal, repairs are perfect (bad assumption!)
* turned out to be somehow realistic

## White Box Approach - Software Metric

# DepSys - Reliability Prediction - 6 Halstead Metric
* Statistical approach
* program length, vocabulary size, program volume, difficulty level
* practice shows that it works well

* real problem: you cannot talk about reliability without having a proper fault model

# DepSys - Distributed Systems Theory - 1 Motivation
* how to BUILD fault tolerant systems?
* "Distributed programming is the art of solving the same problem that you can solve on a single computer using multiple computers"
* divide and conquer approach
* "a ds is a collection of indepented comptuer that appears to its users as a single coherent system"

* 8 Fallacies: network is reliable, latency is zero, bandwidth is infinite, network is secure, topology doesn't change, there is one admin, transport cost is zero, network is homogeneous

* buzzwords: high availability, disaster recovery, geographic distribution, big data

# DepSys - Distributed Systems Theory - 2 Divide and conquer
* abstractions: timing assumptions, failure model, failure detectors, consistency model

## Quiz
* why can it be problematic to measure only availability (e.g. in SLAs)?
	* how is the percentage distributed?

# DepSys - Distributed Systems Theory - 3 Timing Model
* Synchronous, partially synchronous (upper bound is known), asynchronous (unpredictable, most general model)

## Logical Time
* requires transitive "happend before" relation
* uncurrent if a not before b and b not before a

* clock drift -> need synchronization
* hierarchical network time protocol (NTP)

# DepSys - Distributed Systems Theory - 4 Fault Model
* Bynzantine Generals Problem
* Defend against arbitrary failures
* Failure Detectors
	* Model: Failure Detector, Completeness, Accuracy
* Distributed Systems Problems: Atomic broadcast, consensus, leader election, atomic commit, terminating relaible broadcast

# DepSys - Distributed Systems Theory - 5 Consensus

# DepSys - Distributed Systems Theory - 6 Paxos
* Duelling Proposers
* Practical Challenges: Failure detection needs to be implemented seperately, IO complexity, consensus on single values only

# DepSys - Fault Tolerant Distributed Systems - 1 Recap
* timing assumptions: synchronous or asynchronous

# DepSys - Fault Tolerant Distributed Systems - 2 Consistency Models
* Data-Centric Consistency
	* assume no explicit synchronization operations
* Strict Consistency: Any read returns the most recent write
* Linearizable / Atomic Consistency

# DepSys - Fault Tolerant Distributed Systems - 3 Client-Centric Consistency Models
* Causal Consistency

# DepSys - Fault Tolerant Distributed Systems - 4 Trade-Offs
* Lessons form giant-scale services: use symmetry, harvest and yield as metrics, focus on MTTR
* CAP Theorem

# DepSys - Fault Tolerant Distributed Systems - 5 PACELC
* trade off availability and consistency
* Consistency vs Availability

* Fault Tolerance vs Real Time
	* for FT you need to reorder actions
	* Concurrency increases efficiency but makes realtime harder

# DepSys - Fault Tolerant Distributed Systems - 6 Replication
* Logical objects implemented by multiple physical copies: replicas
* replication transperency: clients unaware of the existence ...

## Replication Protocols
* Request, Server Coordination, Execution, Agreement Coordination, Response

* State Machine Replication (Active)
* Primary/Backup Replication (Passiv)
	* clients send requests to primary replica

* eager vs lazy replication approach