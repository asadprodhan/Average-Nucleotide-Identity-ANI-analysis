
<h1 align="center">Average Nucleotide Identity Analysis for Diagnosis</h1>


<h3 align="center">M. Asaduzzaman Prodhan<sup>*</sup></h3>


<div align="center"><b> DPIRD Diagnostics and Laboratory Services, Department of Primary Industries and Regional Development </b></div>


<div align="center"><b> 3 Baron-Hay Court, South Perth, WA 6151, Australia </b></div>


<div align="center"><b> <sup>*</sup>Correspondence: Asad.Prodhan@dpird.wa.gov.au </b></div>


<br />


<p align="center">
  <a href="https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL%203.0-yellow.svg" alt="License GPL 3.0" style="display: inline-block;"></a>
  <a href="https://orcid.org/0000-0002-1320-3486"><img src="https://img.shields.io/badge/ORCID-green?style=flat-square&logo=ORCID&logoColor=white" alt="ORCID" style="display: inline-block;"></a>
</p>


<br />


Average Nucleotide Identity (ANI) analysis calculates the percentage of nucleotide identity among the supplied nucleotide sequences. It produces a square matrix of the calculated values. This matrix allows for pairwise comparisons among the nucleotide sequences and helps determine their similarities. 


<br />

## Contents  

- [ANI methods](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/README.md#ani-methods)  
- [ANI tools](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/README.md#ani-tools)  
- [How to run pyani](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/README.md#how-to-run-pyani)  
- [Results](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/README.md#results)  
- [References](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/README.md#references)  

<a name="headers"/>

<br />


## **ANI methods**


There are several methods to calculate the ANI:


- ANIb (based on BLAST algorithm)

- ANIm (based on MUMmer algorithm)

- TETRA (based on tetranucleotide signature occurrences)

<br />

## **ANI tools**


There are several tools available for ANI analysis (Figueras et al., 2014). For example:


- JSpecies (http://www.imedea.uib.es/jspecies) (multiple genome analysis)


- Gegenees (http://www.gegenees.org/documentation.html) (Due to changes in NCBI Blast, Gegeneese may not function with Blast versions 2.10 and later. Blast version 2.9 should work OK) 


- EzGenome (http://www.ezbiocloud.net/ezgenome/ani) [online] 


- ANI calculator (http://enve-omics.ce.gatech.edu/ani/index) [online] (only two genomes per analysis)


- Python3 package (pyani) (https://github.com/widdowquinn/pyani, https://pyani.readthedocs.io/en/latest/run_anim.html) based on (Richter and Rossello´-Mo´ra, 2009). Pyani uses MUMmer algorithm.

<br />

## **How to run pyani**


- If you are working on HPC Cluster, load the required version of python

  ```
  module load cray-python/3.10.10
  ```

- Create a conda environment with the compatible version of python, matplotlib and pyani

  ```
  conda create -n pyani_env python=3.10 "matplotlib<=3.7" "pyani>=0.2.12" -c bioconda
  ```

- Activate the ani environment
 
  ```
  conda activate pyani_env
  ```

- Alternatively, you can use my conda environment for pyani


- #### Download it [HERE](https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/pyani_env.yml)


- #### Then activate it as follows


  ```
  conda env create -f pyani_env.yml 
  ```


- Check it has been installed. Copy the following command and hit enter

  ```
  average_nucleotide_identity.py --help
  ```

The above command will show the flags/options of the pyani program

- Install dos2unix for changing file format

  ```
  conda install conda-forge::dos2unix
  ```

- Check it has been installed. Copy the following command and hit enter

  ```
  dos2unix
  ```

- Make two metadata files and name them as ‘classes.txt’ (Fig. 1) and ‘labels.txt’ (Fig. 2)


<br />
<p align="center">
  <img 
    src="https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/classes.PNG"
  >
</p>
<p align = "center">
Figure 1. Classes
</p>


<br />
<p align="center">
  <img 
    src="https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/labels.PNG"
  >
</p>
<p align = "center">
Figure 2. Labels
</p>



> Note, the first column is the nucleotide sequences names

> Second column is the label of the nucleotide sequences
 
 <br />
 

- Make a directory and name it as ‘ANI’ for example


- Within the ‘ANI’ directory, make another directory and name it as ‘genomes’ for example


- Keep all the nucleotide sequences, ‘classes.txt’ and ‘labels.txt’ in the ‘genomes’ directory


- Check the line terminator of the ‘classes.txt’ and ‘labels.txt’ files as follows 


```
file *.txt
```


- If ‘classes.txt’ and ‘labels.txt’ have CRLF (Windows) format, then convert them into Unix format as follows:



```
dos2unix *.txt
```

- Run the following command from the ‘ANI’ directory



```
average_nucleotide_identity.py -i genomes -o output_ANI --labels genomes/labels.txt --classes genomes/classes.txt -g --gmethod seaborn --gformat pdf,png -v -l ba_ANI.log
```


- Note that you do not make the output directory beforehand. Otherwise, the command will exit with an ‘overwriting’ error



- Command reference: https://github.com/widdowquinn/pyani/issues/56

<br />

## **Results**


The final output of the ANI analysis looks like this (Fig. 3):


<br />
<p align="center">
  <img 
    src="https://github.com/asadprodhan/Average-Nucleotide-Identity-ANI-analysis/blob/main/ANIm_percentage_identity.png"
  >
</p>
<p align = "center">
Figure 3. Results
</p>


<br />

## **References**


Figueras, M.J., Beaz-Hidalgo, R., Hossain, M.J., Liles, M.R., 2014. Taxonomic Affiliation of New Genomes Should Be Verified Using Average Nucleotide Identity and Multilocus Phylogenetic Analysis. Genome Announc 2, e00927-14. https://doi.org/10.1128/genomeA.00927-14


Richter, M., Rossello´-Mo´ra, R., 2009. Shifting the genomic gold standard for the prokaryotic species definition | Proceedings of the National Academy of Sciences. PNAS 106, 19126–19131. https://doi.org/10.1073/pnas.0906412106

