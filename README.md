# Hansa-toy-version
Using metrics like Gribskov score, Probability of finding mutant/wild type amino acid at a
given position, Buried/exposed amino acid data and structure of amino acid
[helix/coil/other], I tried to create a basic version of Hansa, a method that uses SVM to
classify mutations into neutral and deleterious
For this analysis I used five sequences: I used the human protein Sodium- and chloridedependent glycine transporter 2 protein [UniProt ID Q9Y345], its rat and mouse ortholog
[obtained from BLAST Aligner], and then for the fourth protein, I inserted neutral mutations
and in the last sequence I inserted deleterious mutations
The data for these mutations for this particular protein was obtained form the HumVar.tar.gz
dataset from the Harvard university Database. The hansa paper also has used this dataset
Like Hansa, I have tried calculating Probability(Wild type), Probability(mutant), Difference
b/w both the probabilities, Gribskov score for the position’s mutation, buried/exposed data
[ 10% RSA < exposed], and structure [coil/helix/strand]. The structural data for this protein
was obtained from "https://services.healthtech.dtu.dk/cgibin/webface2.cgi?jobid=6A0C46C300279D39CD285359&wait=20" webpage.
I used SVM, and Cost parameter as 0.1, which affects the strictness of the model
I also converted the data into numerical values to be fed into the model
Here, the acess column is the Buried/exposed where 0 is exposed and 1 is buried, strct is the
column for structure[helix/strand]
The 'position' column is the position of the given mutation in the amino acid sequence [0
indexing]
The 'score' column is the Gribskov score, and the 'diff' is the difference between the
probability of a wild type amino acid and mutation amino acid.
To be fed into the SVM model, wild type and mutation column data were converted into
numerical values, with a reference vector of [A, R, N, D, C, Q, E, G, H, I, L, K, M, F, P, S, T, W, Y,
V]
Therefore the final data fed into the model was
I had used 7 neutral mutations and 6 deleterious mutations, the model predicted 7/7 neutral
mutations and predicted 4/6 deleterious mutations correctly. There were two false positives
for neutral.
There are significant drawbacks to my pipeline:
1) The training dataset is very small, not large enough to arrive at statistically significant
analyses.
2) The dataset does not contain equal amount of information for both types.
This toy version of Hansa was thus implemented.
3) This pipeline is not reproducible on other datasets.
I also used the internet and AI to help me understand the concepts in the paper and to help
me debug the code.
