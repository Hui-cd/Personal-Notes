
### Linear Regression
1. Linear regression is a prediction method for regression tasks
2. Definition: Linear regression is a method to predict the relationship between independent variables and dependent variables. 
3. regression tasks - predict variables is numeric 
4. given a dataset with 2 continues variables:
	1. feature x (independent variable)
	2. predicted variables y (dependent variable or target variable) 
5. Goal: Approximate the relationship between these variables with a straight line for given dataset 
#### Fitting a line
1. predict error = actual value - predict value $\epsilon = y_{i} - \hat{y}_i$  
2. Performance index: sum of squared prediction errors (SSE) $SSE = \sum_{i}(y_{i} - \hat{y}_i)^2$
3. our goal is to find a line which minimise SSE
4. Can be solved using the method of the least squares
5. This solution is obtained by minimizing SSE using differential calculate 
$$
b_{1} = \frac{\sum x_iy_{i}- (\sum x_{i}-\sum y_{i})/{n}} {(\sum x_{i}^2 - (\sum x_i^2/n)}
$$
$$
b_{0}= \overline y - b_{1} \overline x
$$#### Coefficient of determination $R^2$ 决定系数
1. $R^2$ measure the goodness of fit of the regression line by the least squared method  
$$ R^{2} = \frac{SSR}{SST}$$
2. SSE - Sum of squared prediction errors  --- actual value – predicted value 
  $$SSE = \sum (y_{i}- \widehat y_i)^2$$
3. SST - Sum of squared total errors --- actual value – mean value
	$$SST = \sum (y_{i}- \overline y_i)^2$$
4. SSR - Sum of squared regression errors --- predicted value – mean value
$$SSR = \sum\limits (\hat y_{i} - \overline y_{i})^2$$
	SST=SSR+SSE
	
5. Values between 0 and 1, the higher the better 
#### Relation $R^2$ and r   r - 相关系数
1. r-correlation coefficient : measures linear relationship between 2 vectors X and Y\
$$ r = corr(X,Y) = \frac{covar(X,Y)}{std(X)std(Y)} = \frac{covar(X,Y)}{\sqrt{ var(x)var(Y)}}$$
2. $r = \sqrt R^2$  , Except for the sign of r, which depends on the direction of the relationship, so  $r = \pm \sqrt R^2$
3. If the value of the correlation coefficient is negative, this indicates that the 2 variables are negatively correlated

#### MAE, MSE and RMSE
1. MAE, MSE and RMSE are other performance measures for evaluating
2. Mean Absolute Error (MAE): $$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$
3. Mean Squared Error (MSE): $$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$
4. Root Mean Squared Error (RMSE): $$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$
#### Exercise 
1. The regression line minimizes the sum of the residuals
	**No, the sum of squared residuals**
2. If all residuals are 0, SST=SSR 
	**If the residuals are 0 =>SSE will be 0; SST=SSR+SSE => SST=SSR**
3. If the value of the correlation coefficient is negative, this indicates that the 2 variables are negatively correlated 
	**True**
4. The value of the correlation coefficient can be calculated given the value of R2
	**False**
5. SSR represents an overall measure of the prediction error on the training set by using the regression
	**No, this is SSE, $R^2$or other measures such as MAE, MSE, RMSE**
### Logistic Regression
1. Logistic regression is a extension of linear regression for classification tasks
2. classification tasks - predict variables is nominal 
3. The equation of the logistic (sigmoidal) curve is: $$ p = \frac{e^{b_0+b_1x}}{1+e^{b_0+b_1x}}$$
4. It gives a value between 0 and 1 that is interpreted as the probability for class membership
5. It uses the **maximum likelihood method** to find the parameters $b_0$ and $b_1$ - the curve that best fits the data
### Overfitting and Regularization
Generalization performance = accuracy on test set
#### Overfitting 
1. high accuracy in training dataset, but have lower accuracy in testing dataset
2. It occurs when we fit a model too closely to the particularities of the training set
3. Various reasons
	1. Issues with the data
		1. Noise in the training data
		2. Training data does not contain enough representative examples – too small
	2. How the algorithm operates
		1.  Some algorithms are more susceptible to overfitting than others 
#### Underfitting 
 1. low accuracy in training dataset and testing dataset 
#### Regularization
1. Regularization means explicitly restricting a model to avoid overfitting 
##### Ridge and Lasso Regression
1. Ridge regression
	1. A regularized version of the standard Linear Regression (LR)
	2. Uses the same equation as LR to make predictions
	3. Minimizes the following cost function:  using L2 regularization $$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}  (\hat y_i- y_{(i)})^2 + \alpha \sum_{j=1}^{m} w_i^2$$
	4. Parameter $\alpha$ controls the trade-off between the performance on the training set and model complexity 
2. Lasso regression
	1. LASSO = Least Absolute Shrinkage and Selection Operator Regression
	2. As Ridge Regression, it adds a regularization term to the cost function but it uses the L1 norm of the regression coefficient vector w $$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}  (\hat y_i- y_{(i)})^2 + \alpha \sum_{j=1}^{m}(|w_i|)$$****