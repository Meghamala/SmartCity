# SmartCity Project 
This deals with solving growing traffic congestion issues using dynamic allocation of lights based on waiting time, rate of flow of cars as a measure of congestion using basic round robin method of scheduling

## Problem Statement
Designing the scheduling of the traffic light such that it dynamically assigns the proportionate duration of green time based on the current congestion of the respective lanes.

## Design of the algorithm

>> Approach to the Algorithm

For each cycle,
Take the picture of the respective line and find the number of the cars
Calculate the ratio of congestion between the lanes
Choose a suitable K(Restricted to the number of vehicle in the lanes)

The so obtained green duration is said to be initial green
                        initialGreen  =  numOfCars( i )/(totalNumCars) * K

The above parameter can also be called static parameter (Doesn’t considers the inflow to the lane )
To add the factor of dynamism we have decided to consider the inflow parameter, which counts the number of the cars that inflowed to a particular lane when it was waiting for its chance to be green, i.e (inflow/waitTime)

Since this dynamic addition of this parameter to the previous one gives us the final green duration of a particular line
                     dynamicParameter  = inflow( i )/sum(inflow) * waittime
                     
The above parameter adds the additional green duration in a proportionate way as it considers the inflow of the other lanes in the denominator ( example, 3 lines A B C
           If inflow of C > B quantum allocated to B will be less as it includes C’s and A’s inflow which is  inversely  proportional to the B’s dynamic parameter(includes in the denominator))

Final equation would be
   G = Initialgreen + dynamicParameter
   G = (numberofCarLane( i )/totalNumberOfCars)*k + ((inflow( i )/Sum(inflow))*waitingTime( i))


 
