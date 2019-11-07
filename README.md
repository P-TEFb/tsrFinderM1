# tsrfinderv2
tsrFinder identifies transcription start regions (TSRs) from PRO-Cap data. The current tsrfinder is an updated version of the original tsrFinder written by Kyle Nilson.

Author: Mrutyunjaya Parida, David Price Lab, UIOWA

Please download and put TSR_F_V2 and TSR_F programs under one folder.
```
Please provide these details to run TSR finder properly:
a) input file to run such as /home/<user>/<folder name>/mapped-fragments.bed.
   Please provide the full path of the input file.
   <user> refers to username and <folder name> is where the file is.
b) TSR window size is an integer such as 20
c) TSR read depth is an integer such as 20
d) TSR average read length is an integer such as 30
e) Fragment size is an integer such as 600
f) chromosome size file path and name such as ###.chrom.sizes
```
Note: tsrFinderv2 runs on Python 2.7+ version. Please refer to https://github.com/P-TEFb/tsrFinder for description on the program features and details. 
Key differences are as follows:

The script accepts mapped sequencing reads in bed format and requires a chrom.sizes file (obtainable using the [fetchChromSizes](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/) utility). TSR information is output in bed format only, for use with utilities such as [bedtools](http://bedtools.readthedocs.io/en/latest/).

No parameters are hardcoded in this script.
No options for number of threads and size of memory buffer per thread.

The score field in the output bed file is not clipped at 1000.

The final output is a comprehensive tab-delimited text file which contains information about both FW and RV strand TSR boundaries, sum of TSR read lengths, # of TSR reads, strand, the max TSS position, # of MaxTSS reads, the average TSS position, maxTSS-avgTSS, and the standard deviation of the average TSS position.

```
Example run of TSR finder: python TSR_F_V2 mapped-fragments.bed 20 20 30 600 ###.chrom.sizes
```
