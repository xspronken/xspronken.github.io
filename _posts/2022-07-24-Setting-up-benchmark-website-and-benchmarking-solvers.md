## Week 5 and 6 Finishing up automation and starting to benchmark solvers


These two weeks were spent setting up the website that would hold the benchmarks, it can be found at [qutip.org/qutip-benchmark](https://qutip.org/qutip-benchmark/).
The website was initially created with a set of filters that would allow the user to sort through all the different plots for the benchmarking of an operation. This idea was dropped in favor of using less plots which contained more information. This meant showing 3 of the 5 available CPUs on the same graph as well as all four datalayers as opposed to a seperate plot for each datalayer and CPU. The 3 CPus s chosen were the Xeon Platinum series as they were the most used and provided the most consistent data.


Having finished this the benchmarking and plotting automation is completed, which alllows me to focus on benchmarking solvers and plugging them in to the existing structure.

The first solver to be benchmarked is mesolve (note that all solvers and operations benchmarked are from the dev.major branch of qutip, which contains the unreleased V5). 
Benchmarking solvers is somewhat more complex than operations. Since operations are effectively matrix operations such as matrix multiplication, creating two random dense or sparse matrices and timing their multiplication was enough.
Solvers on the other hand are designed to simulate the behaviour of quantum systems, which can be represented by sparse or dense matrices depending on the nature of the system.
Thus we have chosen to solve and benchmark 3 diffrent systems: A photon in a cavity and a Jaynes-Cummings model, which are sparse systems, and a system of qubits, which is more dense.
