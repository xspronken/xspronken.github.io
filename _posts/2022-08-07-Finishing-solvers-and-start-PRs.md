## Week 7 and 8: Finshing solver benchmarking and Starting to set up PRs

The first of these two weeks was spent finishing the solver benchamrks, we first created the models that would be used to to benchmark, these were the photon cavity, the Jaynes-Cummings model, and a qubit spin chain.
The models were then used to benchmark qutipś master equation solver and monte-carlo solver. Follwing this the J-C and photon cavity models were used to benchmark the steadystate solver.

The second week was spent creating PRs to merch into the qutip-benchmarks repository. So far 2 PRs have been made and reviewed, they will most likely be merged thsi week. The 1st PR contains the script to run the benchmarks as well as the benchmarks for the Add and Matmul operations. The second PR contains the first part of the github workflow that can be used to run the benchmarks in git actions.
