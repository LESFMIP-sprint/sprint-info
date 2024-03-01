## Tutorial 3 - Creating and sharing your own conda/mamba environment

### Why create your own environment?

The provided environment (located in /gws/smf/j04/canari/conda-env) contains many packages you are likely to need, but doesn't contain everything. As this is a shared environment we can't allow everyone to install new packages into it. If you need extra packages you will have to create your own environment.

### Creating an environment from the JASMIN Jupyter Notebook Service

It is assumed you have cloned the tutorials Github repository into a directory called tutorials, if you haven't see the "Getting the CANARI example code" section of tutorial 2 (Configuring and Using the JASMIN Notebooks Service). 

* In a terminal on the notebook service (note: this will not work on a Sci server) run the command `mamba env create -n canari -f ~/tutorials/environment.yml`. We are using the command `mamba` instead of `conda`. Mamba is a replacement for conda that can resolve the dependencies for an enviroment much faster. 
* This will take about 10 minutes to execute. After it is complete, verify it exists by running: `mamba env list`, you should see something similar to the following:
```
# conda environments:
#
                         /gws/smf/j04/canari/conda-env
canari                   /home/users/colinsau/.conda/envs/canari
```
* To make the enviroment visible to Jupyter Lab run ("CANARI-mine" is the name it will show in the Jupyter Launcher, feel free to change this): `mamba run -n canari python -m ipykernel install --user --name CANARI-mine`.
* After about one minute a new icon called "CANARI-mine" should apear in the Jupyter launcher.

### Adding extra packages to your environment
#### Installing extra packages with Mamba
We can install extra packages in our mamba/conda enviroment by using the `mamba install` command from a terminal inside the JASMIN notebook service. We need to specify the name of our enviroment with the `-n` option. If for example we wanted to install plotnine (which creates R ggplot2 style plots in Python) then we could install it by typing: 

`mamba install -n canari plotnine`

#### Installing extra packages with Pip
Sometimes packages aren't available via Mamba/Conda but are available via Python's pip package manager. Always try to install via Mamba in the first instance though. To install plotnine using pip run the command:

`mamba run -n canari pip install plotnine` 

If you already installed plotnine using mamba then this will detect the installation and refuse to install it again. 

### Sharing your enviroment
Now you've added more packages to your enviroment you might want to share your enviroment with somebody else (or yourself on a different computer). Mamba/Conda allows us to export a list of all packages installed in an enviroment with the `mamba env export` command. An example use of this command is:

`mamba env export -n canari --from-history -f new_environment.yml`

* As with other Mamba commands this takes a `-n` parameter for the name of the enviroment we're exporting.
* The option `--from-history` this means that the export will reflect the package versions we specified, for example we might have requested Python version 3.10.12 instead of the exact version we got which might have been something like version 3.10.2=hd12c33a_0_cpython. These overly precise version numbers can cause problems when trying to replicate the enviroment on another computer, especially if it runs a different operating system.
* We can specify an output file with the `-f` parameter, if this isn't specified then the environment data is displayed on screen.
* The resulting file (new_enviroment.yml) can now be shared with somebody else or added to a git repository.
* To install a new enviroment using this file run the command `mamba env create -n canari-new -f new_enviroment.yml`. This will create a new enviorment called "canari-new" from the file new_enviroment.yml that we just exported.
