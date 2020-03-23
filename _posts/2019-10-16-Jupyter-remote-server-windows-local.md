---
title: 'Running a Jupyter notebook from a ubuntu remote server'
datae: 2019-10-16
permalink: /posts/2019/10/Jupyter-Remote/
tags: 
    - Jupyter
    - Remote 
    - Windows10
---

This is a guide on how to connect Jupyter notebook from ubuntu remote server at local side. The system of local machine is windows10. The original blog is [here](https://ljvmiranda921.github.io/notebook/2018/01/31/running-a-jupyter-notebook/).

**Set-up:** Here, let’s define the local user and host as `localuser` and `localhost` respectively. Similarly, let’s define the remote user and remote host as `remoteuser` and `remotehost`. Needless to say, make sure that [Jupyter notebook and all its dependencies](http://jupyter.readthedocs.io/en/latest/install.html) are installed in both machines. Here’s a quick diagram of the whole process, I will discuss them one-by-one in the next section:

![overview](https://ljvmiranda921.github.io/assets/png/tuts/jupyternotebook.png)

1. Run Jupyter Notebook from remote machine

   ```
   xiaolin@imimo:jupyter notebook --no-browser --port=XXXX
   
   # Note: Change XXXX to the port of your choice. Usually, the default is 8888. 
   # You can try 8889 or 8890 as well.
   ```

2. Forward port XXXX to YYYY and listen to it

   In your remote, the notebook is now running at the port `XXXX` that you specified. What you’ll do next is forward this to port `YYYY` *of your machine* so that you can listen and run it from your browser. To achieve this, we write the following command:

   ```
   C:\Users\XiaolinHu>ssh -N -f -L localhost:YYYY:localhost:XXXX xiaolin@imimo
   ```

   - `ssh`: your handy ssh command. See [man page](https://man.openbsd.org/ssh) for more info
   - `-N`: suppresses the execution of a remote command. Pretty much used in port forwarding.
   - `-f`: this requests the `ssh` command to go to background before execution.
   - `-L`: this argument requires an input in the form of `local_socket:remote_socket`. Here, we’re specifying our port as `YYYY` which will be binded to the port `XXXX` from your remote connection.

3. Fire-up Jupyter Notebook

   To open up the Jupyter notebook from your remote machine, simply start your browser and type the following in your address bar:

   ```
   localhost:YYYY
   ```

   Again, the reason why we’re opening it at `YYYY` and not at `XXXX` is because the latter is already being forwarded to the former. `XXXX` and `YYYY` can be the “same” number (not the same port, technically) because they are from different machines.

   If you’re successful, you should see the typical Jupyter Notebook home screen in the directory where you ran the command in Step 1. At the same time, if you look in your remote terminal, you should see some log actions happening as you perform some tasks.

   In your first connection, you may be prompted to enter an Access Token as typical to most Jupyter notebooks. Normally, I’d just copy-paste it from my terminal, but to make things easier for you, you can [set-up your own notebook password](http://jupyter-notebook.readthedocs.io/en/stable/public_server.html#automatic-password-setup).