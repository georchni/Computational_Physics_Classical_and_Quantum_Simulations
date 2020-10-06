# Computational Physics with Python
This is a collection of some computational physics problems that were programmed with python during the Master's level course Computational Physics II offered be the TU Munich.
The context of the course was the study of classical and quantum mechanics simulations.
The following algorithms can be found here:

### 1) Quantum Wave Function via Path Integrals Formulation: Metropolis Algorithm 

The Metropolis algorithm performs a special kind of Monte Carlo integration. It works as follows:

a) We choose values for the xi first. Either choose a cold start (set all the x_i to zero) or a warm start
(choose random values for all the x_i).

(b) The next step is to thermalize the configuration. The point of this step is to get rid of unphysical
initial conditions. In order to thermalize the configuration we perform the following update step
described in item (c) for 5 to 10 times the number of data samples that we assume to be correlated
Ncor.

(c) Update the configuration:
1. Choose an uniform random number r in [-epsilon,epsilon].
2. Change a random x_i by r.
3. Calculate the difference in action between the old and the new configuration.
4. If the action is decreased, keep the new configuration.
5. If the action is not decreased, keep the new configuration with probability exp(􀀀(Snew 􀀀 Sold)),
otherwise restore the old configuration.

(d) Now we calculate a sample of Ncf configurations. There are two equivalent ways to do this:

- Perform steps (a) - (c) and take the last configuration for your sample, repeat this Ncf times.

- Perform steps (a) - (c) only once and take Ncf configurations after the thermalization.

 The second method is obviously much faster. However, care has to be taken in order to obtain
uncorrelated configurations. This can be done by performing Ncor update steps in between each
obtained configuration.

(e) We are interested in the transition matrix element, which translates to the calculation of the Green’s
function abd the calculation of energy difference.

(f) Then we determine the ground state of the wave function.

Remarks:

Some modification for improvement: 

- Replacement of the derivative in the lattice action by a derivative of higher order for improved action.
- The derivation of an improved numerical derivative by means of Taylor Series, i.e. showing that the -1/12 factor cancels the O(a^2) error produced by the higher order derivative.
-The parameter tuning can result into different and ameliorated solutions.
