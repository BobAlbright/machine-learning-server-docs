--- 
 
# required metadata 
title: "Parallel External Memory Algorithm for Classification and Regression Decision Forests" 
description: "Fit classification and regression decision forests on an ‘.xdf’ file or" 
keywords: "M, I, S, S, I, N, G,  , K, E, Y, W, O, R, D, S" 
author: "Microsoft Corporation Microsoft Technical Support" 
manager: "" 
<<<<<<< HEAD
ms.date: "06/26/2017" 
=======
ms.date: "06/27/2017" 
>>>>>>> heidist-revoscalepy
ms.topic: "reference" 
ms.prod: "microsoft-r" 
ms.service: "" 
ms.assetid: "" 
 
# optional metadata 
ROBOTS: "" 
audience: "" 
ms.devlang: "" 
ms.reviewer: "" 
ms.suite: "" 
ms.tgt_pltfrm: "" 
ms.technology: "r-server" 
ms.custom: "" 
 
---

<<<<<<< HEAD
# rx_dforest
=======
## rx_dforest


### Usage
>>>>>>> heidist-revoscalepy



```
revoscalepy.functions.RxDTree.rx_dforest(formula, data, output_file=None, write_model_vars=False, overwrite=False, pweights=None, fweights=None, cost=None, min_split=None, min_bucket=None, max_depth=10, cp=0, max_compete=0, max_surrogate=0, use_surrogate=2, surrogate_style=0, n_tree=10, m_try=None, replace=True, cutoff=None, strata=None, sample_rate=None, importance=False, seed=None, compute_cp_table=False, compute_oob_error=1, max_num_bins=None, max_unordered_levels=32, remove_missings=False, use_sparse_cube=False, find_splits_in_parallel=True, row_selection=None, transforms=None, transform_objects=None, transform_function=None, transform_variables=None, transform_packages=None, transform_environment=None, blocks_per_read=1, report_progress=2, verbose=0, compute_context=None, xdf_compression_level=1, **kwargs)
```




<<<<<<< HEAD
## Description
=======
### Description
>>>>>>> heidist-revoscalepy

Fit classification and regression decision forests on an ‘.xdf’ file or
data frame for small or large data using parallel external memory algorithm.


<<<<<<< HEAD
## Parameters


### formula
=======
### Arguments


##### formula
>>>>>>> heidist-revoscalepy

formula as described in rxFormula. Currently, formula
functions are not supported.


<<<<<<< HEAD
### data
=======
##### data
>>>>>>> heidist-revoscalepy

either a data source object, a character string specifying a
‘.xdf’ file, or a data frame object.


<<<<<<< HEAD
### output_file
=======
##### output_file
>>>>>>> heidist-revoscalepy

either an RxXdfData data source object or a character
string specifying the ‘.xdf’ file for storing the resulting node indices.
If None, then no node indices are stored to disk. If the input data is a
data frame, the node indices are returned automatically. If rowSelection is
specified and not None, then outFile cannot be the same as the data since
the resulting set of node indices will generally not have the same number
of rows as the original data source.


<<<<<<< HEAD
### write_model_vars
=======
##### write_model_vars
>>>>>>> heidist-revoscalepy

logical value. If True, and the output file is
different from the input file, variables in the model will be written to
the output file in addition to the node numbers. If variables from the
input data set are transformed in the model, the transformed variables will
also be written out.


<<<<<<< HEAD
### overwrite
=======
##### overwrite
>>>>>>> heidist-revoscalepy

logical value. If True, an existing outFile with an
existing column named outColName will be overwritten.


<<<<<<< HEAD
### pweights
=======
##### pweights
>>>>>>> heidist-revoscalepy

character string specifying the variable of numeric values
to use as probability weights for the observations.


<<<<<<< HEAD
### fweights
=======
##### fweights
>>>>>>> heidist-revoscalepy

character string specifying the variable of integer values
to use as frequency weights for the observations.


<<<<<<< HEAD
### method
=======
##### method
>>>>>>> heidist-revoscalepy

character string specifying the splitting method. Currently,
only “class” or “anova” are supported. The default is “class” if the
response is a factor, otherwise “anova”.


<<<<<<< HEAD
### parms
=======
##### parms
>>>>>>> heidist-revoscalepy

optional list with components specifying additional
parameters for the “class” splitting method, as follows:

prior: a vector of prior probabilities. The priors must be positive and
    sum to 1. The default priors are proportional to the data counts.

loss: a loss matrix, which must have zeros on the diagonal and positive
    off-diagonal elements. By default, the off-diagonal elements are set to 1.

split: the splitting index, either gini (the default) or information.

If parms is specified, any of the components can be specified or
    omitted. The defaults will be used for missing components.


<<<<<<< HEAD
### cost
=======
##### cost
>>>>>>> heidist-revoscalepy

a vector of non-negative costs, containing one element for
each variable in the model. Defaults to one for all variables. When
deciding which split: to choose, the improvement on splitting on a variable
is divided by its cost.


<<<<<<< HEAD
### min_split
=======
##### min_split
>>>>>>> heidist-revoscalepy

the minimum number of observations that must exist in a
node before a split is attempted. By default, this is sqrt(num of obs). For
non-XDF data sources, as (num of obs) is unknown in advance, it is wisest
to specify this argument directly.


<<<<<<< HEAD
### min_bucket
=======
##### min_bucket
>>>>>>> heidist-revoscalepy

the minimum number of observations in a terminal node
(or leaf). By default, this is minSplit/3.


<<<<<<< HEAD
### cp
=======
##### cp
>>>>>>> heidist-revoscalepy

numeric scalar specifying the complexity parameter. Any split
that does not decrease overall lack-of-fit by at least cp is not attempted.


<<<<<<< HEAD
### max_compete
=======
##### max_compete
>>>>>>> heidist-revoscalepy

the maximum number of competitor splits retained in the
output. These are useful model diagnostics, as they allow you to compare
splits in the output with the alternatives.


<<<<<<< HEAD
### max_surrogate
=======
##### max_surrogate
>>>>>>> heidist-revoscalepy

the maximum number of surrogate splits retained in
the output. See the Details for a description of how surrogate splits are
used in the model fitting. Setting this to 0 can greatly improve the
performance of the algorithm; in some cases almost half the computation
time is spent in computing surrogate splits.


<<<<<<< HEAD
### use_surrogate
=======
##### use_surrogate
>>>>>>> heidist-revoscalepy

an integer specifying how surrogates are to be used
in the splitting process:
0: display-only; observations with a missing value for the primary

    split variable are not sent further down the tree.

1: use surrogates,in order, to split observations missing the primary
    split variable. If all surrogates are missing, the observation is not
    split.

2: use surrogates, in order, to split observations missing the primary
    split variable. If all surrogates are missing or maxSurrogate=0, send
    the observation in the majority direction.

The 0 value corresponds to the behavior of the tree function, and 2
    (the default) corresponds to the recommendations of Breiman et al.


<<<<<<< HEAD
### surrogate_style
=======
##### surrogate_style
>>>>>>> heidist-revoscalepy

an integer controlling selection of a best
surrogate. The default, 0, instructs the program to use the total number of
correct classifications for a potential surrogate, while 1 instructs the
program to use the percentage of correct classification over the
non-missing values of the surrogate. Thus, 0 penalizes potential surrogates
with a large number of missing values.


<<<<<<< HEAD
### n_tree
=======
##### n_tree
>>>>>>> heidist-revoscalepy

a positive integer specifying the number of trees to grow.


<<<<<<< HEAD
### m_try
=======
##### m_try
>>>>>>> heidist-revoscalepy

a positive integer specifying the number of variables to
sample as split candidates at each tree node. The default values is
sqrt(num of vars) for classification and (num of vars)/3 for regression.


<<<<<<< HEAD
### replace
=======
##### replace
>>>>>>> heidist-revoscalepy

a logical value specifying if the sampling of observations
should be done with or without replacement.


<<<<<<< HEAD
### cutoff
=======
##### cutoff
>>>>>>> heidist-revoscalepy

(Classification only) a vector of length equal to the number
of classes specifying the dividing factors for the class votes. The default
is 1/(num of classes).


<<<<<<< HEAD
### strata
=======
##### strata
>>>>>>> heidist-revoscalepy

a character string specifying the (factor) variable to use
for stratified sampling.


<<<<<<< HEAD
### sample_rate
=======
##### sample_rate
>>>>>>> heidist-revoscalepy

a scalar or a vector of positive values specifying the
percentage(s) of observations to sample for each tree:
for unstratified sampling: a scalar of positive value specifying the

    percentage of observations to sample for each tree. The default is 1.0
    for sampling with replacement (i.e., replace=True) and 0.632 for
    sampling without replacement (i.e., replace=False).

for stratified sampling: a vector of positive values of length equal to
    the number of strata specifying the percentages of observations to
    sample from the strata for each tree.


<<<<<<< HEAD
### importance
=======
##### importance
>>>>>>> heidist-revoscalepy

a logical value specifying if the importance of
predictors should be assessed.


<<<<<<< HEAD
### seed
=======
##### seed
>>>>>>> heidist-revoscalepy

an integer that will be used to initialize the random number
generator. The default is random. For reproducibility, you can specify the
random seed either using set.seed or by setting this seed argument as part
of your call.


<<<<<<< HEAD
### compute_oob_error
=======
##### compute_oob_error
>>>>>>> heidist-revoscalepy

an integer specifying whether and how to compute
the prediction error for out-of-bag samples:
<0: never. This option may reduce the computation time.
=0: only once for the entire forest.
>0: once for each addition of a tree. This is the default.


<<<<<<< HEAD
### max_num_bins
=======
##### max_num_bins
>>>>>>> heidist-revoscalepy

the maximum number of bins to use to cut numeric data.
The default is min(1001, max(101, sqrt(num of obs))). For non-XDF data
sources, as (num of obs) is unknown in advance, it is wisest to specify
this argument directly. If set to 0, unit binning will be used instead of
cutting. See the ‘Details’ section for more information.


<<<<<<< HEAD
### max_unordered_levels
=======
##### max_unordered_levels
>>>>>>> heidist-revoscalepy

the maximum number of levels allowed for an
unordered factor predictor for multiclass (>2) classification.


<<<<<<< HEAD
### remove_missings
=======
##### remove_missings
>>>>>>> heidist-revoscalepy

logical value. If True, rows with missing values
are removed and will not be included in the output data.


<<<<<<< HEAD
### use_sparse_cube
=======
##### use_sparse_cube
>>>>>>> heidist-revoscalepy

logical value. If True, sparse cube is used.


<<<<<<< HEAD
### find_splits_in_parallel
=======
##### find_splits_in_parallel
>>>>>>> heidist-revoscalepy

logical value. If True, optimal splits for
each node are determined using parallelization methods; this will typically
speed up computation as the number of nodes on the same level is increased.


<<<<<<< HEAD
### row_selection
=======
##### row_selection
>>>>>>> heidist-revoscalepy

None. Not currently supported, reserved for future
use.


<<<<<<< HEAD
### transforms
=======
##### transforms
>>>>>>> heidist-revoscalepy

None. Not currently supported, reserved for future use.


<<<<<<< HEAD
### transform_objects
=======
##### transform_objects
>>>>>>> heidist-revoscalepy

None. Not currently supported, reserved for future use.


<<<<<<< HEAD
### transform_function
=======
##### transform_function
>>>>>>> heidist-revoscalepy

variable transformation function. The variables used
in the transformation function must be specified in transformVars if they
are not variables used in the model. See rxTransform for details.


<<<<<<< HEAD
### transform_variables
=======
##### transform_variables
>>>>>>> heidist-revoscalepy

character vector of input data set variables needed
for the transformation function. See rx_transform for details.


<<<<<<< HEAD
### transform_packages
=======
##### transform_packages
>>>>>>> heidist-revoscalepy

None. Not currently supported, reserved for future use.


<<<<<<< HEAD
### transform_environment
=======
##### transform_environment
>>>>>>> heidist-revoscalepy

None. Not currently supported, reserved for future use.


<<<<<<< HEAD
### blocks_per_read
=======
##### blocks_per_read
>>>>>>> heidist-revoscalepy

number of blocks to read for each chunk of data read from
the data source.


<<<<<<< HEAD
### report_progress
=======
##### report_progress
>>>>>>> heidist-revoscalepy

integer value with options:
0: no progress is reported.
1: the number of processed rows is printed and updated.
2: rows processed and timings are reported.
3: rows processed and all timings are reported.


<<<<<<< HEAD
### verbose
=======
##### verbose
>>>>>>> heidist-revoscalepy

integer value. If 0, no additional output is printed. If 1,
additional summary information is printed.


<<<<<<< HEAD
### compute_context
=======
##### compute_context
>>>>>>> heidist-revoscalepy

a RxComputeContext object for prediction.


<<<<<<< HEAD
### kwargs
=======
##### kwargs
>>>>>>> heidist-revoscalepy

additional parameters


<<<<<<< HEAD
## Returns
=======
### Returns
>>>>>>> heidist-revoscalepy

a rx_dforest_results object of dtree model.


<<<<<<< HEAD
## Author
=======
### Author
>>>>>>> heidist-revoscalepy

Microsoft Corporation [Microsoft Technical Support](https://go.microsoft.com/fwlink/?LinkID=698556&clcid=0x409.md)


<<<<<<< HEAD
## See also


## Example
=======
### See also


### Example
>>>>>>> heidist-revoscalepy



```
import os
from revoscalepy import rx_dforest, rx_import_datasource, RxOptions, RxXdfData
sample_data_path = RxOptions.get_option("sampleDataDir")
ds = RxXdfData(os.path.join(sample_data_path, "kyphosis.xdf"))
kyphosis = rx_import_datasource(input_data = ds)

# classification
formula = "Kyphosis ~ Number + Start"
method = "class"
parms = {'prior': [0.8, 0.2], 'loss': [0, 2, 3, 0], 'split': "gini"}

dforest = rx_dforest(formula, data = kyphosis, pweights = "Age", method = method,
                     parms = parms, cost = [2, 3], max_num_bins = 100, importance = True,
                     n_tree = 3, m_try = 2, sample_rate = 0.5,
                     replace = False, seed = 0, compute_oob_error = 1)

# regression
formula = "Age ~ Number + Start"
method = "anova"
parms = {'prior': [0.8, 0.2], 'loss': [0, 2, 3, 0], 'split': "gini"}

dforest = rx_dforest(formula, data = kyphosis, pweights = "Kyphosis", method = method,
                     parms = parms, cost = [2, 3], max_num_bins = 100, importance = True,
                     n_tree = 3, m_try = 2, sample_rate = 0.5,
                     replace = False, seed = 0, compute_oob_error = 1)
```
