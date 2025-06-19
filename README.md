# Average Nucleotide Identity analysis


### **Asad Prodhan PhD** 

https://asadprodhan.github.io/


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

- Create a conda environment

  ```
  conda create -n ani
  ```

  - Activate the ani environment
 
  ```
  conda activate ani
  ```


- Instal pyani as follows:


```
conda install -c bioconda pyani
```

- Check it has been installed. Copy the following command and hit enter

```
average_nucleotide_identity.py
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
dos2linux *.txt
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

