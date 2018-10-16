# MemCplxDB

Table of Contents

* [Introduction](#introduction)
* [Repository Structure](#repository-structure)
* [Benchmark entries](#benchmark-entries)
  * [Dimeric complexes](#dimeric-complexes)
  * [Trimeric complexes](#trimeric-complexes)
* [Analysis](#analysis)
  * [HADDOCK terms](#haddock-terms)
  * [RMSD terms](#rmsd-terms)
  * [ProFit Instructions](#profit-instructions)

## Introduction

Membrane protein complexes docking benchmark. This repository contains the
entries of the Membrane Protein docking benchmark (V1.0). It also contains
[ProFit](http://www.bioinf.org.uk/programs/profit/) analysis scripts for
the calculation of Interface- and Ligand-RMSD (I-/L-RMSD) values for all
the entries of the becnhmark. We have generated docking decoys for all the
entries of the benchmark with the [HADDOCK](http://milou.science.uu.nl/services/HADDOCK2.2/)
webserver. In addition to I- and L-RMSDs we have calculated van der Waals,
Electrostatic and Desolvation energies and the Buried Surface Area (BSA)
for all decoys of all complexes.

## Repository Structure

The repository structure is the following:

    |   LICENSE
    |   README.md
    |   analysis
    |   \   random_restraints
    |   |   \   1k4c.txt
    |   |   |   1m56.txt
    |   |   /   ...
    |   |   true_interface
    |   |   \   1k4c.txt
    |   |   |   1m56.txt
    |   /   /   ...
    |   structures
    |   \   1k4c
    |   |   \   1k4c_bound.pdb
    |   |   |   1k4c_unbound.pdb
    |   |   |   1k4c_unbound_A.pdb
    |   |   |   1k4c_unbound_C.pdb
    |   |   |   AC.irmsd
    |   |   |   AC.izone
    |   |   /   AC.lzone
    |   |   1m56
    |   |   \   1m56_bound.pdb
    |   |   |   1m56_unbound.pdb
    |   |   |   1m56_unbound_AB.pdb
    |   |   |   1m56_unbound_CD.pdb
    |   |   |   AB.irmsd
    |   |   |   AB.izone
    |   |   /   AB.lzone

The [structures](structures) folder contains all the structure files in PDB format. Both
reference (bound) and unbound structures are included. All structures have been
modified so that chain identifiers and residue numbering is consistent.

Every subfolder in the [structures](structures) folder (eg [1k4c](structures/1k4c)) contains
the following files:

* `*_bound.pdb` -> The reference structure for a given complex.
* `*_unbound_*.pdb`-> The unbound structures for a given complex.
* `*_unbound.pdb` -> The unbound structures optimally and independently superimposed on the reference chains.
* `*.irmsd` -> The backbond I-RMSD (in Å) of the unbound complex relative to the reference structure.
* `*.izone` -> [ProFit](http://www.bioinf.org.uk/programs/profit/)-compatible I-RMSD calculation script.
* `*.lzone` -> [ProFit](http://www.bioinf.org.uk/programs/profit/)-compatible L-RMSD calculation script.

The two subfolders in the [analysis](analysis) folder contain the results of the docking
runs for two docking scenarios. One using only random restraints to drive the docking
([random_restraints](analysis/random_restraints)) and one using restraints derived from
the interface of the bound complex ([true_interface](analysis/true_interface)). Both folders
contain 37 space-separated text files that are the results of the analysis of the docking
run of a given complex.

## Benchmark entries

The two tables below list the dimeric and trimeric entries respectively. The second column is the PDB
id of the bound complex, the second and third (second through fourth for the trimeric table) list the
origin of the unbound structures for that complex. The complexes that appear more than once in the
benchmark are idenitified by the presence of an identifier in the complex_id field (eg 2r6g-TM).

The _Category_ column refers to the nature of the complex. MS stands for complexes whose interface lies
along the membrane-soluble region, TM stands for complexes whose interface lies within the membrane,
Both stands for complexes whose interface lies in both membrane and soluble regions, Buried stands for
complexes where one of the partners is buried in a transmembrane β-barrel and AB stands for complexes
where one of the partners is an antibody-like domain.

The _Composition_ column refers to the origin of the unbound structures of a complex. BB stands for
Bound-Bound and means all partners have been extracted from the bound complex, UB stands for Bound-Unbound
and means at least one of the partners has been extracted from an alternative structure and UU stands
for Unbound-Unbound and means none of the partners originate in the bound complex.

The _Difficulty_ column reflects the difficulty of a given complex with Bound cases having an I-RMSD
of 0, Easy cases having an I-RMSD between 0 and 1Å, Intermediate cases having an I-RMSD between 1 and 2Å
and Hard cases having an I-RMSD greater than 2Å.

### Dimeric complexes

| complex | complex_pdb_id | Unbound PDB id 1 | Unbound PDB id 2 | Category | Composition |  Difficulty  | Interface RMSD [Å] |
| ------: | -------------- | ---------------- | ---------------- | -------- | ----------- | -----------  | -----------------: |
| 1       | 2bg9           | 2bg9_ADE         | 2bg9_BC          | Both     | BB          | Bound        | 0                  |
| 2       | 2bs2           | 2bs2_AB          | 2bs2_CD          | MS       | BB          | Bound        | 0                  |
| 3       | 2r6g-TM        | 2r6g_F           | 2r6g_G           | TM       | BB          | Bound        | 0                  |
| 4       | 2vpz           | 2vpz_AB          | 2vpz_CD          | MS       | BB          | Bound        | 0                  |
| 5       | 4hg6           | 4hg6_A           | 4hg6_B           | TM       | BB          | Bound        | 0                  |
| 6       | 4huq-TM        | 4huq_S           | 4huq_T           | TM       | BB          | Bound        | 0                  |
| 7       | 4huq-TM-A      | 4huq_ST          | 4huq_A           | MS       | BB          | Bound        | 0                  |
| 8       | 4huq-TM-B      | 4huq_ST          | 4huq_B           | MS       | BB          | Bound        | 0                  |
| 9       | 5a63-BC        | 5a63_B           | 5a63_C           | TM       | BB          | Bound        | 0                  |
| 10      | 2hdi           | 2hdi_A           | 1cii_A           | Buried   | UB          | Easy         | 0.361              |
| 11      | 4j3o           | 4j3o_D           | 3bfq_FG          | Buried   | UB          | Easy         | 0.392              |
| 12      | 1m56           | 2gsm_AB          | 1m56_CD          | TM       | UB          | Easy         | 0.572              |
| 13      | 1k4c           | 1k4c_A           | 1j95_ABCD        | MS       | UU          | Easy         | 0.638              |
| 14      | 3x29           | 3x29_A           | 2quo_A           | MS       | UB          | Easy         | 0.673              |
| 15      | 2k9j           | 2rmz_A           | 2k1a_A           | TM       | UU          | Easy         | 0.678              |
| 16      | 2r6g-TM-peri   | 2r6g_FG          | 1jw4_A           | MS       | UB          | Easy         | 0.716              |
| 17      | 2gsk           | 2guf_A           | 1u07_A           | MS       | UU          | Easy         | 0.86               |
| 18      | 5aww           | 5aww_YG          | 5aww_E           | TM       | UB          | Easy         | 0.868              |
| 19      | 2zxe-AG        | 2zxe_A           | 2zxe_G           | TM       | UB          | Easy         | 0.919              |
| 20      | 2zxe-AB        | 2zxe_A           | 2zxe_B           | TM       | UB          | Easy         | 0.94               |
| 21      | 3wxw           | 3wxw_A           | 1vfa_HL          | AB       | UB          | Easy         | 0.982              |
| 22      | 3hd7           | 3hd7_A           | 3hd7_B           | TM       | UU          | Intermediate | 1.024              |
| 23      | 3csl           | 3csl_A           | 1b2v_A           | MS       | UB          | Intermediate | 1.065              |
| 24      | 2ks1           | 2n2a_A           | 2m0b_A           | TM       | UU          | Intermediate | 1.158              |
| 25      | 5d0o           | 5d0o_A           | 2yhc_A           | MS       | UB          | Intermediate | 1.182              |
| 26      | 5a63-AC        | 5a63_A           | 5a63_C           | TM       | UB          | Intermediate | 1.218              |
| 27      | 3p0g           | 2rh1_A           | 4unu_A           | AB       | UU          | Intermediate | 1.26               |
| 28      | 2r6g-TM-cyto   | 2r6g_FG          | 1q12_AB          | MS       | UB          | Intermediate | 1.363              |
| 29      | 3o0r           | 3o0r_B           | 3o0r_C           | AB       | UB          | Intermediate | 1.445              |
| 30      | 5fxb           | 5fxb_AB          | 1ttf_A           | AB       | UB          | Intermediate | 1.475              |
| 31      | 4q35           | 4q35_A           | 4nhr_A           | Buried   | UB          | Hard         | 2.061              |
| 32      | 4m48           | 4m48_A           | 4dvb_HL          | AB       | UB          | Hard         | 2.335              |
| 33      | 2hi7           | 1ti1_A           | 2k73_A           | MS       | UU          | Hard         | 2.588              |
| 34      | 1ots           | 1kpk_AB          | 4nzu_HL          | AB       | UU          | Hard         | 3                  |
| 35      | 3v8x           | 3v8x_A           | 4x1b_A           | MS       | UB          | Hard         | 3.422              |

### Trimeric complexes

| complex | complex_pdb_id | Unbound PDB id 1 | Unbound PDB id 2 | Unbound PDB id 3 | Category | Composition |  Difficulty  | Interface RMSD [Å] |
| ------: | -------------- | ---------------- | ---------------- | ---------------- | -------- | ----------- |  ----------  | -----------------: |
| 1       | 2j8s           | 3w9h_A           | 3w9h_B           | 3w9h_C           | Both     | UUU         | Easy         | 0.648              |
| 2       | 4fz0           | 2qts_A           | 2qts_B           | 2qts_C           | Both     | UUU         | Intermediate | 1.18               |

## Analysis

All the RMSD values have been calculated with [ProFit](http://www.bioinf.org.uk/programs/profit/) and
all energy values along with Surface area by [HADDOCK](http://milou.science.uu.nl/services/HADDOCK2.2/).

The following is an example of the results of the analysis for dimeric complex.

    $ head 1k4c.txt
    complex i-RMSD l-RMSD HS Eair Evdw Eelec Edesolv BSA stage pdb rank difficulty
    1 0.959 2.102 -35.7645987 417.16 9.01013 -14.8071 -12.3443 1287.49 it0 1k4c 705 Easy
    2 13.601 30.105 -10.0395301 1298.94 -1.60801 -4.26846 -6.80819 1193.62 it0 1k4c 6360 Easy
    3 10.638 26.939 -25.8562489 1185.26 4.58911 -5.10454 -19.5606 1308.96 it0 1k4c 3083 Easy
    4 6.757 20.617 -26.756805 990.199 12.5825 -9.88172 -11.7789 1512.4 it0 1k4c 2916 Easy
    5 0.934 4.333 -31.571787 602.385 24.9723 -16.4337 -8.06686 1334.48 it0 1k4c 2137 Easy
    6 14.473 29.379 -2.988335 1385.01 26.7835 -1.33664 -4.52393 1124.57 it0 1k4c 8595 Easy
    7 14.348 29.247 -4.985707 1253.87 20.8563 -0.97943 -5.58424 1116.93 it0 1k4c 8029 Easy
    8 10.826 26.383 -25.9056835 1206.93 -2.13535 -4.64953 -19.672 1363.21 it0 1k4c 3074 Easy
    9 6.213 27.452 -10.763576 1411.04 24.4844 -2.1838 -14.0344 890.062 it0 1k4c 6111 Easy

and for a trimeric one

    complex i-RMSD l-RMSD l-RMSD-sd HS Eair Evdw Eelec Edesolv BSA stage pdb rank difficulty
    1 46.268 75.6035 1.8335 1790.72757 102074 718.818 -13.7373 7.13569 1901.6 it0 4fz0 8305 Intermediate
    2 33.500 51.8455 1.1275 401.32159 38540.4 248.141 -9.81252 -51.7452 3421.41 it0 4fz0 393 Intermediate
    3 36.232 58.523 17.595 673.51548 50304 375.559 53.4633 5.52919 3188.66 it0 4fz0 3527 Intermediate
    4 47.686 62.758 6.711 636.45832 53861.1 356.872 -10.6338 31.3379 3474.35 it0 4fz0 3109 Intermediate
    5 53.633 89.111 14.586 1552.34581 117606 412.29 -7.01079 6.8906 1238.89 it0 4fz0 7804 Intermediate
    6 18.942 41.166 0.153 663.585429 53746.8 388.635 12.9086 -0.648221 2777.93 it0 4fz0 3401 Intermediate
    7 38.178 61.3475 1.0615 579.84936 46221.8 172.666 42.2576 15.0654 3910.15 it0 4fz0 2494 Intermediate
    8 34.095 62.5555 16.3635 833.98877 66967.1 250.811 5.05806 34.3765 3304.69 it0 4fz0 5141 Intermediate
    9 49.997 91.598 8.271 2210.46723 89319.8 419.985 -7.88672 -13.6433 2024.06 it0 4fz0 8940 Intermediate

### HADDOCK terms

The values that have been calculated with HADDOCK are the Eair, Evdw, Eelec, Edesolv and BSA terms.
HS stands for HADDOCK-SCORE which is a weighted sum of the pervious terms. Eair refers to the
restraint energy, Evdw and Eelec are the non-bonded terms and are calculated with the OPLS force
field, Edesolv stands for desolvation energy and BSA stands for Buried Surface Area.

The terms that are related to HADDOCK but are not included in the scoring of complexes are stage,
and rank. Stage refers to one of three stages of a HADDOCK run:

* it0 - Rigid-body energy minisation
* it1 - Simulated annealing in torsional space
* itw - Flexible refinement in explicit solvent

Rank refers to the ranking of that particular structure by the HADDOCK scoring function.

### RMSD terms

The two RMSD terms are i-RMSD and l-RMSD. They stand for interface and ligand RMSD respectively. For
the I-RMSD calculation we have calculated the RMSD of the backbone atoms of the interface. The interface
is defined as the set of residues whose atoms are within 10Å of any atom of a partner. For the L-RMSD
calculation we have superimposed the receptors (defined as the biggest partner) using all backbone atoms
and calculated the displacement of the backbone atoms of the ligand (defined as the smallest partner).
For the trimers, we have calculated the displacement of both partners (with regards to the first) and
report their mean and standard deviation.

### ProFit Instructions

Those interested in reproducing the RMSD calculations can do so with the following ProFit commands

Using complex `1m56` as an example.

For the I-RMSD calculations:

`profit -f AB.izone 1m56_bound.pdb 1m56_unbound.pdb`

If ProFit is correctly installed on your system you should see the following output:

                  PPPPP                FFFFFF ii   tt
                  PP  PP               FF          tt
                  PP  PP rrrrr   oooo  FF     ii  ttttt
                  PPPPP  rr  rr oo  oo FFFF   ii   tt
                  PP     rr     oo  oo FF     ii   tt
                  PP     rr     oo  oo FF     ii   tt
                  PP     rr      oooo  FF      ii   ttt

                      Protein Least Squares Fitting

                               Version 3.1

      Copyright (c) Dr. Andrew C.R. Martin, SciTech Software 1992-2009
              Copyright (c) Dr. Craig T. Porter, UCL 2008-2009

     Reading reference structure...
     Reading mobile structure...

     Starting script: 'AB.izone'
     Fitting structures...
     RMS: 0.572
     Finished script: 'AB.izone'

The line starting with RMS contains the I-RMSD value.

For the L-RMSD calculations:

`profit -f AB.lzone 1m56_bound.pdb 1m56_unbound.pdb`

Which should print:

                  PPPPP                FFFFFF ii   tt
                  PP  PP               FF          tt
                  PP  PP rrrrr   oooo  FF     ii  ttttt
                  PPPPP  rr  rr oo  oo FFFF   ii   tt
                  PP     rr     oo  oo FF     ii   tt
                  PP     rr     oo  oo FF     ii   tt
                  PP     rr      oooo  FF      ii   ttt

                      Protein Least Squares Fitting

                               Version 3.1

      Copyright (c) Dr. Andrew C.R. Martin, SciTech Software 1992-2009
              Copyright (c) Dr. Craig T. Porter, UCL 2008-2009

     Reading reference structure...
     Reading mobile structure...

     Starting script: 'AB.lzone'
     Fitting structures...
     RMS: 0.560
     RMS: 0.000
     Finished script: 'AB.lzone'

In this case two RMSD values are calculated and printed to the terminal. The first is the RMSD
of the backbone atoms of the receptor (in this case chain A). The second is the L-RMSD value.
In this case it is 0 as chain B has been extracted from the bound complex for case `1m56`.
