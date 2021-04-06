---
title: "Evaluation Metrics - Ranking"
excerpt: "Exploring Machine Learning Evaluation Metrics in Clustering tasks"
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

<img src="/img/Learning/Teaser/performanceeval.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:20px;"> Performance Evaluation Metrics in Machine Learning</span>   

<span style="font-family:Georgia; font-size:16px;"> This article is part of **Machine Learning Evaluation Metrics** series where we cover most prominent machine learning metrics used to evaluate/compare machine learning models. Choosing an appropriate metric is crucial while evaluating machine learning (ML) models. Each metric has its own applications and caveats and are grouped based on the ML problem they address.  In this article, we shall discuss the metrics used to evaluate ranking.</span>  

The following list is a overview of how the model evaluation metrics/techniques are classified:


<span style="font-family:Georgia; font-size:16px;"> 1. Regression Metrics</span>   
<span style="font-family:Georgia; font-size:16px;"> 2. Classification Metrics</span>   
<span style="font-family:Georgia; font-size:16px;"> 3. **Ranking Metrics**</span>   
<span style="font-family:Georgia; font-size:16px;"> 4. Clustering Metrics<span>   
<span style="font-family:Georgia; font-size:16px;"> 5. Statistical Metrics</span>   

<span style="font-family:Georgia; font-size:16px;">
Thanks for reading! If you want to get in touch with me or leave me any feedback, feel free to reach me on my email. 