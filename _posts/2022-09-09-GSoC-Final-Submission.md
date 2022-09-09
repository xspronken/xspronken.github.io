# Final Submission

## How to find my project files and folders 
This project was conducted in the qutip-benchmark [repository](https://github.com/qutip/qutip-benchmark) which had been abandoned for 8 years.
Rather than updating the existing code I chose to start a new project from scratch, however the pre-existing files and folders are still present in the repository.  
#### Files and folders that existed before the project and were not modified:
- [benchmark](https://github.com/qutip/qutip-benchmark/tree/master/pre_GSoC_benchmark)
- [continuous-benchmark](https://github.com/qutip/qutip-benchmark/tree/master/pre_GSoC_continuous-benchmark)
- [.gitignore](https://github.com/qutip/qutip-benchmark/blob/master/.gitignore)

#### Files that existed before the project that I modified:
- [LICENSE](https://github.com/qutip/qutip-benchmark/blob/master/LICENSE), modified in this [commit](https://github.com/qutip/qutip-benchmark/commit/dd1cff5ef64ebb0d759fe3b11ac14836bef6281c#diff-c693279643b8cd5d248172d9c22cb7cf4ed163a3c98c8a3f69c2717edd3eacb7)

#### Files and folders that did not exist and were created during the project:
- [benchmarks](https://github.com/qutip/qutip-benchmark/tree/master/benchmarks)
- [website](https://github.com/qutip/qutip-benchmark/tree/master/website)
- [.github](https://github.com/qutip/qutip-benchmark/tree/master/.github)
- [README.md](https://github.com/qutip/qutip-benchmark/blob/master/README.md) 

## Project use cases
#### 1. Running automatic nightly benchmarks in git actions and publishing the results on [qutip.org/qutip-benchmark](https://qutip.org/qutip-benchmark/)

This job is performed by the [nightly_benchmarks](https://github.com/qutip/qutip-benchmark/blob/master/.github/workflows/nightly_benchmarks.yml) workflow.
This workflow first downloads the latest version of qutip and the required dependencies into the VM. After this all the previous benchmark result files are downloaded from an S3
bucket, a new benchmark is run using [benchmarks/benchmarks.py](https://github.com/qutip/qutip-benchmark/blob/master/benchmarks/benchmarks.py) and the new result file is added to the S3 bucket.
The updated benchmark results are then used to produce all the plots with [benchmarks/view_benchmarks.py](https://github.com/qutip/qutip-benchmark/blob/master/benchmarks/view_benchmarks.py).
The plot png files that result from this are placed in the [website](https://github.com/qutip/qutip-benchmark/tree/master/website) folder under images/plots.
Finally the website folder is published to the [gh-pages](https://github.com/qutip/qutip-benchmark/tree/gh-pages) branch which hosts the [qutip-benchmark](https://qutip.org/qutip-benchmark/) section of [qutip.org](https://qutip.org/)

#### 2. Running and plotting benchmarks locally as a user
Information about this can be found in the [README.md](https://github.com/qutip/qutip-benchmark/blob/master/README.md) and [tutorial.md](https://github.com/qutip/qutip-benchmark/blob/master/tutorial.md) files at the root of the repo.


## TODO
The project is entirely functional, however some things remain to be done:
- Automatic testing of the plotting and sorting functions in [view_utilities.py](https://github.com/qutip/qutip-benchmark/blob/master/benchmarks/view_utilities.py) to facilitate later updates of these functions and uncover potential bugs that have not yet been found.
- Adding more filtering and plotting options to the previously mentionned functions and imporving their user-friendliness.
- Adding more operations and solvers to the benchmarking suite for local users. As the currently available benchmarks are tailored to be performed nightly and published on the website.  
