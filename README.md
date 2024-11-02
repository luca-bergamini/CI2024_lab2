# CI2024_lab2

In this laboratory we are going to use different algorithms to resolve the **TSP** (Travelling Salesman Problem). I implemented four different solutions:
- **Greedy Algorithm**: starting from an empty path, the algorithm fills the path with the closest next city;
- **Inverse Crossover**: is going to select a subsequence, from the current path or from one random path selected in the population, and then reverses it. It's an easy one but not necessarly maintain subsequences of nearby cities. It is not really efficient for TSP, in fact there is no improvement compared to Greedy Algorithm;
- **Order Crossover**: is going to select a subsequence, from the current path or from one random path selected in the population, preserving it's order. It's known to maintain optimized subsequence (without reversing it), that is really important to converge towards optimal solutions in the TSP;
- **Simulated Annealing**: starting from a random path, at each iteration it explores new paths and accepts them based on a probability that depends on the distance difference and the temperature. Lower temperatures and slower cooling (parameter used to change the temperature) increase the probability of finding good solutions, but make the algorithm slower.

## Results

Using as parameters:
- **MAX_GENERATIONS** = 5_000 (for Italy, Russia and Vanuatu) or 2_000 (for China and US)
- **POPULATION_SIZE** = 10
- **RATE** = 0.5
- **MUT_RATE** = 0.1
- **temperature** = 100
- **cooling_factor** = 0.99

### Greedy Algorithm

| CITY | STEPS | LENGTH |
| :- | :- | :- |
| China | 726 | 63962.92km
| Italy | 46 | 4436.03km
| Russia | 167 | 42334.16km
| US | 326 | 48050.03km
| Vanuatu | 8 | 1475.53km

### Inverse Crossover

| CITY | STEPS | LENGTH |
| :- | :- | :- |
| China | 726 | 63962.92km
| Italy | 46 | 4436.03km
| Russia | 167 | 42334.16km
| US | 326 | 48050.03km
| Vanuatu | 8 | 1345.54km

### Order Crossover

| CITY | STEPS | LENGTH |
| :- | :- | :- |
| China | 726 | 63419.11km
| Italy | 46 | 4361.22km
| Russia | 167 | 41043.37km
| US | 326 | 46334.00km
| Vanuatu | 8 | 1345.54km

### Simulated Annealing

| CITY | STEPS | LENGTH |
| :- | :- | :- |
| China | 726 | 54637.09km
| Italy | 46 | 4172.76km
| Russia | 167 | 33119.08km
| US | 326 | 40813.50km
| Vanuatu | 8 | 1345.54km

## Conclusion

We can conclude that the Simulated Annealing achieves better results in comparison with the other algorithms, for it's ability to avoid local minimum, that is a common problem for greedy, inverse and order crossover approach. In fact the Simulated Annealing algorithm has a probability of accepting worse solutions, allowing to search for real optimum and not getting stuck in a local optimum. 

Order Crossover works better than Inverse Crossover with larger number of cities because it maintain optimized subsequence, instead the Inverse Crossover reversing the order of the subsequence doesn't always maintain the optimal subsequence. On the other hand, working with smaller number of cities Order and Inverse Crossover and Simulated Annealing have a similar behavior.
