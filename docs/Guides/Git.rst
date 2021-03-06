##############
Git and GitHub
##############

*********************
Creating a Repository
*********************

Lets say I’ve been developing some code in the directory **MyRepo** and would like to use Git for version control. Currently I have three files in **MyRepo** - *my1stCode.py*, *my2ndCode.py*, and *untracked.txt* :numref:`(Fig. %s) <MyRepo>`.

.. figure:: Git/Section1/MyRepo.png
    :width: 100%
    :align: center
    :figclass: align-center
    :name: MyRepo
     
    Contents of the MyRepo directory

Our first step is to initialize Git (i.e. create an empty Git repository) using the *init* command :numref:`(Fig. %s) <UnixInit>`, please note that this step is only required when creating a new repository and is not required when cloning a repository.

.. figure:: Git/Section1/UnixInit.png
    :width: 100%
    :align: center
    :figclass: align-center
    :name: UnixInit
     
    Initializing Git

Once initialized, we may begin version controlling our files. This process requires two steps: 1) we first stage file(s) using the *add* command :numref:`(Fig. %s) <UnixAdd>`; 2) we then are able to commit the staged file(s) using the *commit* command :numref:`(Fig. %s) <Unix1stCommit>`. Please note, that the *commit* command requires a message, which may be included alongside the command - i.e. *-m 'First Commit'* - or entered using the text editor.

.. figure:: Git/Section1/UnixAdd.png
    :width: 100%
    :align: center
    :figclass: align-center
    :name: UnixAdd
     
    Staging Files

.. figure:: Git/Section1/Unix1stCommit.png
    :width: 100%
    :align: center
    :figclass: align-center
    :name: Unix1stCommit
     
    Commiting Files
