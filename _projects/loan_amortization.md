---
title: "Loan Amortization"
layout: single
author_profile: true
excerpt: "Financial Modeling Series - Loan Amortization using vba & Python"
date:   2021-02-14 22:12:28 -0500
header:
  teaser: /img/Project/ProjectTeaser/amortization.jpeg
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

<img src="/img/Project/ProjectTeaser/amort1.jpg" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

#### Introduction

<span style="font-family:Georgia; font-size:18px;">
This article is part of a series about **financial modeling** using python/vba/R where I cover some of the prominent financial models useful for analysts. In this article we will explore loan amortization using Excel and Python. If you follow along for both, you’ll understand the concept at a deeper level, but feel free to navigate directly to the [Excel](#loan-amortization-using-microsoft-excel) or [Python](#loan-amortization-using-python) sections however you please.</span>   

<span style="font-family:Georgia; font-size:18px;">
**So, what does it mean when a loan is amortized?**</span>   
<span style="font-family:Georgia; font-size:18px;">
Amortization, derived from a Latin word *admortire*, which means “to kill”, simply refers to paying off an amount owed over time by making planned, incremental payments of principal and interest.</span>   

<span style="font-family:Georgia; font-size:18px;"> In the following section, we will talk about some key terms on amortization before jumping onto the code and building a amortization schedule.</span>    

> ##### Amortization Schedule
<span style="font-family:Georgia; font-size:18px;"> An amortization schedule is a complete table of periodic loan payments, showing the amount of principal and the amount of interest that comprise each payment until the loan is paid off at the end of its term.</span>   


> ##### Components of a Amortization Schedule in a Financial Model
- <span style="font-family:Georgia; font-size:18px;"> **Loan amount** : Original or expected balance for your mortgage/loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> **Term in years** : The number of years over which you will repay this loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> **Interest rate** : Annual fixed interest rate for this loan.</span>   
- <span style="font-family:Georgia; font-size:18px;"> **Payment per period** : Also called as Equated Monthly Installment (EMI), includes principal payment and interest payment (PI). While each periodic -  payment is the same amount early in the schedule, the majority of each payment is interest; later in the schedule, the majority of each payment covers the loan's principal.</span>   
- <span style="font-family:Georgia; font-size:18px;"> **Total interest** : Total of all interest paid over the full term of the mortgage. This total interest amount assumes that there are no prepayments of principal.</span>   
- <span style="font-family:Georgia; font-size:18px;"> **Total payments** : Total of all monthly payments over the full term of the mortgage. This total payment amount assumes that there are no prepayments of principal.</span>   

<span style="font-family:Georgia; font-size:18px;">
Next, lets discuss the design and layout of the amortization calculator that we are going to build in following sections. We shall build our excel amortization model with three sections: loan information/summary grid, loan EMI data table and an amortization schedule. </span>   

#### Loan Amortization using Microsoft Excel

<span style="font-family:Georgia; font-size:18px;">
We begin initializing our input to the amortization calculator, such as, the annual interest rate, amortization period, payments per year, and the loan amount (principal). Let's consider a 30-year loan of 200,000 USD with monthly payments at an 8% annual rate of interest. This should require a monthly payment of $1,467.53 to fully amortize the loan.  </span>   

<figure>
  <img src="/img/Project/p3/summary.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 1: Loan Summary </figcaption>
</figure>

<span style="font-family:Georgia; font-size:18px;">
The loan EMI data table is a table that does a sensitivity analysis on the loan information provided in the summary. This paragraph elaborates on the implementation of two-dimensional excel data tables to perform sensitivity analysis on the payment per period/EMI with loan term and the annual interest rate. Figure 2 illustrates the sensitivity analysis on the payment per period.</span>   

<figure>
  <img src="/img/Project/p3/emi-comp-chart.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 2: Sensitivity analysis on the EMI with loan term and annual interest rate </figcaption>
</figure>

<span style="font-family:Georgia; font-size:18px;">
The upper left-hand corner of our data table contains, the formula as a reference to the payment per period(available in the loan summary section) .
We now use the Data Table command. We fill in both the Row input cell (indicating the cell that contains loan term in the loan summary) and the Column input cell (indicating the cell that contains annual interest rate in the loan summary). We then proceed with generating the loan amortization schedule.</span>   

<figure>
  <img src="/img/Project/p3/amort-schedule.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 3: Loan amortization schedule for the input information in the loan summary.</figcaption>
</figure>

<span style="font-family:Georgia; font-size:18px;">
We will be using IF statements in the amortization table so that changes in the “Number of Years” and/or “Payments per Year” input variables will be correctly incorporated into the cells. We use the excel functions PMT, IPMT, and PPMT to compute the “Payment” and “Interest” and “Repayment of Principal” column entries, respectively. Figure 3 depicts amortization schedule for our input from loan summary section. To modify any of the cells or edit the worksheet, you can fork my [github repository](https://github.com/prabhupavitra/Financial-Modeling/) or download this workbook by clicking on this [link](https://github.com/prabhupavitra/Financial-Modeling/blob/master/CodeFiles/Amortization.xlsx).</span>   

#### Loan Amortization using Python

##### References

<span style="font-family:Georgia; font-size:18px;">
(1) Benninga, Simon (April 2014). Financial Modeling. Cambridge, MA: MIT Press. ISBN: 9780262027281.</span>    
<span style="font-family:Georgia; font-size:18px;">
(2) Ross, S. A., R. W. Westerfield, and J. Jaffe. 2010. Corporate Finance, 9th ed. McGraw-Hill.

