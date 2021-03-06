# Acknowledging authorship #
In the academic spirit of collaboration, the source code should be appropriately acknowledged in the resulting scientific disseminations.  
You may cite it as follows: 
- [1], for reference to the origins of the EnergyScope project or to the first online version of the calculator energyscope.ch
- [2], for reference to the energyscope MILP modeling framework
- [3], for reference to this specific release of the model (v1 monthly MILP)

You are welcome to report any bugs related to the code to the following:  
moret.stefano@gmail.com


# Content #
This folder contains the first release (v1, monthly MILP) of the EnergyScope (ES) model.  
More recent releases are available @ the energyscope project repository: https://github.com/energyscope/EnergyScope   
This version of the model corresponds to the one documented in [3], Chapter 1.  
The data used in this version of the model are fully documented in [3], Appendix A.


# How to run the model #
The model is coded in GLPK, using the open-source solver GLPSOL. To run the model, perform the following 4 steps:

1. Install GLPK:

a) on Mac OS X (Option 1, recommended): use homebrew
http://arnab-deka.com/posts/2010/02/installing-glpk-on-a-mac/

b) on Mac Os X (Option 2)/Linux:
- Download the latest version of GLPK from: http://www.gnu.org/software/glpk/#downloading
- Install GLPK from the command line

$ cd ~/Downloads  
$ tar -xzf glpk-4.63.tar.gz  
$ cd  glpk-4.63 [or newer version]  
$ ./configure --prefix=/usr/local  
$ make  
$ sudo make install  

See if your system recognises it:

$ which glpsol

should reveal:

$ /usr/local/bin/glpsol

Now try:

$ glpsol --help

Source: http://hichenwang.blogspot.ch/2011/08/fw-installing-glpk-on-mac.html

c) on Windows:

- Download the source files from: https://sourceforge.net/projects/winglpk/files/latest/download
- Extract the files in a folder. Depending on your operating system use glpsol.exe from:
./w64 if running on a 64 bit version
./w32 if running on a 64 bit version
- For facilitating the access to glpsol.exe you can add the full path (depending on your operating system, see below) from the previous point to the system variables PATH

2. Clone/download the content of this folder
3. Navigate to that folder via terminal/cmd prompt and execute (check glpsol documentation for more options):

$ glpsol -m ses_main.mod -d ses_main.dat -o ses_main.out
(You might need to use 'glspol.exe' on Windows)

4. Check that the ses_main.out file is correctly generated.

If the command at point (3) did not run, it might be that glpsol is not on your PATH. Two solutions for that:
- (not best) instead of "glpsol" use the full path, e.g. on Mac '/usr/local/bin/glpsol  -m ses_main.mod -d ses_main.dat -o ses_main.out'
- (best) add the folder in which glpsol is installed to the PATH. e.g. on Windows 7 (http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx). on mac (from terminal) 'export PATH=/usr/local/bin:$PATH' (if glpsol is installed in /usr/local/bin)

The model was originally developed in AMPL. Compatible solvers are CPLEX, Gurobi, etc. Running the model in AMPL requires the licences of AMPL and of at least one MILP solver.


References:  
[1] V. Codina Gironès, S. Moret, F. Maréchal, D. Favrat (2015). Strategic energy planning for large-scale energy systems: A modelling framework to aid decision-making. Energy, 90(PA1), 173–186. https://doi.org/10.1016/j.energy.2015.06.008  
[2] S. Moret, M. Bierlaire, F. Maréchal (2016). Strategic Energy Planning under Uncertainty: a Mixed-Integer Linear Programming Modeling Framework for Large-Scale Energy Systems. https://doi.org/10.1016/B978-0-444-63428-3.50321-0  
[3] S. Moret (2017). Strategic Energy Planning under Uncertainty. PhD Thesis n. 7961, EPFL, Switzerland. http://dx.doi.org/10.5075/epfl-thesis-7961