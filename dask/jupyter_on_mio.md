### -1. BIG WARNING

This creates a jupyter notebook server on Mio that you can access from your local machine. **BE CAREFUL, THE NOTEBOOK INSTANCE CREATED IS RUNNING ON THE MIO HEAD NODE AND THEREFORE CAN CRASH IF ABUSED AND MAKE LOTS OF PEOPLE VERY ANGRY**. Use Dask to dsitribute your computations to multiple nodes using the SLURM scheduler!

### 0. Connect to the Mines network via VPN (if not on campus)

https://its.mines.edu/software-title/vpn/ for more info.

### 1. Start Jupyter on Mio

On your local machine, open a terminal and input the commands

    ssh USERNAME@mio.mines.edu
    jupyter lab
   
This should start a Jupyter lab instance on Mio, and output an address that looks like the following:

    http://localhost:8888/?token=TOKEN
    
Note the port (8888) that the notebook is started on, we will use this in the next step.

### 2. Bind your ports

In a new terminal on your local machine, input the command:

    ssh USERNAME@mio.mines.edu -L8888:localhost:8888 
    
If you are using Dask and want to access the /status page on http://localhost:8787/status, add the following to the above command:

    -L8787:localhost:8787

### 3. Open a local browser

Simply open a web browser on your local machine and navigate to http://localhost:8888/?token=TOKEN (the URL output in step 1). The notebook will run on Mio, but you'll be able to see the output on your local machine's web browser! **BE CAREFUL, THE NOTEBOOK INSTANCE IS RUNNING ON THE HEAD NODE AND THEREFORE CAN CRASH** (making a lot of people upset), so if you're doing heavy processing you should utilize Dask to distribute your computations to the compute nodes.

If you're using Dask, you can also navigate to http://localhost:8787/status to see the status page.
