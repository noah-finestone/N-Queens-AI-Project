# N-Queens
My solution to the n-queens optimization problem.

## Solution description
Solved the N-Queens constraint-satisfaction problem using a Local Search method.

My solution to the n-queens problem uses the hill-climbing optimization technique. This technique starts at a randomly generated state (board in our case) and improves from that initial state by means of what is called an "evaluation function". This function calculates the number of collisions between all queens within the boards current state. This technique attempts to make changes that only improve out current state, such that the number of collisions gets closer to 0 and never increases. Thus, hill-climbing can only advance in its algorithm if there is a better solution in the neighboring space - a lower number of collisions. This means it can get stuck at local optimum points or states and to solve this I use random-restart hill-climbing. If the board cannot advance more and it's not a global optimum, then I create a new random board state and restart the algorithm from there.

## Largest board size
I managed to solve the n-queens problem with a board of size n=30, higher board sizes were taking too long. Cth entry having value R means the queen in col C is in column R. (e.g., a solution for N=4 is [2, 0, 3, 1]).

![image](https://user-images.githubusercontent.com/67278226/231536979-63a78833-3685-497e-86f3-094f4070bf53.png)

## Run-time complexity of my method, as a function of N
The run time complexity of the hill-climbing technique is NP-complete such that its neither complete nor optimal but with random-restart, it depends on the number of restarts. So, with random-restart the time-complexity will be at worst O(n) - going through all the local peaks and at best it can be O(log n).

## How I overcame local optimas
Most of my solutions hit a local optimum as can be shown in my code where I print the number of local mins hit. To solve this, as stated before I use random-restart and generate a new random board state and run the algorithm again from this new state. I do this repeatedly until a board state with zero number of collisions is found.
