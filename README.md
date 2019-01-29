# Genetic algorithm protein folding
This project was developed for a genetic algorithm course at the "Hochschule Darmstadt".

The input is a string of 0s and 1s. 
The goal is to fold the sequence optimizing the n4 neighbors of the 1s without an overlap in the chain.
All this happens on a 2D plain with 3 possible directions: straight, left, right.

## Possible settings

In the Main (`org.hda.gaf.Main`) there are several settings you can modify/comment in:
* Choose one of the genetic algorithms:
    * Time limited algorithm (e.g. generate for 20s, then stop) 
    * Generation limited algorithm (e.g. generate 100 generations, then stop)
* Selection algorithms:
    * Fitness proportional (Every individual has a chance to get chosen. A higher fitness results in a better chance to get chosen)
    * Tunier fitness proportional (Same as fitness proportional but pairing individuals in a tunier and choosing every turn)
    * Tunier best fitness (Pairing individuals in a tunier and choosing the one with the best fitness)
* Population amount: Individual amount per generation
* Mutate rate: 
    Percent of how many genes of the total population should be mutated after selection. 
    The mutation includes changing a left turn to either a straight, right or left turn.
    
    E.g. Having 100 genes per individual in a population with 10 individuals means we have a total of 1000 genes. 
    With a mutation rate of 2% a total 20 of the genes gets modified every generation.
* Crossover rate: 
    Percent of how many individuals in a population should do a crossover every generation.
    Using a simple one point crossover (splitting the gene chain anywhere and switching it with another partner in the population).
    
    E.g. Having a population of 100 individuals and a crossover rate of 20% means that 20 individuals crossover every generation.
 
* Print while generating:
    Activates a GUI displaying the currently best found protein and some stats. For better performance deactivate it.

## Other projects
The project was also implemented using different parallel computing technologies:

Java Multithreading: \
Using multiple java threads to share the workload.
Exchanging part of the generated population with other threads to allow for more variety. \
https://github.com/MPritsch/genetic-algorithm-protein-folding-multithread

MPJ Express: \
MPJ is a java implementation of MPI (Message Passing Interface).
It can be used to distribute the computing workload on a Cluster with multiple CPU's. 
Part of the generated population is shared with other MPJ processes to allow for more variety. \
https://github.com/MPritsch/genetic-algorithm-protein-folding-mpj