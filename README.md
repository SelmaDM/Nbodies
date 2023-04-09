## N-Bodies problem:
### Evolution of a set of bodies that interact with each other.

Example in astrophysics: The motion of stars taking into account the forces of gravitation.

For each pair of stars, each applies to the other a force f where G is a constant, m1, m2 are the respective masses of the two stars, and x1, x2 their position vectors.

At each time step, we calculate the forces that apply to each star, then we update the data concerning it (position, velocity and acceleration).

The basic solution consists at each iteration in :
calculate, at each step, the forces experienced by each star from each of the other stars
to sum up all the forces suffered by each star
calculate, from the forces, the new positions, velocity and acceleration of each star on a given set of time steps (iterations).


### The sequential program is as follows:



```
for t in range(0, NB_STEPS)
	force = []
for i in range(0,N)
force.append((0,0)) # force[i]
for j in range(0, N)
force[i] = force[i] !+! interaction(data[i], data[j])

for i in range(0, N)
data[i] = update(data[i], force[i])
```


where data[i] is a data structure that includes the position, velocity and acceleration of star i, N is the number of starts, interaction(data[i],[j]) is a function that returns the force applied by star j to star i (this function reads data[i] and data[j] but does not modify them), and update(data[i],force[i]) is a function that computes the new position, velocity and acceleration of star i based on the force it experiences. It is assumed that only the process of rank 0 knows data and that the number of processes divides the number of stars. Be careful, to really implement this algorithm, more lines of code are needed to add the force pairs when updating force[i].

<img src="https://github.com/SelmaDM/Nbodies/blob/master/Temps%20exe%20vs.%20Param.png"/>









