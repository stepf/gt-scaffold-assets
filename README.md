###gt-scaffold-assets

Supplementary data and tools to evaluate [gt-scaffold](https://github.com/dorleosterode/gt-scaffold)

####Data sets
The test data was generated using a Dockerized SGA pipeline (see ./docker). The various input reads were generated from a reference using `art_illumina` with the following profile:

```Shell
art_illumina -sam -i Enterobacteriophage_lambda.fa -l 150 -f 20 -m 400 -s 10 -rs 123 -o e_lambda
=======================================ART======================================
                            ART_Illumina (2008-2014)
                            Q Version 2.1.8 (Mar 8, 2014)
                     Contact: Weichun Huang at whduke@gmail.com
================================================================================

                          Paired-end sequencing simulation

Total CPU time used: 25.8323

The random seed for the run: 123

Parameters used during run
  Read Length:  150
  Genome masking 'N' cutoff frequency:  1 in 150
  Fold Coverage:            20X
  Mean Fragment Length:     400
  Standard Deviation:       10
  Profile Type:             Combined
  ID Tag:

Quality Profile(s)
  First Read:    EMP250R1 (built-in profile)
  Second Read:   EMP250R2 (built-in profile)
```
