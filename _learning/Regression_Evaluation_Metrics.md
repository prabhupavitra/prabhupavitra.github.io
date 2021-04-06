---
title: "Evaluation Metrics - Regression"
excerpt: "Exploring Machine Learning Evaluation Metrics in Regression tasks"
date:   2021-03-10 22:12:28 -0500
theme : "mint"
---

<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>

<img src="/img/Learning/Teaser/reg-eval-metrics.jpg" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:20px;"> Performance Evaluation Metrics in Machine Learning</span>   

<span style="font-family:Georgia; font-size:16px;"> This article is part of **Machine Learning Evaluation Metrics** series where we cover most prominent machine learning metrics used to evaluate/compare machine learning models. Choosing an appropriate metric is crucial while evaluating machine learning (ML) models. Each metric has its own applications and caveats and are grouped based on the ML problem they address. In this article, we shall discuss the metrics used to evaluate regression.</span>  


<span style="font-family:Georgia; font-size:16px;"> The following list is a overview of how the model evaluation metrics/techniques are classified:</span>  

<span style="font-family:Georgia; font-size:16px;"> 1. **Regression Metrics**</span>   
<span style="font-family:Georgia; font-size:16px;"> 2. Classification Metrics</span>   
<span style="font-family:Georgia; font-size:16px;"> 3. Ranking Metrics</span>   
<span style="font-family:Georgia; font-size:16px;"> 4. Clustering Metrics</span>   
<span style="font-family:Georgia; font-size:16px;"> 5. Statistical Metrics</span> 
<span style="font-family:Georgia; font-size:16px;"> 5. Other Model Evaluation Techniques</span> 

### RMSE

<span style="font-family:Georgia; font-size:16px;">Root mean squared error (RMSE) is a quantifiable measure to check how the model's predictions stack up against the actual outcome for regression tasks. It is defined as the square root of the average squared distance between the actual outcome and the predictions:</span>      

$$ RMSE = \sqrt{\frac {1}{N} \sum_{u,i}{(\hat{y_i} - y_i)^2}} $$   

<span style="font-family:Georgia; font-size:16px;">
where $N$ is the number of observations, $\hat{y_i}$ is the predicted value and $y_i$ is the actual value.</span>    

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     
- <span style="font-family:Georgia; font-size:16px;"> Easy to optimize  </span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     
- <span style="font-family:Georgia; font-size:16px;"> Less intuitive to understand;  </span>     
- <span style="font-family:Georgia; font-size:16px;"> Sensitive to outliers;  </span>     

<span style="font-family:Georgia; font-size:18px;">**When to use RMSE?**</span>     
 <span style="font-family:Georgia; font-size:16px;"> Use RMSE to evaluate your regression model, when the error is evenly distributed across the dataset or for error terms that follow a normal distribution. Since its computationally efficient, its a loss metric of choice when hyperparameter tuning or batch training a deep neural network.</span>   

### MAE

<span style="font-family:Georgia; font-size:16px;"> Mean Absolute Error(MAE) is a loss function used for regression tasks and is defined as the sum of absolute differences between our target and predicted variables. </span>   

$$MAE = \frac {1}{N} \sum_{i=1}^{N}{|\hat{y_i} - y_i|}$$     

<span style="font-family:Georgia; font-size:16px;">
where $N$ is the number of observations, $\hat{y_i}$ is the predicted value and $y_i$ is the actual value.</span>   

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     
- <span style="font-family:Georgia; font-size:16px;"> Easy to understand;  </span>     
- <span style="font-family:Georgia; font-size:16px;"> Robust to outliers;  </span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>   
- <span style="font-family:Georgia; font-size:16px;"> MAE with absolute value calculation is not differentiable globally, and hence not easy to optimize.   </span>     

<span style="font-family:Georgia; font-size:18px;">**When to use MAE?**</span>   
<span style="font-family:Georgia; font-size:16px;"> If your use case consists of dataset with large outliers, RMSE will be much larger than MAE. Using MAE will be appropriate in such cases.</span>   

### Quantile of Errors   

<span style="font-family:Georgia; font-size:16px;"> Quantile of errors, also known as the residual quantiles play a vital role in inspecting statistical models. It is useful in examining models like the normal linear regression, because we can expect that the residuals are normally distributed and have equal variance. In non-normal regression situations, such as logistic regression or log-linear analysis, the residual quantiles are practically of no use. </span>   

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>   
- <span style="font-family:Georgia; font-size:16px;"> Robust to outliers;  </span>     
- <span style="font-family:Georgia; font-size:16px;"> Useful for examining normal linear regression models;  </span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     
- <span style="font-family:Georgia; font-size:16px;"> Not applicable in case of non-normal regression situations;  </span>     

<span style="font-family:Georgia; font-size:18px;">**When to use Residual Quantiles?**</span>     
<span style="font-family:Georgia; font-size:16px;"> Use quantiles to evaluate your statistical models, when the distribution is normal. </span>   

### MAPE

<span style="font-family:Georgia; font-size:16px;"> The mean absolute percentage error(MAPE), also known as mean absolute percentage deviation (MAPD) is one of the most widely used measures of forecast accuracy and is expressed as a ratio defined by the formula: </span>   

$$MAPE = \frac {1}{n} \sum_{t=1}^{n}\left |{\frac{A_t - F_t}{A_t}}\right |$$     

<span style="font-family:Georgia; font-size:16px;">
where $A_t$ is the Actual value, $F_t$ is the forecast value. The MAPE is also sometimes reported as a percentage, which is the above equation multiplied by 100. </span>   

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>  
- <span style="font-family:Georgia; font-size:16px;"> THey are dimensionless and easy to interpret;  </span>     
- <span style="font-family:Georgia; font-size:16px;"> It is scale-independent and can apply easily to both high and low volume products;  </span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>  
- <span style="font-family:Georgia; font-size:16px;"> MAPE produces infinite or undefined values for zero or close-to-zero actual values</span>    
- <span style="font-family:Georgia; font-size:16px;"> MAPE is asymmetric, it imposes a larger penalty for negative errors than for positive errors.</span>    
- <span style="font-family:Georgia; font-size:16px;">MAPE assumes that the unit of measurement of the variable has a meaningful zero value. For instance, it should not be used to calculate the accuracy of a temperature forecast since it can take arbitrary zero value. </span>   
- <span style="font-family:Georgia; font-size:16px;">MAPE is not differentiable everywhere, and it can cause issues when used as an optimization criterion.</span>   

<span style="font-family:Georgia; font-size:18px;">**When to use MAPE?**</span>     
<span style="font-family:Georgia; font-size:16px;"> MAPE is a good measure for assessing demand volatility, comparing overall process outcome, Although MAPE is used extensively in forecasting accuracy, it is advised to use it in conjunction with other metrics . Additionally, there are various alternative measures to fix the shortcomings of MAPE. These include symmetric mean absolute percentage error (SMAPE), mean absolute proportional error (MASE), average direction accuracy (MDA), weighted MAPE (WMAPE) etc. </span>   

### RMSLE

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     

<span style="font-family:Georgia; font-size:18px;">**Applications**</span>     

### RRSE

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     

<span style="font-family:Georgia; font-size:18px;">**Applications**</span>     

### RAE

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     

<span style="font-family:Georgia; font-size:18px;">**Applications**</span>     

### R-Squared

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     

<span style="font-family:Georgia; font-size:18px;">**Applications**</span>     

### Adjusted R-Squared

<span style="font-family:Georgia; font-size:18px;">**Advantages**</span>     

<span style="font-family:Georgia; font-size:18px;">**Limitations**</span>     

<span style="font-family:Georgia; font-size:18px;">**Applications**</span>     


<span style="font-family:Georgia; font-size:16px;">
Thanks for reading! If you want to get in touch with me or leave me any feedback, feel free to reach me on my email. 

##### References

Gneiting, T. Making and Evaluating Point Forecasts. Journal of the American Statistical Association, 2011, 106, 746-762

Goodwin, P. & Lawton, R. On the asymmetry of the symmetric MAPE. International Journal of Forecasting, 1999, 15, 405-408

Hoover, J. Measuring Forecast Accuracy: Omissions in Today's Forecasting Engines and Demand-Planning Software. Foresight: The International Journal of Applied Forecasting, 2006, 4, 32-35

Kolassa, S. Why the "best" point forecast depends on the error or accuracy measure (Invited commentary on the M4 forecasting competition). International Journal of Forecasting, 2020, 36(1), 208-211

Kolassa, S. & Martin, R. Percentage Errors Can Ruin Your Day (and Rolling the Dice Shows How). Foresight: The International Journal of Applied Forecasting, 2011, 23, 21-29

Kolassa, S. & Schütz, W. Advantages of the MAD/Mean ratio over the MAPE. Foresight: The International Journal of Applied Forecasting, 2007, 6, 40-43

McKenzie, J. Mean absolute percentage error and bias in economic forecasting. Economics Letters, 2011, 113, 259-262

Zheng, S. Gradient descent algorithms for quantile regression with smooth approximation. International Journal of Machine Learning and Cybernetics, 2011, 2, 191-207

Mark A. Moon, Demand and Supply Integration: The Key to World-Class Demand Forecasting. Performance Measurement, 2013, 

Next Generation Demand Management
by Charles W. Chase
Published by Wiley, 2016 WHY MAPE IS NOT ALWAYS THE BEST METRIC
