## Week 3 and 4: Automating benchmark display
GIThub actions reliability:

Github actions was found to be reliable enough to run a nightly benchmark of qutip's operations, as long as the CPU allocated to the VM that is created is recorded. Since the benchmarks performed on the same cpu are consistent with each other. 
So far 5 CPUs have been used in the benchmarks, 2 Xeon E5s at 2,30GHz and 2,40GHz and 3 Xeon PLatinums runnning at 2,60 at 2,80 GHz. The Xeon PLatinums offer the more consistent benchmarks both across workflow runs and within a benchmark. The standard deviation recorded by pytest-benchmark on completion of each benchmark being much lowerfor these CPUs. 

Benchmark recording and visualization:

1. Storing the benchmark data:
Every time the benchmarks a run a JSon file is created in which all the data of that run is recorded and saved. In order to avoid a growing database of benchmarks stored in the github repository, the json file is uploaded to an S3 bucket.

2. Retrieving the data and plotting the graphs
The benchmark JSon files in the S3 bucket are then all downloaded to be used to graph the benchmark history. 

3. Exporting the graphs to qutip.org
A gh-pages branch was created in the qutip-benchmark repository allowing the benchmark data graphs to be accessed via qutip.org/qutip-benchmarks.
In order to update the benchmark plots, the contents of the gh-pages branch are pulled and the folder containing the images is replaced with the newly created plot images. The filenames of the plots are kept consistent so no other modification to the website has to be made. The entire website directory is then pushed back to gh-pages using ghp-import:
```
  ghp-import -m "Automatic push by ghp-import" -f -p -o -r origin -b gh-pages qutip-benchmark
``` 
The push is a force push with  no history recorded in order to avoid the git commit history to grow too much since the updates will be performed every night. Since the push replaces the entire contents of the gh-pages branch the entire website has to be pulled and pushed back to the gh-pages branch each time.

