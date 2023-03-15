# SILO
SILO is an IBD detection method that is capable of identifying short IBD segments.
## Usage
```
python3 run_SILO.py --winsize INT --length FLOAT --error_common FLOAT --error_lowf FLOAT --threshold FLOAT --mode STR --union INT  
--density FLOAT --bin_length FLOAT --N_simIBD INT --N_simnonIBD INT --negative_ratio_thres FLOAT --gative_count_thres INT  
--pseudo FLOAT --threads INT --train_common STR --train_lowf STR --test_common STR --test_lowf STR --output STR  

Hyperparameters:
  -w, --winsize: the window size.  
  -l, --length: the length of block.  
  -ec, --error_common: the genotype error of common variants. The default value is 0.005.  
  -el, --error_lowf: the genotype error of low-frequency variants. The default value is 1e-5.  
  -t, --threshold: the threshold for LLR score. The default value is 3.  
  --mode: input 'inner' or 'outer', which stands for computing inner log-likelihood ratio or computing outer log-likelihood ratio,  
  respectively. The default value is 'outer'.  
  --union: calculate scores for low frequency variants of a pair of individuals that 1. either one carries minor alleles or 2.  
  Both two individuals carry minor alleles. Input 1 for case 1, or 2 for case 2. The default value is 2.  
  --density: the minimum number of common SNPs in a block length of 1 cM. The default value is 125.  
  --bin_length: the length of bins. The default value is 2.  
  --N_simIBD: the number of simulated IBD pairs. The default value is 1000.  
  --N_simnonIBD: the number of simulated non-IBD pairs. The default value is 1000.  
  --negative_ratio_thres: the threshold for the negative ratio in generating IBD regions based on low frequency variants. The  
  default value is 0.1.  
  --negative_count_thres: the threshold for the negative count in generating IBD regions based on low frequency variants. The  
  default value is 1.  
  --pseudo: the pseudo-count used in empirical distribution for smoothing. The default value is 0.01.  
  --threads: the number of threads used. The default value is 10.  
  --train_common: the path and filename (prefix) of common variants of the training set.  
  --train_lowf: the path and filename (prefix) of low-frequency variants of the training set.  
  --test_common: the path and filename (prefix) of common variants of the test set.  
  --test_lowf: the path and filename (prefix) of low-frequency variants of the test set.  
  --output: the path and filename (prefix) of output.  
```
## File format
### Input
Common variants of the training set: .hap, .map, .frq  
Common variants of the testing set: .tped, .tfam  
Low frequency variants of the training set: .map, .frq, .frq.counts  
Low frequency variants of the testing set: .tped  
All file formats except .hap could be found at https://www.cog-genomics.org/plink/2.0/formats#haps.  
The file format of .hap is as follow:  
```
haplotype1 haplotype2 haplotype3 haplotype4
1 0 0 1
1 1 1 0
0 0 -1 1
```
'0' stands for the minor allele, and '1' stands for the major allele. '-1' stabds for the missing value. Each column in the .hap is a haplotype. The first two columns are the haplotypes for the first person, and the third and fourth columns are the haplotypes for the second person. Each row is a SNP, the corresponding order is the same as the order in .map file. Each column is seperated by a space. 
## Getting started
Download the IBD_functions.py and run_SILO.py and put them in one folder. run_SILO.py will load the functions defined in IBD_functions.py.  
Below is an example for running SILO:
```
python3 run_SILO.py 
--winsize 10  
--length 3  
--error_common 0.005  
--error_lowf 1e-5  
--threads 10  
--train_common /PATH(COMMON VARIANTS IN TRAINING SET)  
--train_lowf /PATH(LOW FREQUENCY VARIANTS IN TRAINING SET)  
--test_common /PATH(COMMON VARIANTS IN TESTING SET)  
--test_lowf /PATH(LOW FREQUENCY VARIANTS IN TESTING SET)  
--output /PATH(OUTPUT)  
```
