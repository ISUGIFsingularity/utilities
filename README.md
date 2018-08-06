# Bioinformatic scripts that we commonly use

This Singularity container is primarily for testing out how containers function.  All of the functions included in the container will run without a container.  Having them in a container results in a huge performance hit as singularity has to be called and these scripts do not have dependencies that could benefit from a container.  



**nb** = notebook to add text to a notebook but not the readme file
**readme **= readme will create a README file in the folder and put the date and text into this file along with a copy in the notebook
**createhist.awk** = function that will take a binsize argument and a list of numbers and return a count of numbers within increments of binsize
**intervalBins.awk** = modified createhist script that gives the intervals and counts of elements in the interval
**new_Assemblathon.pl** = script that will create summary statistics from a fasta file usually used for genome assemblies (see Assemblathon2 paper)
**seqlen.awk **= script that will take a fasta file and report the ID and the length of the sequence.
**colsum** = used to sum the Nth colum of a file.
**summary** = give summary statistics of a column of numbers


### Place singularity container into SIMG folder inside this repo

You can pull the singularity image using this command

```
cd $UTILITIESgit
mkdir SIMG
cd SIMG
singularity pull shub://ISUGIFsingularity/utilities:utilities.1.0.1

```

### Add Alias and PATH

Place the following into your .bashrc folder for container use

```
alias UTILITIESgit=Path2thisRepo
export PATH=$PATH:$UTILITIESgit/utilities
```

Place the following into your .bashrc folder to use scripts without container (preferred method unless testing container functions)

```
alias UTILITIESgit=Path2thisRepo
export PATH=$PATH:$UTILITIESgit/wrappers
```


### Notes

For this to function properly had to add ```--bind $UTILITIESgit:/mnt``` to the wrappers

Example

```
 singularity exec --bind $UTILITIESgit:/mnt --bind $PWD $UTILITIESgit/SIMG/ISUGIFsingularity-utilities-master.simg /mnt/utilities/summary.sh
```
