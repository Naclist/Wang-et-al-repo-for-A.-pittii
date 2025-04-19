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
Here we offer you 4 file describing the plasmid sharing net we discussed in our manuscript. All plasmids were predicted by PlasT.
1. Aci.node.tsv
   Basic node information about involved plasmids types and species of genus _Acinetobacter_
2. Aci.rate.tsv
   PT Carring rate for each species
3. Aci.node.importance.csv
   An addtional file. For each node, we have estimated its importance inside the sharing net by Gephi.
4. PT_712seq.zip
   A compressed package containing the PT_712 sequence from genus _Acinetobacter_
### Machine learning for genomarker identification

To discriminate the HC1100-specified associated genes, we concluded a gene presence/absence matrix. We employed a module of sci-kit learn package‘RandomForestClassifer' to train a model from this matrix (initial parameters: n_estimators = 1000, random_state = 42). We also used the 3-fold cross-validation to estimate the accuracy of this model. The importance of each feature was exported by Random Forest model’s attribution API. 

ML.py is a standalone python pipeline for our machine learning classifier, which can be reproducted by running Python codes below:

Train the model (we use -n parameter to define the numbers of features with the highest importance for second validation, here default value of 20 is selecetd for convenience)
~~~
$ python ML.py learn -m/--matrix pangenome.content.0819tab.transposed.titled.hc1100.modi -t/--target group -c/--classifier randomF -o/--output_model -p/--prefix [Prefix]
~~~
This will generate 4 result tab-separated matrixs: 
~~~
[Prefix].importance
[Prefix].selected_20.importance
[Prefix].selected_20.distribution
[Prefix].model.pkl
~~~
F1 score, AUC curve and the accuraccy of this model will printed in the screen.

