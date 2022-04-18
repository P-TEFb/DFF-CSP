# DFF-CSP
DFF-CSP identifies center cluster regions (CCs) from DFF-ChIP sequencing datasets.

Author: Mrutyunjaya Parida, David Price Lab, UIOWA

## Usage:
DFF-ChIP-Seq Peak (DFF-CSP) runs on Python v2.7+. The DFF-CSP evaluates every CC window across the genome for the sum of fragment centers and the average read length. DFF-CSP-I is an interface program that runs the DFF-CSP program. It checks for errors in a user's input. If errors are found the DFF-CSP-I program displays the usage example and parameter description prior to exiting the run. 
If no use input errors are found DFF-CSP-I runs DFF-CSP program automatically.

Both DFF-CSP and DFF-CSP-I are intended to be run via a Python v2.7+ interpreter installed on your desired operating system of choice such as Windows, Mac or Linux. Additionally, DFF-CSP-I requires the joblib python module installed prior to the DFF-CSP run. If the module is missing DFF-CSP-I will guide you on installing the module. Finally, DFF-CSP-I expects the following syntax on a linux command-line interface:

```
python DFF-CSP-I <mapped-fragment-centers.bed file> <CC window size> <CC read depth> <chromosome sizes file>

Example run: python DFF-CSP-I mapped-fragment-centers.bed 8 10 KF297339.1.chrom.sizes.txt

```
Maintain the program files under the DFF-CSP-I_dir folder.

### Parameter description:
```
mapped-fragment-centers.bed file: A mapped fragment centers bed file can be generated from alignment files in sam
                           format using samtools and bedtools.

CC window size:           A desired size of the CC window (an integer). We found CCs are usually
                           8bp in width and are often clustered. This parameter can be increased or
			   decreased to find longer or shorter sized CCs.

CC read depth:            The minimum amount of fragment centers per CC (an integer). This determination of
                           this parameter can vary depending on sequencing depth and the amount of
			   background signal in your dataset.

chromosome sizes file:     DFF-CSP-I requires a chromosome sizes file. This file can be obtained
                           using [fetchChromSizes](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/)
			   utility.
```

### Output:
The final output is a comprehensive tab-delimited text file which contains information about non-overlapping CC boundaries, sum of CC read lengths, # of CC fragment centers, strand, the avg CC position.
