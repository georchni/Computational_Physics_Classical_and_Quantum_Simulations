# Computational Physics with Python
This is a collection of some computational physics problems that were programmed with python during the Master's level course Computational Physics II offered be the TU Munich.
The context of the course was the study of classical and quantum mechanics simulations.
The following algorithms can be found here:

### 1) Quantum Wave Function via Path Integrals Formulation: Metropolis Algorithm 

The Metropolis algorithm performs a special kind of Monte Carlo integration. It works as follows:

i. We choose values for the x_i first. Either choose a cold start (set all the x_i to zero) or a warm start
(choose random values for all the x_i).

ii. The next step is to thermalize the configuration. The point of this step is to get rid of unphysical
initial conditions. In order to thermalize the configuration we perform the following update step
described in item (c) for 5 to 10 times the number of data samples that we assume to be correlated
Ncor.

iii. Update the configuration:
1. Choose a uniform random number r in [-epsilon,epsilon].
2. Change a random x_i by r.
3. Calculate the difference in action between the old and the new configuration.
4. If the action is decreased, keep the new configuration.
5. If the action is not decreased, keep the new configuration with probability exp(􀀀(Snew 􀀀 Sold)),
otherwise restore the old configuration.

iv. Calculate a sample of N_cf configurations. There are two equivalent ways to do this:

- Perform steps (a) - (c) and take the last configuration for your sample, repeat this N_cf times.

- Perform steps (a) - (c) only once and take N_cf configurations after the thermalization.

 The second method is obviously much faster. However, care has to be taken in order to obtain
uncorrelated configurations. This can be done by performing N_cor update steps in between each
obtained configuration.

v. We are interested in the transition matrix element, which translates to the calculation of the Green’s
function abd the calculation of energy difference.

vi. Then we determine the ground state of the wave function.

Remarks:

Some modification for improvement: 

- Replacement of the derivative in the lattice action by a derivative of higher order for improved action.
- The derivation of an improved numerical derivative by means of Taylor Series, i.e. showing that the -1/12 factor cancels the O(a^2) error produced by the higher order derivative.
-The parameter tuning can result into different and ameliorated solutions.

### 2) Ising Model

Implementation of the Metropolis algorithm to simulate the 1D Ising chain model: N magnetic dipoles fixed on a chain.

i. Use a warm start configuration (all spins are set randomly) as the initial condition. Set the number of dipoles to N = 20.

ii. Pick one dipole randomly and flip its spin to create the new trial configuration. Calculate the energy of both old and the trial configuration.

iii. Calculate the relative probability for the trial configuration for a temperature of kT = 0.1.

iv. Check the condition for accepting relative probability.

v. Continue the calculations for 10N and investigate the alignment of the spins and the results given different parameters. 

vi. Use 100N steps and temperature of kT = 0.01, kT = 0.1, kT = 1.

vii. Try also a cold start where initial spins are aligned (in this case you either have to do lots of steps
or increase kT)

viii. Extend the model in 2D model.

### 3) Monte Carlo of Evolution

 The algorithm is the following:

i. N species are arranged in 1D line.

ii. Assign a random barrier Bi in the range [0; 1] to each species.

iii. Mutate the species with the lowest barrier by assigning a new barrier Bn for this species and its
neighbouring species B_{n-1} and B_{n+1}.

iv. Repeat this mutation for each iteration.

v. The real time of the mutation is proportional to exp(B_n=T_car), were T_car is a characteristic time
scale (T_car = 0.01). 

vi. Produce similar plots to those printed in the article.

The results are compared with the following article, in which certain aspects of evolution are described with the help of a MC model:  P. Bak and K. Sneppen, Punctuated equilibrium and criticality in a simple model of evolution, Phys. Rev.
Lett. 71 (1993) 4083.
