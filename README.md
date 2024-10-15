# Repository for Genetic Landscape and Evolution of _Acinetobacter pittii_ -an underestimated emerging nosocomial pathogen of Wang et al

## File content
### dcgMLST allelic profile
1. Pangenome presence/absence profile
~~~
Wang-et-al-repo-for-A.-pittii/pangenome.content.0819tab.transposed.titled.hc1100.modi
~~~
2. Reference allelic sequences
~~~
Wang-et-al-repo-for-A.-pittii/0805_Cinch_0805_Cinch.726Ap_pp.allele.pan.allele.modi.cds.cinch.fasta
~~~
3. dcgMLST allelic profile
~~~
0805_Cinch.profile
~~~
### Plasmid identification based PlasT pipeline
PlasT is a stand-alone module of [KleTY](https://github.com/zheminzhou/KleTy) (DOI: <https://doi.org/10.1101/2024.04.16.24305880>), which can predict potential plasmid sequences from assembled genome file.
Usage:
~~~
python PlasT.py [genome]
~~~
We have give a genome containing a PT712 plasmid, named [WZ-35_4.fna]. You can use WZ-35_4.fna to do a test for PlasT. This will generate a prediction based on identity against our pre-clustered dataset, and assign a cluster thereafter.

### Plasmid sharing net file inside genus _Acinetobacter_
Here we offer you 3 file describing the plasmid sharing net we discussed in our manuscript. All plasmids were predicted by PlasT.
1. Aci.node.tsv
   Basic node information about involved plasmids types and species of genus _Acinetobacter_
2. Aci.rate.tsv
   PT Carring rate for each species
3. Aci.node.importance.csv
   An addtional file. For each node, we have estimated its importance inside the sharing net by Gephi.
