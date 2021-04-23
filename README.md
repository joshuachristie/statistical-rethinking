# Statistical rethinking book club

To run the code in the book and complete the questions, you'll need to download `R`, 
[rstan](https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started) and the following R packages (using `install.packages()`): 
`coda`,`mvtnorm`,`devtools`,`dagitty`, `ellipse`, and `ape`.

You also need to install McElreath's R package `rethinking` by running (from within R):

`library(devtools)`

`devtools::install_github('rmcelreath/rethinking')`

Of those steps, installing `rstan` is the trickest as you'll need to make sure you have a C++ compiler (and configure it for R).

Alternatively, you can run everything in a programming environment called a [jupyter notebook](https://jupyter.org/) 
via a piece of software called [docker](https://www.docker.com/get-started) (which one can use to configure a lightweight virtual software environment
that is standardized between operating systems).

I've set up a docker environments for R and also another for [edward2](https://github.com/google/edward2) and 
[tensorflow-probability](https://www.tensorflow.org/probability) using python if you'd prefer to use something other than R 
(you could also use [pymc3](https://docs.pymc.io/notebooks/getting_started.html) for another python alternative).

## Running docker images

The first step is to [download docker](https://www.docker.com/get-started).

Once you have downloaded and configured docker you need to get an `image` (the virtualisation that has all the software installed). 
You can get this by typing the following into your terminal ("Terminal" in mac/linux, "PowerShell" in windows):

`docker pull joshuarchristie/statistical-rethinking:r`

(If you want the tensorflow version, use `docker pull joshuarchristie/statistical-rethinking:tfp` instead.)

If you get a permission error then try ` sudo docker pull joshuarchristie/statistical-rethinking:r` and enter your password when prompted.

You can then run a `container` (a specific instance of the `image` you downloaded) by typing into the terminal (if mac/linux):

`docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/work joshuarchristie/statistical-rethinking:r`

or if on windows:

`docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v ${pwd}:/home/jovyan/work joshuarchristie/statistical-rethinking:r`

and then click on (or copy and paste) the underlined link down the bottom that says something like "or http://127.0.0.1:8888/...". (again use `sudo` if you have permission issues).

That will launch a jupyter notebook in your default browser where clicking on the `work` directory from within jupyter will show your current working directory 
(i.e. the directory given if you enter `pwd` in the terminal).
Click on the `R` button to open a new notebook using the configured R environment.

We can go through how to set this up when we meet if these instructions aren't very clear or if you run into any trouble.

To run the `tensorflow` image you need to use the following instead:

`docker run --gpus all --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/tf/notebooks/ joshuarchristie/statistical-rethinking:tfp`

## Chapter code and questions

In the [r/](./r/) directory I've added the code from chapter 2 of the book to `chapter2_code.ipynb` and the questions to `chapter2_questions.ipynb`.
If you fork the github repository and start docker from the [r/](./r/) directory then you can work on these files by navigating into the 
`work` directory in the jupyter notebook.
