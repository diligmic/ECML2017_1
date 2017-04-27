# ECML2017_1
Code and data to replicate the experiments presented in the paper "Learning Lukasiewicz Logic Fragments by Quadratic Programming"

# Experiments on Image Classification
1) Uncompress the software package
   tar xvfz SBRS_7.0_20170404.tar.gz  
   cd SBRS_7.0/Train  
   make clean  
   make
   
 2) Run the Baseline  
    SBRS_7.0/Train/sbr_train --transductive --training_data_file=dataSBRStransductive.txt --training_examples_file=trainTransductiveExamplesSBRS_all_pred.txt --validation_examples_file=validTransductiveExamplesSBRS_all_pred.txt --test_examples_file=testTransductiveExamplesSBRS_all_pred.txt --predicates_file=predicatesWinstonRecognizer_LEARN_all.txt --rules_file= --max_iterations=300 --lambda_labeled_values=1 --lambda_regularization_values=0.1 --lambda_constraint_values=0.1,1 --learning_rate=0.001 --max_learning_rate=0.1 --learning_type=RGD --function_type=KERNEL_MACHINE --squashing_function_type=SIGMOID --kernel_type=GAUSSIAN --gram_matrix_normalization_by_row_sum --output_dir=baseline --input_dir=.
    
 3) Run the experiments  
    Train/sbr_train --transductive --training_data_file=dataSBRStransductive.txt --training_examples_file=trainTransductiveExamplesSBRS_all_pred.txt --validation_examples_file=validTransductiveExamplesSBRS_all_pred.txt --test_examples_file=testTransductiveExamplesSBRS_all_pred.txt --predicates_file=predicatesWinstonRecognizer_LEARN_all.txt --rules_file=rulesWinstonRecognizer_all_wluk_no_residuum.txt --max_iterations=300 --iteration_start_constraints=200 --lambda_labeled_values=1 --lambda_regularization_values=0.1 --lambda_constraint_values=0.1,1 --learning_rate=0.001 --max_learning_rate=0.1 --learning_type=RGD --function_type=KERNEL_MACHINE --squashing_function_type=SIGMOID --kernel_type=GAUSSIAN --gram_matrix_normalization_by_row_sum --output_dir=convex_luk --input_dir=transductive
    
 4) Eval  
    cat baseline/ll1-*/results/test_results.dat | SBRS_7.0/scripts/proteins/test.pl
    cat convex_luk/ll1-*/results/test_results.dat | SBRS_7.0/scripts/proteins/test.pl
    
    
    
# Toy Problem
1) Open the Matlab file training_sets.mat to load the training sets used in the paper.

2) Run the script ex1.m to get the optimal solution to the problem. From this file you can manage the different constraints you want to take into account in the learning problem.

3) Run the script print.m to visualize the task functions you got which best fit the constraints.

Instructions and useful comments are reported on the top of such scripts.
