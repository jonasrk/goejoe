[/FIT-2014-04-24-Interactive-Fabrication](/FIT-2014-04-24-Interactive-Fabrication)

[/FIT-2014-04-24-Interactive-Fabrication-condensed](/FIT-2014-04-24-Interactive-Fabrication-condensed)


# Future Interactive Technologies - Video - 2014_06_05 Science Intro, Debugging Raw Data, t-tests (Patrick) 1
## Science
* Science works by falsifiying statements
* If a study disagrees, you know that a law does not hold
* If a study agrees, you keep this as a woring hypothesis
* ... which means you are never positive!
* If we observe something, it supports a claim. not proove it.

## Hick's Law
* Could be true or false

## Mince Evers Video
* Vermutung: Im Kühlschrank ist noch Bier.
* In der Theologie werden Vermutungen nicht überprüft.
* Ein Theologe kann in 5 Minuten mehr behaupten als ein Wissenschaftler in seinem ganzen Leben wiederlegen kann
* In der Wissenschaft bleibt immer ein Restzweifel

## Why would you run studies in HCI?
* Studies in HCI can validate designs
* Sound of science is not "Heureka" but "That's odd"
* Death Ray: "mad scientist" are just mad engineers

## understanding touch
* what is the underlying assumption of all touch sensors?
	* contact area and center of the contact area?
	* assumption: the contact area is what your trying to indicate to
* touc input is inacurate
* new model: people are aiming with the center of ther fingernail
* people have now idea about the contact area
* The new model fits 10 times better
* touch sensor based on the old model can't be acurate
* new model will be a better model
* majority: engineer something, make measurements

## experiments
* experiments are questions to nature
* nature responds with data
* statistics are the tools to interpret the response


# Future Interactive Technologies - Video - 2014_06_05 Science Intro, Debugging Raw Data, t-tests (Patrick) 2
## what can go when processing study results?
* scientific dishonesty: mostly non-publishing of unfavored results

## human reaction time
* stay on same level, high at beginning, fluctuating?

## outliers
* how do you justify removing outliers
* created by other external factors
* it seems less likely that it just took the person long

## learning period
* remove it? it depends!
* if the study is about learning, keep it. elsehow, not.

## histogram
* see distribution better
* but you loose exact timing
* first look at a raw bar chart and then start aggregating

## what would histogram of human reaction time look like?
* infinite or finite to the left or right?
* right infinite, no upper bound
* not symmetric because bound on one side and no bound on other
* depending on how much repetitions you have irregularities can happen
 
## debugging results
* trad snapping anectode
	* programming bug led to unusual results

## summary
* look at raw data first
* learning or fatigue
* bugs in your apparatus
* side effect: by spending more time with your data you might notice something that can lead to your next idea


# Future Interactive Technologies - Video - 2014_06_10 t-tests, Stats Design Basics (Patrick)
## conditions
* how can we learn about underlying mechanisms?
* finding out something about the contents of a black box (can be directly observed?)

## stats
* mechanism of science

### significance
* result is unlikely to have occured by chance

### p-value
* probability that something observed is at least this unlikely to happen

### significance level
* test gives p-value lower than significance level, the null hypothesis is rejected

* Why 5% in HCI?
	* just a convention
* different e.g. with life-threatening effects

* you always try to observe is two mechanisms are identical or different

* means do play a role, but so does standard deviation

## t-test
### intro
* general tool to solve many issues
* many phenomena take place on a global scale and are not personally observable
* you need to understand global level things -> therefore understand stats
* tools are needed to understand the fate of mankind

### student's t-test
* implemented in Python, Excel, SPSS
* some packages first give t-value -> not today
* Why not Gosset's t-test? Not allowed at guiness company
* data has to be normal distributed
* for unknown standard deviation
* our reaction time data has to be transformed

### you make a new input device and what to show that it is as good as the mouse
* you can't show that something is the same
* if tests find significant difference you can't make any conclusions

#### classic engineering vs. scientist question
* very scientific analasys that doesn't really fit here

#### why does "my device is better with p < 0.0000001" not impress?
* we don't know how much better

## stats design basics
* compare new mouse design with old one - how to proceed with 24 participants?

### power of stats test
* paired test has greater power than unpaired
* one-tailed or two tailed?
	* new drug about hairloss? one-tailed or two-tailed?
	
## bonferroni correction
* 10 different devices: compare each with each other
* many misconecptions about repeated testing - bost of them can be fixed by bonferroni

## planned comparison
1. avoid sequence effects
2. counterbalancing
* avoid confounding

### latin square
* limitations? 


# Future Interactive Technologies - Video - 2014_06_12 Stats Bootcamp (Dominik, Alex) 1
## längliche französische Filmausschnite über ein Experiment
* elektrischer Stuhl
* what's the purpose of this experiment?
* person on the electric stool is just playing the shocks
* different conditions: participants in same room or different
* purpose was to find out how much voltage people put on the pupil
* 65% of the population goes up to 450 Volt
* after WW2 people wanted to find out what's wrong with people
* underlying theory: anyone can end up in a violent system using torture
* participant got 6$ - but most said they didn't do it for the money
* people explaned they were just following orders
* is this science/engineering?

* why is this science?
* there was a general observation and they tried to explain it
* good science: you have a model, you make predictions, you run experiments

## Dominik Stats Bootcamp
* make the three participants file one file
* independent variables in study?
* gesture flat or tip, number of fingers, set size
* what were the hypothesis?
* combined sets had a longer reaction time
* flat takes longer because its more complicated
* how will these variables related to each other?
* should we expect interactions?
* main effects vs. interactions

## SPSS tutorial
* variables should be 7 chars or sharter
* e.g. time of first contact ... 
* sometimes numbers are just names

### is numbers of fingers ordinal?
* yes, because more fingers is more than fewer fingers ... but their order depends

* data is plotted as scatter plot
* cheat sheed will be handed out

### is there something interesting in the scatterplot?
* is milliseconds scale? -> fucked up scale becuase there are zeros which is impossible
* overall the data looks plausible
* long time might mean that a participant did not take the experiment serious
* use SPSS to filter out
* plot boxchart
* SPSS generates protocol and that has to be saved and submitted for assignment


# Future Interactive Technologies - Video - 2014_06_12 Stats Bootcamp (Dominik, Alex) 2
## SPSS Besprechung barchart as expected?
* surprising or expected?
* surprising: 19 out of 20 did something wrong

### how to resolve situation?
* take this person out?
* fix bug and rerun?
* if lots of data is missing you have to rerun experiments
* drop one gesture?
* doing stats is not about dropping stuff on paper
* we assume an debug and rerun
* we use time of first contact time in this case

* data still makes sense on the scatterplot

* how does this effect the hypothesis?
* next: histogram of the data to see if it is normal distributed
* distribution per patrick

### what do two peaks mean?
* two different participants

* next histogram and variables

* logarithm data

* filter out outliers

* tadaa: hypothesis is not working out here
* long green bars - we expected short green bars


# Future Interactive Technologies - Video - 2014_06_12 Stats Bootcamp II (Dominik, Alex, Patrick) 1
## recap
* last time we wanted to analyze the data from students hicks law study
* data was screwed, usually we would have debugged the data. In this case we made a compromise to get through the whole process.
* What was the hypothesis? More finger take more than less fingers. Flat takes longer that tip.
* Bar charts looked as expected

## next: statistical tests
* logarithm time
* outlier removal (analyze -> descriptive tests)
* remove all outliers that are more than two standard deviations away
* Next: Analysis of Variances (kind of generalized t-test)
* -> data -> aggregate : create a new dataset

* use people to approximate population
* if your sample is not good you do not catch a lot
* you need a decent size sample to get representative data
* Hick's law is so basic that it should be the same for everyone
* variation across participants valuable

* unrelated: people should do a startup that should replace SPSS

* now there are only three rows that tell you everything about the three participants

## Run the ANOVA
* generalized linear model -> ...
* IV short for independent variable
* EXAM: define independent variable

### IVs
* flat or tip
* numbers
* ?

* We need to make sure to have the right order of the IVs

### What does the table mean?
* The chance for this or something more extreme to happen was 25%

# Future Interactive Technologies - Video - 2014_06_12 Stats Bootcamp II (Dominik, Alex, Patrick) 2
## Continue Testing

## Line chart
* does the line chart correspond to the former bar chart

* before you run the thing ask your self what you expect to see
* in the example a significant main effect was found
* write down f and p values

* End of Dominiks SPSS Tut

## what would be a better way to handle SPSS?

## task time, but what about error?
* task time and error, if both is higher, which is better?

### how can you make them comparable?
* utility theory: come up with a formula
* you can push people to do roughly around the same level of error
* less common: keep task time constant
* sample whole space

### how many participants does a study need?
* small effect: 783, medium: 85, large: 28

# Future Interactive Technologies - Video - 2014_06_19 Jack Lindsay
## Optimizing Agriculture
* start-up trying to improve farming
* optimize water use (4/5 go to irrigation)
* famers might spend 200 000$ on water
* fertilizer is even more expensive
* power consumption

* large farms produces 95%

## Let's make some data
* What's worth measuring?
* Rainfall, where and how much

* e.g. california had droughts
* soil chemistry: not real time and only for a single point
* drainage

* wind patterns
* plant stress

## what can we do with it?
* build a bunch of cheap sensors?
* drones start to happen

## Data analysis
* Geophysics
* Weather prediction
* plant biology
* uncertainty in best practices
* -> A Market for Algorithmus will evolve

## User Interface
* understand farmers perspective
* demonstrating uncertainty -> greyscale the picture of what to to where how much
* managing liability -> who is responsible for failures?
* maintaining control -> how to recommend data
* managing the load on the grid -> get rid of peaks

## end of monoculture
* easy, but terrible for the world

## Thoughts?
* Where are the users in east germany? -> a lot of corporate control. but there is still be people running it.
* how many people? -> hierarchy with only a few people
* european union beurocracy? -> 
* sample of the engineering? -> picture of integrated solid weather station
	* foot high, rein sensor with piezo, solar panel
	* process data in realtime? yes
	* rein sensor is very easy on processing
* how is data transferred? -> cell network similar to cellsensors. if you have enough, you can create a mesh
* sunlight not accurate for evaporation
* how much does it bend for sensing wind? tricky problem. you need material in the realm of infinite fatigue
* pricepoint? 200$ for one. km^2 needs in between 1-3 to 1 per acre
* ice wine is super hard and risky
* crossing the chasm book: you need an early adopter
* could the system suggest what to plant? yes.