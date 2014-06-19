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