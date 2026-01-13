# BIOM 262: Introduction to Statisics, Day 1/2 (*Ad Hoc Lecture Notes*)

**Author**: Michelle Franc Ragsac (mragsac@ucsd.edu)

## Background

During the first day of this course module, the course JupyterHub was having trouble spawning interactive sessions students! So instead of having the majority of the class spend time following me go through a Jupyter Notebook, I did an **improv session** to teach the class how to **initialize environments for programming on one's *personal computer***!

This `.md` file contains the steps that we performed in that class session. The steps here can be used on your personal computer, but also on a shared, Linux-based cluster (e.g., the Triton Shared Compute Cluster, TSCC) to initialize computing environments for your future bioinformatics projects.

## Opening the Terminal

First, we want to open a **terminal** window. 

The terminal allows you to interact with your computer in a text-based fashion. Instead of clicking through different folders to get to a file you're interested in (i.e., through a graphical user interface, or GUI), you can perform those same functions in a text-based manner with commands in a terminal window.

Many of the common programming tools for data science and data visualization rely on the user to install packages through the terminal, which is what we'll be doing in the next few sections!

### Finding the Terminal Application on macOS and Windows

* For macOS users, you can find the [`Terminal` application](https://support.apple.com/guide/terminal/welcome/mac) under `Applications > Utilities > Terminal`
* For Windows users, you can use the [`Powershell` application](https://learn.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started?view=powershell-7.5) by searching for `PowerShell` with the Windows Taskbar search functionality

## Installing Software Packages and Initializing Software Environments

### Software Package Management Tools

With a terminal window open, we can now installing a **package management application** if you don't have one already. Package management applications support the installation, upgrading, configuring, and removing software in a consistent manner.

Instead of going to an individual website for each package we want to install, package management software allows you to define particular software tools you would like to download and it will handle installing things to your computer and grabbing particular software versions you are interested in.

### Software Environments

In the context of software, you can think of **environments** as spaces on your computer that are fine-tuned to run software programs under specific constraints. For example, you can install software packages with particular version numbers or in particular programming languages within a space that is isolated from other projects that have different requirements.

### [The `conda` Package Management and Environment Mangement System](https://www.anaconda.com/docs/getting-started/concepts/what-is-conda)

`conda` is an open-source, cross-platform, language-agnostic package manager and environment management system. Many people use `conda` to install packages for data science in languages such as Python, R, Julia, and more!

> [!WARNING]
> There are multiple ways to install `conda`. One of the most common ways is through the **Anaconda** installation. However, I do not recommend installing things through Anaconda as it contains installations for **other packages** that you may or may not use (i.e., packages meant for electrical engineering that wouldn't necessarily be useful in looking at biological data). 
> 
> Additionally, there was a [recent policy change for Anaconda](https://www.theregister.com/2024/08/08/anaconda_puts_the_squeeze_on/) that requires **all users to have an existing paid software license**, causing a lot of scandal within the data science community. Thus, we will be installing an alternative to the Anaconda distribution for this exercise: `miniconda`. 

### [Installing `conda` with the `miniconda` Distribution](https://www.anaconda.com/docs/getting-started/miniconda/main)

In this next section, we will be installing `conda` through the `miniconda` distribution. 

`miniconda` is a free, miniature installation of the Anaconda distribution that **only** includes the `conda` package manager, thus, it will serve our purposes for this course (and all future analyses) well!

> [!TIP]
> You can find more information on the differences between Anaconda and `miniconda` on the [official website](https://www.anaconda.com/docs/getting-started/concepts/anaconda-or-miniconda).

To install `miniconda`, you will first need to determine the installer for your system [on their website](https://www.anaconda.com/docs/getting-started/miniconda/install#quickstart-install-instructions); the installation script differs slightly depending on your operating system.

---

To verify that `miniconda` has been properly installed on your system, you can run the following command in your terminal window:

```bash
conda
```

Running `conda` by itself should produce some helpful documentation on how to run the tool. If you are having issues with running this command (i.e., it shows an error), you can try **exiting** the current terminal session, then re-opening a **new** terminal window.

### [Initializing the `conda` Environment](https://www.anaconda.com/docs/getting-started/concepts/what-is-an-environment)[^1]

[^1]: The `conda` documentation has helpful information on *environment management* on the following page: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

Now that we have `conda` installed, we can create a unique software environment that contains all of the packages required for this week's module. 

When you first install `conda`, it creates a **default environment** known as `base`. This environment is where `conda` itself is installed and should only be used to install conda-related applications. Therefore, we want to **create a new environment** to contain all of the software related to our project!

In your terminal window, please run the following `conda create` command to initialize a new software environment named `stats`.

```bash
conda create --name "stats"
```

> [!TIP]
> The `conda create --name "stats"` command will prompt a confirmation before you create the environment. However, it is possible to bypass this confirmation step and **force** `conda` to initialize the environment. To bypass the confirmation step, you can run the following command instead:
> 
> ```bash
> conda create --name "stats" --yes
> ```
> 
> This command forces `conda` to confirm for any "yes or no" prompts that may pop up during the initialization.

---

With the new `stats` environment created, you can then activate it with the following command:

```bash
conda activate stats
```

Now, if we run any software or scripts, they will run in the context of our `stats` environment!

> [!TIP]
> Depending on your operating system and terminal configuration settings, you may notice that now we are in the `stats` environment that your terminal has slightly changed as so:
> 
> ```bash
> (stats)
> ```
> 
> Sometimes, when changing environments, the terminal will display the name of the environment within parentheses (i.e., `()`). This helps you determine if you are installing packages or performing any operations in the proper space!
> 
> In the code blocks for the rest of this document, I'll be indicating that we are in the `stats` environment with `(stats)` in front of commands. **To ensure that running commands on your computer works, do *not* copy the `(stats)` portion of the command when copying things over to your computer. The command will not work.**

### [Installing Packages to the Newly-Initialized `stats` `conda` Environment](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html)

Now that we are in our new environment, we can install packages to the environment with the `conda install` command. For the first part of this module, we will need the following packages: `python`, `pandas`, `matplotlib`, `seaborn`, and `jupyterlab`. 

You can downlad these packages with the command listed below:

```bash
(stats) conda install python pandas matplotlib seaborn jupyterlab
```

> [!WARNING]
> When installing packages with `conda`, the tool will try and resolve package dependencies on the fly. For example, with the command listed above, `conda` will determine the versions of `python`, `pandas`, `matplotlib`, `seaborn`, and `jupyterlab` that satisfy all dependencies to ensure that all packages can be safely run in the same space.
>
> Therefore, if you are adding a new package to the mix and there are dependency errors, one quick tip is to uninstall the conflicting package, then re-install the package with the package that you were initially trying to install.

### [Displaying Existing Packages within a `conda` Environment with `conda list`](https://docs.conda.io/projects/conda/en/latest/commands/list.html)

After installing the packages, you can preview the packages installed to your environment (which will include the ones specified in the `conda install` command, along with any additional packages that are required to run those listed) with the `conda list` command.

The `conda list` command will show not just the names of packages installed, but also other helpful information, such as the version of the software that is in your environment!

> [!TIP]
> If you are interested in viewing the software version for a particular softare (e.g., `pandas`), you can run `conda list <package_name>` (e.g., `conda list pandas`) to view the version for all packages that match that provided string for the package name.

## [Opening the Statistics Module Content with `JupyterLab`](https://jupyterlab-exp.readthedocs.io/en/latest/getting_started/starting.html)

Now you have the software dependences installed to a proper environment, we can open the **Jupyter Notebooks** (i.e., the `.ipynb` files) for this module's interactive segments!

[**Jupyter Notebooks**](https://jupyterlab-exp.readthedocs.io/en/latest/user/notebook.html#) are documents that combine live runnable code with narrative text (Markdown), equations (LaTeX), images, interactive visualizations and other rich output. 

Jupyter Notebooks can be accessed with the [**Jupyter Lab** interface](https://jupyterlab-exp.readthedocs.io/en/latest/user/interface.html), which is an interactive programming space that includes a file browser (i.e., left-hand panel) among other tools to aid in programming and visualizing data.

> [!IMPORTANT]
> This section assumes that you have the content for this module downloaded to your computer in some location. You can find the content for this module [on the course GitHub](https://github.com/biom262/bnfo262-2026) under `module-2-statistics`.

> [!TIP]
> In your same terminal window, I recommend changing to the directory containing the files for this module. If you downloaded things through GitHub, then this directory might look something like: `../bnfo262-2026/module-2-statistics/`.

In this next section, we will open a Jupyter Lab instance[^2] from which to access everything. You can start a Jupyter Lab instance on your **local computer** by inputting the following commmand into the terminal:

[^2]: For more information on how `jupyter` creates URLs and how that enables you to access your file browser and programming notebooks, they have a nice page in the documentation on their website: https://jupyterlab-exp.readthedocs.io/en/latest/user/urls.html

```bash
(stats) jupyter lab
```

This command will open a local web session for Jupyter Lab: this manifests by the software opening a **new browser window** that should look similar to the JupyterHub that is traditionally used for this class.

## Conclusions

Finally, with the Jupyter Lab open and the dependencies installed, you should be able to open the Jupyter Notebooks for this course and run the desired code!

Cheers!