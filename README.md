Problem Statement
      
You are researching some new anti-viral drugs, and wish to determine the optimal way to apply the medicine in a tissue sample, so that the effects of the virus are minimized.



Initially, you are given the layout of the slide in vector <string> slide as a 2D array of cells, where each cell can be clean ('C'), dead ('X'), or infected with the virus ('V'). You are also given other parameters. int medStrength indicates the strength of the medication when it is first injected in a single cell. int killTime describes the number of units of time between a cell becoming infected and a cell dying. When a cell dies, the virus may spread to any of the four directly adjacent cells. Lastly, double spreadProb indicates the probability of each surrounding cell becoming infected. Note that the virus spread has no effect on cells that are already infected, already dead, or have a sufficient concentration of medicine.



Your code should call one of three methods during each unit of time to indicate what it would like to do:

addMed: Applies medication to one given cell on the slide. This increases the concentration of the medication in that cell by medStrength. Cell coordinates x and y are 0-based, and must be within the limits of the slide. Adding medication takes one unit of time.
observe: Returns the current layout of the cells on the slide, in the same format as at the start of the simulation. This will show the progression of the virus since the start. Note that this does not allow observation of the diffusion of the medication. Making the observation takes one unit of time, at the end of which the state of the slide will change and might differ from the observation.
waitTime: Lets units of time pass without taking any specific action (units must be between 1 and the number of units of time remaining before reaching the maximum simulation time)


As each unit of time passes, several things will happen:

Medication is applied, or an observation is made, if applicable.
Any viral-infected cells with a medication concentration of at least 1.0 become clean cells.
Any viral-infected cells that have been infected for killTime die, possibly spreading the virus to any of the four adjacent cells.
Medication diffuses between adjacent cells. The amount of diffusion is equal to 20% the difference in concentration between the two cells.


The simulation will run for at most 10000 units of time. Your solution is not allowed to perform actions after that time. After your solution returns, the simulation will continue to run until there are no longer any viral-infected cells remaining, or until 10000 units of time have elapsed from the start. The value returned from runSim() will be ignored.



If your method throws any errors, or calls addMed() or waitTime() with invalid parameters, or makes calls in excess of the maximum units of time, you will score a -1 for that test case.



Your raw score for a test case will be (HEALTHY_CELLS_REMAIN - MEDICINE_APPLICTIONS * 0.5) / SIM_TIME.

SIM_TIME is the total time it takes until all viruses are gone or MAX_TIME is reached. Any raw score less than 0 (except for an error as already described) will be treated as 0.



Your combined score for all test cases will be equal to the sum of (YOURS / BEST), scaled to 1,000,000. Thus, a combined score of 1,000,000 implies a solution that has the current best score on all test cases.