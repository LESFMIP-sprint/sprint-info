## Using the Dask gateway

### What is Dask?

[Dask](https://docs.dask.org/) is a distributed computing framework for Python. It allows operations working on large datasets to be split across multiple computers (or multiple cores on the same computer).

JASMIN offers a Dask gateway that allows jobs to run on up to 16 CPU cores on the Lotus cluster. This can be a convienient way to overcome the processor and memory limitations of the JASMIN notebook service, while still using that service to write and run your code.

### Requesting Access to the Dask Cluster

Before using the Dask Cluster on JASMIN you must add it to your services. Please visit the [additional services](https://accounts.jasmin.ac.uk/services/additional_services/dask/) page on the JASMIN accounts portal
This will need approval from the JASMIN staff and won't happen instantly.

### Configuring your Dask environment

There are some extra packages that aren't in the main CANARI environment that you'll need to run Dask. We've added these to another environment in the group workspace called dask-env.

* To make the Dask enviroment visible to Jupyter Lab, in a terminal on the notebook service run: `mamba run -p /gws/smf/j04/canari/dask-env python -m ipykernel install --user --name CANARI-dask`.
* After about one minute a new icon called "CANARI-dask" should appear in the Jupyter launcher.
* If you have existing Dask code then see the [JASMIN documentation](https://github.com/cedadev/jasmin-daskgateway) for an example of how to configure it to use the Dask gateway or see the examples below. 

### Running the examples

There are two dask examples in the tutorials git repository. If you cloned the repository before these were added (end of March 6th) then you'll need to run a git pull operation to bring in the latest changes.
In the files view in Jupyter Lab go to your copy of tutorials repository, click on the Git menu and choose "Pull from Remote". Or you can navigate to this directory in the terminal and type the command `git pull`.

Two example files called `dask-example1.ipynb` and `dask-example2.ipynb` should appear. Open these, ensure they are using the CANARI-dask kernel and launch them. 
The first example demonstrates the Dask Delayed feature where calculations are not executed until their result is requested. 
The second example shows the futures feature where tasks are executed immediately, but anything wanting to access to the result will be forced to wait until the calculation is complete.

### Accessing the Dask gateway from the sci servers
You will need to generate a token for accessing the Dask gateway and place this in `~/.config/dask/gateway.yaml`. See the [JASMIN Dask documentation](https://help.jasmin.ac.uk/docs/interactive-computing/dask-gateway/#elsewhere-on-jasmin) for details on how generate a token and the format of the config file.

