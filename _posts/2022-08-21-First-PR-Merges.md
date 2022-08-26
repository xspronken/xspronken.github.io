## Week 8 and 9 Merging the first PRs

During the first week the first three PRs being merged. The first one to be completed contained the operation benchmarks.
The operation bencchmarks required some changes before being merged such as the creating the matrices using qutip.rand_herm rather than using numpy methods.
The conversion of the matrices to different datatypes also had to be changed since rand_herm outputs q_objects rather than a numpy array that was produced initially
This PR also conatined the addition of a license and a readme for the repo.
Second to be merged was the first part of the workflow that runs the benchmarks, allowing us to make sure the benchmarks in the next PRs work properly on commit.
The workflow does not contain the part that uploadds the benchmarks to an S3 bucket yet.
The QobjEvo benchmarks were also merged with minor changes.

The second week was spent on the plotting and solver PRs, that haven´t been merged yet. The plotting PR required major changes as the plot functions initially made were tailored to each benchmark, thus requiring a new plotting function for each type of plot.
The most part of this week was spent creating functions to first prepare the data and then plot the prepared data. These funtions however still contained hardcoded information that could be extracted from the json files containing the benchmarks.
The data preparation function also needs to be separated further, resulting in a function to extract and clean the data from the json file, a fucntion to the data by operation and a function to sort the data using the benchmark parameters.
