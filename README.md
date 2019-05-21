NP-SMLR is a software for nucleosome occupancy inference at single-molecule level. It takes the aligned signal-levels from Oxford Nanopore sequencing reads, and outputs the positions of all detected nuclosomes on each molecule.


# Dependencies

The current version has been tested in the Linux system with:
1. GCC (version 7.3.0);
2. Perl (version 5.16.3);
3. SAMtools (version 1.9);
4. BEDtools (version 2.28.0).



# Installation

You can download and compile the latest version as follows:

```
git clone https://github.com/Au-Lab/NP-SMLR.git
cd NP-SMLR
mkdir bin
make
```

After compilation, three executable files (`Likelihood`, `Detection` and `NclsPos`) will be generated in the folder `NP-SMLR/bin`.


**Please ensure that you have added**

1. The folder `NP-SMLR/bin`
2. `SAMtools`
3. `BEDtools`

**to your `PATH`.**



# Before running NP-SMLR

Before running NP-SMLR,
1. the reads have be aligned to reference genome; and
2. the alignments between event signals and reference genome should be obtained using `nanopolish eventalign`.

The tutorial of `nanopolish eventalign` can be found at https://nanopolish.readthedocs.io/en/latest/quickstart_eventalign.html.



# Usage

The command is

```
NP-SMLR.pl -b sorted_bam_file -e event_align_scale -o output_dir
```

* Parameters

-b   <STRING>   Name of the BAM file that records the alignment of reads. The BAM file must be sorted.
-g   <STRING>   Event alignment file generated by "nanopolish eventalign" (with flag --scale-events).
-t   <STRING>   Name of output folder.

* Example

The test example can be run using the command

```
NP-SMLR.pl -b ./testdata/sort_test.bam -e ./testdata/eventalign_scale_test.txt -o output
```

The generated files are stored under `output`.



# Output

The file `ncls_pos.bed` in the output folder records the coordinates of nucleosomes detected on each molecule. The columns represent:
Column 1: Chromosome ID;
Column 2: Start position of nucleosome;
Column 3: End position of nucleosome;
Column 4: Name of molecule (read);
Column 5: Quality score of alignment (obtained from BAM file);
Column 6: Strand on which the read is aligned.



# Current version

The version of the current release is v1.0.



# Contact

Please contact wanganqi18@gmail.com for any question.



# License

**Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License**

For details, please read `NP-SMLR/License`.



# Citation

Yunhao Wang, Anqi Wang, Zujun Liu, Andrew L. Thurman, Linda S. Powers, Meng Zou, Yue Zhao, Adam Hefel, Yunyi Li, Joseph Zabner, Kin Fai Au. Single-molecule long-read sequencing reveals the chromatin basis of gene expression. bioRxiv, 2019. DOI: https://doi.org/10.1101/533158
