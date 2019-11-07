# tsrFinder
tsrFinder identifies transcription pause regions (TSRs) from PRO-Cap data.

Author: Mrutyunjaya Parida, David Price Lab, UIOWA

## Usage:
tsrFinder runs on Python v2.7+. The tsrFinderv2 evaluates every TSR window across the genome for the sum of 5' reads (transcription start sites) and the average read length. The tsrFinderI is an interface program that runs the actual tsrFinder program. It checks for errors in a user's input. If errors are found the tsrFinderI program displays the usage example and parameter description prior to exiting the run. 

Both tsrFinder and tsrFinderI are intended to be run via a Python v2.7+ interpreter installed on your desired operating system of choice such as Windows, Mac or Linux. The tsrFinderI expects the following syntax on a linux command-line interface:

```
python tsrFinderI <mapped-fragments.bed file> <TSR window size> <TSR read depth> <minimum average read length> <maximum fragment size> <chromosome sizes file>
```
Download and put tsrFinderI and tsrFinder programs under one folder.

### Parameter description:
```
mapped-fragments.bed file: A mapped fragment bed file can be generated from 
                           alignment files in sam format using samtools and bedtools.

TSR window size:           A desired size of the TSR window (an integer). We found TSRs are usually 
                           40bp in width and are often clustered. This parameter can be 
                           increased or decreased to find longer or shorter sized TSRs.

TSR read depth:            The minimum amount of reads per TSR (an integer). This determination of 
                           this parameter can vary depending on sequencing depth and the 
                           amount of background signal in your dataset.

minimum average read length: The desired minimum average read length (an integer) allows 
                           elimination of TSRs formed exclusively by sequencing artifacts 
                           and hard to map fragments. We observed TSRs tend to have an 
                           avearage read length of atleast 30nt.

maximum fragment size:     This parameter (an integer) allows exclusion of excessively long PRO-Seq reads. 

chromosome sizes file:     tsrFinder requires a chromosome sizes file. This file can be obtained 
                           using [fetchChromSizes](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/) 
                           utility.
```

### Output:
The final output is a comprehensive tab-delimited text file which contains information about both FW and RV strand TSR boundaries, sum of TSR read lengths, # of TSR reads, strand, the MaxTSS position, # of MaxTSS reads, the average TSS position, MaxTSS-averageTSS, and the standard deviation of the average TSS position.
