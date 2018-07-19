# MemCplxDB

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

+ `*_bound.pdb` -> The reference structure for a given complex.
+ `*_unbound_*.pdb`-> The unbound structures for a given complex.
+ `*_unbound.pdb` -> The unbound structures optimally and independently
superimposed on the reference chains.
+ `*.irmsd` -> The backbond I-RMSD (in Å) of the unbound complex relative
to the reference structure.
+ `*.izone` -> [ProFit](http://www.bioinf.org.uk/programs/profit/)-compatible I-RMSD
calculation script.
+ `*.lzone` -> [ProFit](http://www.bioinf.org.uk/programs/profit/)-compatible L-RMSD
calculation script.

The two subfolders in the [analysis](analysis) folder contain the results of the docking
runs for two docking scenarios. One using only random restraints to drive the docking
([random_restraints](analysis/random_restraints)) and one using restraints derived from
the interface of the bound complex ([true_interface](analysis/true_interface)). Both folders
contain 38 space-separated text files that are the results of the analysis of the docking
run of a given complex.

## Benchmark entries

### Dimeric complexes

| complex | complex_pdb_id | Unbound PDB id 1 | Unbound PDB id 2 | Category | Composition |  Difficulty  | Interface RMSD [Å] |
| :-----: | -------------- | ---------------- | ---------------- | -------- | ----------- | -----------  | -----------------: |
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
| :-----: | -------------- | ---------------- | ---------------- | ---------------- | -------- | ----------- |  ----------  | -----------------: |
| 1       | 1yew           | 1yew_ABC         | 1yew_EFG         | 1yew_IJK         | Both     | BBB         | Bound        | 0                  |
| 2       | 2j8s           | 3w9h_A           | 3w9h_B           | 3w9h_C           | Both     | UUU         | Easy         | 0.648              |
| 3       | 4fz0           | 2qts_A           | 2qts_B           | 2qts_C           | Both     | UUU         | Intermediate | 1.18               |
