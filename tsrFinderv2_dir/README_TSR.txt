tsrFinderv2 identifies transcription start regions (TSRs) from PRO-Cap and similar nascent transcript sequencing datasets.

Author: Mrutyunjaya Parida, David Price Lab, UIOWA

Usage:
tsrFinderv2 runs on Python v2.7+. The tsrFinderv2 evaluates every TSR window across the genome for the
sum of 5' reads (transcription start sites) and the average read length. tsrFinderv2 checks for errors
in a user's input. If errors are found the tsrFinderv2 program displays the usage example and parameter
description prior to exiting the run. 

tsrFinderv2 syntax:

tsrFinderv2 <mapped-fragments.bed file> <TSR window size> <TSR read depth> <minimum average read length> <maximum fragment size> <chromosome sizes file>

Download and put tsrFinderI and tsrFinder programs under one folder.

Parameter description:

mapped-fragments.bed file: A mapped fragment bed file can be generated from alignment files in sam
                           format using samtools and bedtools.

TSR window size:           A desired size of the TSR window (an integer). We found TSRs are usually
                           20bp in width and are often clustered. This parameter can be increased or
			   decreased to find longer or shorter sized TSRs.

TSR read depth:            The minimum amount of reads per TSR (an integer). This determination of
                           this parameter can vary depending on sequencing depth and the amount of
			   background signal in your dataset.

minimum average read length: The desired minimum average read length (an integer) allows elimination
                             of TSRs formed exclusively by sequencing artifacts and hard to map
			     fragments. We observed TSRs tend to have an avearage read length of
			     atleast 30nt.

maximum fragment size:     This parameter (an integer) allows exclusion of excessively long PRO-Seq
                           reads. 

chromosome sizes file:     tsrFinderv2 requires a chromosome sizes file. This file can be obtained
                           using [fetchChromSizes](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/)
			   utility.

Output:

                           The final output is a comprehensive tab-delimited text file which contains
			   information about both FW and RV strand TSR boundaries, sum of TSR read lengths,
			   # of TSR reads, strand, the MaxTSS position, # of MaxTSS reads, the average TSS
			   position, MaxTSS-averageTSS, and the standard deviation of the average TSS position.
			   
