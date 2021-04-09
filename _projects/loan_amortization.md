---
title: "Loan Amortization"
layout: single
author_profile: true
excerpt: "Financial Modeling Series - loan amortization using vba & Python"
date:   2021-02-14 22:12:28 -0500
header:
  teaser: /img/Project/Teaser/amortization.jpeg
theme: mint
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

<img src="/img/Project/Teaser/home-loan.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

#### Introduction

<span style="font-family:Georgia; font-size:18px;">
This article is part of a series about financial modeling using python/vba/R where I cover some of the prominent financial models useful for analysts. In this article we will explore loan amortization using Excel and Python. If you follow along for both, you’ll understand the concept at a deeper level, but feel free to navigate directly to the [Excel](#loan-amortization-using-microsoft-excel) or [Python](#loan-amortization-using-python) sections however you please.</span>   

<span style="font-family:Georgia; font-size:18px;">
**So, what does it mean when a loan is amortized?**</span>   
<span style="font-family:Georgia; font-size:18px;">
Amortization, derived from a Latin word *admortire*, which means “to kill”, simply refers to paying off an amount owed over time by making planned, incremental payments of principal and interest.</span>   

<span style="font-family:Georgia; font-size:18px;"> In the following section, we will talk about some key terms on amortization before jumping onto the code and building a amortization schedule.</span>    

> ##### Amortization Schedule
<span style="font-family:Georgia; font-size:18px;"> An amortization schedule is a complete table of periodic loan payments, showing the amount of principal and the amount of interest that comprise each payment until the loan is paid off at the end of its term.</span>   


> ##### Components of a Amortization Schedule in a Financial Model
- <span style="font-family:Georgia; font-size:18px;"> Loan amount : Original or expected balance for your mortgage/loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> Term in years : The number of years over which you will repay this loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> Interest rate : Annual fixed interest rate for this loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> Payment per period : Includes principal payment and interest payment (PI). While each periodic -  payment is the same amount early in the schedule, the majority of each payment is interest; later in the schedule, the majority of each payment covers the loan's principal.</span>   
- <span style="font-family:Georgia; font-size:18px;"> Total interest : Total of all interest paid over the full term of the mortgage. This total interest amount assumes that there are no prepayments of principal.</span>   
- <span style="font-family:Georgia; font-size:18px;"> Total payments : Total of all monthly payments over the full term of the mortgage. This total payment amount assumes that there are no prepayments of principal.</span>   

<span style="font-family:Georgia; font-size:18px;">
Next, lets discuss the layout we are trying to build and the sections we look forward to build.</span>   

#### Loan Amortization using Microsoft Excel

#### Loan Amortization using Python

##### References

<span style="font-family:Georgia; font-size:18px;">
(1) Benninga, Simon (April 2014). Financial Modeling. Cambridge, MA: MIT Press. ISBN: 9780262027281.</span>    

