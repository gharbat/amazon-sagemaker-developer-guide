# XGBoost Hyperparameters<a name="xgboost_hyperparameters"></a>

The Amazon SageMaker XGBoost algorithm is an implementation of the open\-source XGBoost package\. Currently Amazon SageMaker supports version 0\.72\. For more detail about hyperparameter configuration for this version of XGBoost, see [Release 0\.72 XGBoost Parameters](https://xgboost.readthedocs.io/en/release_0.72/parameter.html)\.


| Parameter Name | Description | 
| --- | --- | 
| num\_class | The number of classes\. **Required** if `objective` is set to *multi:softmax* or *multi:softprob*\. Valid values: integer  | 
| num\_round | The number of rounds to run the training\. **Required** Valid values: integer  | 
| alpha | L1 regularization term on weights\. Increasing this value makes models more conservative\. **Optional** Valid values: float Default value: 1  | 
| base\_score | The initial prediction score of all instances, global bias\. **Optional** Valid values: float Default value: 0\.5  | 
| booster | Which booster to use\. The `gbtree` and `dart` values use a tree\-based model, while `gblinear` uses a linear function\. **Optional** Valid values: String\. One of `gbtree`, `gblinear`, or `dart`\. Default value: `gbtree`  | 
| colsample\_bylevel | Subsample ratio of columns for each split, in each level\. **Optional** Valid values: Float\. Range: \[0,1\]\. Default value: 1  | 
| colsample\_bytree | Subsample ratio of columns when constructing each tree\. **Optional** Valid values: Float\. Range: \[0,1\]\. Default value: 1 | 
| csv\_weights | When this flag is enabled, XGBoost differentiates the importance of instances for csv input by taking the second column \(the column after labels\) in training data as the instance weights\. **Optional** Valid values: 0 or 1 Default value: 0  | 
| early\_stopping\_rounds | The model trains until the validation score stops improving\. Validation error needs to decrease at least every `early_stopping_rounds` to continue training\. Amazon SageMaker hosting uses the best model for inference\. **Optional** Valid values: integer Default value: \-  | 
| eta | Step size shrinkage used in updates to prevent overfitting\. After each boosting step, you can directly get the weights of new features\. The `eta` parameter actually shrinks the feature weights to make the boosting process more conservative\. **Optional** Valid values: Float\. Range: \[0,1\]\. Default value: 0\.3  | 
| eval\_metric | Evaluation metrics for validation data\. A default metric is assigned according to the objective:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/sagemaker/latest/dg/xgboost_hyperparameters.html) For a list of valid inputs, see [XGBoost Parameters](https://github.com/dmlc/xgboost/blob/master/doc/parameter.rst)\. **Optional** Valid values: string Default value: Default according to objective\.  | 
| gamma | Minimum loss reduction required to make a further partition on a leaf node of the tree\. The larger, the more conservative the algorithm is\. **Optional** Valid values: Float\. Range: \[0,∞\)\. Default value: 0  | 
| grow\_policy | Controls the way that new nodes are added to the tree\. Currently supported only if `tree_method` is set to `hist`\. **Optional** Valid values: String\. Either `depthwise` or `lossguide`\. Default value: `depthwise`  | 
| lambda | L2 regularization term on weights\. Increasing this value makes models more conservative\. **Optional** Valid values: float Default value: 1  | 
| lambda\_bias | L2 regularization term on bias\. **Optional** Valid values: Float\. Range: \[0\.0, 1\.0\]\. Default value: 0  | 
| max\_bin | Maximum number of discrete bins to bucket continuous features\. Used only if `tree_method` is set to `hist`\.  **Optional** Valid values: integer Default value: 256  | 
| max\_delta\_step | Maximum delta step allowed for each tree's weight estimation\. When a positive integer is used, it helps make the update more conservative\. The preferred option is to use it in logistic regression\. Set it to 1\-10 to help control the update\.  **Optional** Valid values: Integer\. Range: \[0,∞\)\. Default value: 0  | 
| max\_depth | Maximum depth of a tree\. Increasing this value makes the model more complex and likely to be overfitted\. 0 indicates no limit\. A limit is required when `grow_policy`=`depth-wise`\. **Optional** Valid values: Integer\. Range: \[0,∞\) Default value: 6  | 
| max\_leaves | Maximum number of nodes to be added\. Relevant only if `grow_policy` is set to `lossguide`\. **Optional** Valid values: integer Default value: 0  | 
| min\_child\_weight | Minimum sum of instance weight \(hessian\) needed in a child\. If the tree partition step results in a leaf node with the sum of instance weight less than `min_child_weight`, the building process gives up further partitioning\. In linear regression models, this simply corresponds to a minimum number of instances needed in each node\. The larger the algorithm, the more conservative it is\. **Optional** Valid values: Float\. Range: \[0,∞\)\. Default value: 1  | 
| normalize\_type | Type of normalization algorithm\. **Optional** Valid values: Either *tree* or *forest*\. Default value: *tree*  | 
| nthread | Number of parallel threads used to run *xgboost*\. **Optional** Valid values: integer Default value: Maximum number of threads\.  | 
| objective | Specifies the learning task and the corresponding learning objective\. Examples: `reg:linear`, `reg:logistic`, `multi:softmax`\. For a full list of valid inputs, please refer to [XGBoost Parameters](https://github.com/dmlc/xgboost/blob/master/doc/parameter.rst)\. **Optional** Valid values: string Default value: `reg:linear`  | 
| one\_drop | When this flag is enabled, at least one tree is always dropped during the dropout\. **Optional** Valid values: 0 or 1 Default value: 0  | 
| process\_type | The type of boosting process to run\. **Optional** Valid values: String\. Either `default` or `update`\. Default value: `default`  | 
| rate\_drop | The dropout rate that specifies the fraction of previous trees to drop during the dropout\. **Optional** Valid values: Float\. Range: \[0\.0, 1\.0\]\. Default value: 0\.0  | 
| refresh\_leaf | This is a parameter of the 'refresh' updater plugin\. When set to `true` \(1\), tree leaves and tree node stats are updated\. When set to `false`\(0\), only tree node stats are updated\. **Optional** Valid values: 0/1 Default value: 1  | 
| sample\_type | Type of sampling algorithm\. **Optional** Valid values: Either `uniform` or `weighted`\. Default value: `uniform`  | 
| scale\_pos\_weight | Controls the balance of positive and negative weights\. It's useful for unbalanced classes\. A typical value to consider: `sum(negative cases)` / `sum(positive cases)`\. **Optional** Valid values: float Default value: 1  | 
| seed | Random number seed\. **Optional** Valid values: integer Default value: 0  | 
| silent | 0 means print running messages, 1 means silent mode\. Valid values: 0 or 1 **Optional** Default value: 0  | 
| sketch\_eps | Used only for approximate greedy algorithm\. This translates into O\(1 / `sketch_eps`\) number of bins\. Compared to directly select number of bins, this comes with theoretical guarantee with sketch accuracy\. **Optional** Valid values: Float, Range: \[0, 1\]\. Default value: 0\.03  | 
| skip\_drop | Probability of skipping the dropout procedure during a boosting iteration\. **Optional** Valid values: Float\. Range: \[0\.0, 1\.0\]\. Default value: 0\.0  | 
| subsample | Subsample ratio of the training instance\. Setting it to 0\.5 means that XGBoost randomly collects half of the data instances to grow trees\. This prevents overfitting\. **Optional** Valid values: Float\. Range: \[0,1\]\. Default value: 1  | 
| tree\_method | The tree construction algorithm used in XGBoost\. **Optional** Valid values: One of `auto`, `exact`, `approx`, or `hist`\. Default value: `auto`  | 
| tweedie\_variance\_power | Parameter that controls the variance of the Tweedie distribution\. **Optional** Valid values: Float\. Range: \(1, 2\)\. Default value: 1\.5  | 
| updater | A comma\-separated string that defines the sequence of tree updaters to run\. This provides a modular way to construct and to modify the trees\. For a full list of valid inputs, please refer to [XGBoost Parameters](https://github.com/dmlc/xgboost/blob/master/doc/parameter.rst)\. **Optional** Valid values: comma\-separated string\. Default value: `grow_colmaker`, prune  | 