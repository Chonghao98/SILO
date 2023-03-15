# SILO: Detection-of-short-identity-by-descent-by-incorporating-low-frequency-variants
SILO is an IBD detection method that is capable of identifying short IBD segments.
# The hyperparameters of SILO
--winsize (or -w, type=int): the window size.  
--length (or -l, type=float): the length of block.  
--error_common (or -ec, type=float): the genotype error of common variants.  
--error_lowf (or -el, type=float, default=1e-5): the genotype error of low-frequency variants.  
--threshold (or -t, type=float,default=3): the threshold for LLR score.  
--mode (type=str, default='outer'): input 'inner' or 'outer', which stands for computing inner log-likelihood ratio or computing outer log-likelihood ratio, respectively.  
--union (type=int, default=2): calculate scores for low frequency variants of a pair of individuals that 1. either one carries minor alleles or 2. both two individuals carry minor alleles. Input 1 for case 1, or 2 for case 2.  
--density (type=float,default=125): the minimum number of common SNPs in a block length of 1 cM.  
--bin_length (type=float, default=2): the length of bins.  
--N_simIBD (type=int,default=1000): the number of simulated IBD pairs.  
--N_simnonIBD (type=int,default=1000): the number of simulated non-IBD pairs.  
--negative_ratio_thres (type=float,default=1/10): the threshold for the negative ratio in generating IBD regions based on low frequency variants.  
--negative_count_thres (type=int,default=1): the threshold for the negative count in generating IBD regions based on low frequency variants.  
--pseudo (type=float,default=0.01): the pseudo-count used in empirical distribution for smoothing.  
--threads (type=int,default=10): the number of threads used.  
--train_common (type=str): the path and filename (prefix) of common variants in the training set.  
--train_lowf (type=str): the path and filename (prefix) of low-frequency variants in the training set.  
--test_common (type=str): the path and filename (prefix) of common variants in the test set.  
--test_lowf (type=str): the path and filename (prefix) of low-frequency variants in the test set.  
--output (type=str): the path and filename (prefix) of output.  
# Getting started
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
