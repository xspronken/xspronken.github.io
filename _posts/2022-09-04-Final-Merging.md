## Week 11 and 12: Finalising the project

These two weeks were spent on the merging the PRs that are required for the project to be published and up and running.

Firstly, the solver benchmarks were merged into the project after some minor changes to to fixture names and the size of the systems used for the benchmarking.
It was limited to 128x128 matrices, as the benchmarks would take too much time to complete, or, in the case of SteadyState, would use up too much ram.  
  
The major part of these two weeks was spent finalising the plotting PR. The functions were made as generalistic as possible, allowing the user to provide the required parameters to filter data and plot the right information.
The plotting comprises in 4 major usable functions.  
The first one extracts the data from the json files into a dataframe and deletes the columns that are not needed in the future functions.
Second the data is separated into one dataframe per operation type, with the possibility to filter out certain operations if the user does not wish to plot them.
After this the data is separated further using the fixture parameters such as size, matrix density or model in the case of solvers. The goal of this function is to have all the data required for the plots in separate dataframes.
This also offers the possibilty to filter out certain parameter vaules if the user does not wish to plot them. For example not showing the dense matrix benchmarks.
There is also the possibilty to set a parameter as line separator rather than plot separator, i.e. rather that plotting the different values for this particular parameter on different figures, they will appear on the same plot as different lines.
Finally the plotting function uses the data output from the previous function and plots the contents of each dataframe as its own figure. The user can choose which columns of the datafram ill serve as x_ axis and y_axis and whether these axes scale logarithmically or linearly.


Once the plotting was finalised and merged , we could also merge the final part of the workflows that publish the plotted benchmark results to the qutip [website](https://qutip.org/qutip-benchmark). This PR includes a workflow to perform benchmarks nightly and update the website with the new results, and a workflow to test all the benchmarks on a new pushes and commits.
The source files for the website were also stored in the repo so the workflow can publish them after adding the images files which contain the plots.

The last part of these weeks was spent finishing the documetation, this includes a Readme.md file which shows the user how to perform benchmarks and plot them, as well as a notebook tutorial with an example of data filtering and plotting using the plotting functions.

