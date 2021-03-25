---
title: "Financial Data Visualization - Distributions"
excerpt: "Visualizing Distributions in R - Finance "
date:   2020-08-10 22:12:28 -0500
theme : "mint"
---


<img src="/img/Learning/Teaser/viz-distributions.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

<span style="font-family:Georgia; font-size:16px;">
This article is part of **financial data visualization** blog series where we cover most prominent plots used to quickly comprehend thousands or even millions of data points to support decision-making in finance. In this article, we examine ways of visualizing distributions in finance.</span>  

<span style="font-family:Georgia; font-size:16px;">
Analyzing and visualizing distributions is widely used in Data Science projects since we are interested in understanding the behaviour of a numeric variable. In other words, we would want to know the central tendency of a variable as well as the outliers. We would also be interested in knowing if the variable is symmetrically distributed or skewed, if the distribution is unimodal/bimodal/multimodal, if it contains suspicious/impossible values and so on</span>   

<span style="font-family:Georgia; font-size:16px;">
Most commonly used visualizations to compare amounts include:</span>   

<span style="font-family:Georgia; font-size:16px;"> 1. Histogram</span>   
<span style="font-family:Georgia; font-size:16px;"> 2. Density Plot</span>    
<span style="font-family:Georgia; font-size:16px;"> 3. Empirical cumulative distribution function</span>    
<span style="font-family:Georgia; font-size:16px;"> 4. Boxplot</span>    
<span style="font-family:Georgia; font-size:16px;"> 5. Violin Plot</span>    
<span style="font-family:Georgia; font-size:16px;"> 6. Strip Chart</span>    
<span style="font-family:Georgia; font-size:16px;"> 7. Sina Plot</span>    
<span style="font-family:Georgia; font-size:16px;"> 8. Ridgeline Plot</span>    
<span style="font-family:Georgia; font-size:16px;"> 9. Quantile–quantile plot</span>    

<span style="font-family:Georgia; font-size:16px;">
We will be using quandl api and quantmod api to import financial data. Using an API for importing data is beneficial, especially in finance, because the dataset is updated extremely frequently, and they offer a lot of benefits in terms of ease and flexibility. </span>    
<span style="font-family:Georgia; font-size:16px;">
We can install quandl & quantmod packages and register an account on quandl.com</span>    

<span style="font-family:Georgia; font-size:16px;">
Create a free Quandl account and set your API key here</span>    
<span style="font-family:Georgia; font-size:16px;">
For more information, refer to the link below : </span>    
<span style="font-family:Georgia; font-size:16px;">
<a href="https://www.quandl.com/tools/r"> https://www.quandl.com/tools/r </a> </span>    

```r
# Run the script below with your secret key obtained after registering on quandl
# quandl_sk = "<quandl secret key>"

# Alternative way to Load Data Tokens by declaring them in a file 
source("../R/Setup/apitokens.r")

# Data manipulation libraries used in this notebook
library(tibble) # includes rownames_to_column function
library(dplyr) # includes filter function
library(tidyr) # includes spread function

# Visualization libraries used in this notebook
library(ggplot2) # Includes ggplot function
library(ggforce) # Includes geom_sina & geom_parallel_sets
library(ggridges) # Includes geom_
library(cowplot) # Includes axis_canvas for generating A Canvas Onto Which One Can Draw Axis-Like Objects

# Data API libraries
library(Quandl) # To import data from Quandl API
library(quantmod) # To import data using yahoo,google api

# Animation Packages
library(gganimate) # to add animation to static plot 
library(gifski) # Converts images to GIF animations
library(png) # Provides an easy and simple way to read, write and display bitmap images stored in the PNG format.

# Datetime Parsing functions
library(lubridate) # includes datetime parsing functions

# Data visualization addon library for Themes and colors available in my github repository
# https://github.com/prabhupavitra/dviz.addon
library(dviz.addon)

# Resizing plot width and height from default 7
# https://www.rdocumentation.org/packages/repr/versions/0.7/topics/repr-options
options(repr.plot.width=10, repr.plot.height=4)

```

> Importing Data (Using Quandl and quantmod API)   

<span style="font-family:Georgia; font-size:16px;"> 
This notebook uses Quandl and quantmod API to import Financial Data directly to R.</span>   

<span style="font-family:Georgia; font-size:16px;"> Datasets used in this notebook include:</span>   
<span style="font-family:Georgia; font-size:16px;"> 1. Historical Prices of Precious Metals (Gold, Silver, Platinum and Palladium) </span>    
<span style="font-family:Georgia; font-size:16px;"> 2. Historical Prices of Non-Ferrous Base Metals  (Aluminum; Copper; Lead; Nickel; Tin and Zinc)</span>   
<span style="font-family:Georgia; font-size:16px;"> 3. Consumer Price Index for All Urban Consumers (CPI-U)</span>   

> <span style="font-family:Georgia; font-size:16px;">Precious Metals Prices : London Fixing (U.S. Dollars per Troy Ounce)</span>   

```r
# Using Quandl API : Import prices of Precious Metals ( Gold, Silver, Platinum, Palladium )

# Gold Price: London Fixing
gold <- Quandl("LBMA/GOLD", api_key=quandl_sk)

# Silver Price: London Fixing
silver <- Quandl("LBMA/SILVER", api_key=quandl_sk)

# Platinum Fixing
platinum <- Quandl("LPPM/PLAT", api_key=quandl_sk)

# Palladium
palladium <- Quandl("LPPM/PALL", api_key=quandl_sk)
```

> <span style="font-family:Georgia; font-size:16px;">Base Metals Prices : Spot Prices (U.S. Dollars per metric ton)</span>    

```r
# Other Base Metals (Aluminum; Cobalt; Copper; Iron Ore; Lead; Molybdenum; Nickel; Tin; Uranium and Zinc)

# Aluminum; 99.5% minimum purity; LME spot price; CIF UK ports; US$ per metric ton
aluminium <- Quandl("ODA/PALUM_USD", api_key=quandl_sk)

# Copper; grade A cathode; LME spot price; CIF European ports; US$ per metric ton
copper <- Quandl("ODA/PCOPP_USD", api_key=quandl_sk)

# Lead; 99.97% pure; LME spot price; CIF European Ports; US$ per metric ton
lead <- Quandl("ODA/PLEAD_USD", api_key=quandl_sk)

# Nickel; melting grade; LME spot price; CIF European ports; US$ per metric ton
nickel <- Quandl("ODA/PNICK_USD", api_key=quandl_sk)

# Tin; standard grade; LME spot price; US$ per metric ton
tin <- Quandl("ODA/PTIN_USD", api_key=quandl_sk)

# Zinc; high grade 98% pure; US$ per metric ton
zinc <- Quandl("ODA/PZINC_USD", api_key=quandl_sk)
```

> <span style="font-family:Georgia; font-size:16px;">CPI Data : CPI for U.S. City Average (Units: Index 1982-1984=100, Seasonally Adjusted ; Frequency: Monthly)</span>  

```r
# Consumer Price Index for All Urban Consumers: All Items in U.S. City Average 
monthly_allitems <- Quandl("FRED/CPIAUCSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Food and Beverages in U.S. City Average
monthly_foodbev <- Quandl("FRED/CPIFABSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: All Items Less Food and Energy in U.S. City Average
monthly_excfoodnbev <- Quandl("FRED/CPILFESL", api_key=quandl_sk)  

# Consumer Price Index for All Urban Consumers: Recreation in U.S. City Average
monthly_recreation <- Quandl("FRED/CPIRECSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Housing in U.S. City Average 
monthly_housing <- Quandl("FRED/CPIHOSNS", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Education and Communication in U.S. City Average
monthly_eduncomm <- Quandl("FRED/CPIEDUSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Apparel in U.S. City Average
monthly_apparel <- Quandl("FRED/CPIAPPSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Energy in U.S. City Average
monthly_energy <- Quandl("FRED/CPIENGSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Other Goods and Services in U.S. City Average
monthly_othergns <- Quandl("FRED/CPIOGSSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Transportation in U.S. City Average 
monthly_trnsprt <- Quandl("FRED/CPITRNSL", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Services in U.S. City Average 
monthly_otherserv <- Quandl("FRED/CUSR0000SAS", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Commodities in U.S. City Average
monthly_commod <- Quandl("FRED/CUSR0000SAC", api_key=quandl_sk) 

# Consumer Price Index for All Urban Consumers: Medical Care in U.S. City Average
monthly_medcare <- Quandl("FRED/CPIMEDSL", api_key=quandl_sk)
```

> <span style="font-family:Georgia; font-size:16px;">Bitcoin and IBM Stock Data from Yahoo : Using Quantmod Package</span>   

```r
cryptodata <- new.env() #Make a new environment for quantmod to store data in
 
beginDate = as.Date("2014-04-01") #Specify period of time we are interested in
endDate = as.Date("2019-12-01")
 
ticker <- c("BTC-USD","IBM") #Define the tickers we are interested in
 
#Download the stock historical data (for all tickers mentioned previously)
getSymbols(ticker, env = cryptodata, src = "yahoo", from = beginDate, to = endDate,auto.assign=TRUE)

btcusd <- data.frame(get("BTC-USD", envir = cryptodata))
ibmstock <- data.frame(get("IBM", envir = cryptodata))
```

### Data Preparation

> <span style="font-family:Georgia; font-size:16px;">Precious Metals Prices : London Fixing (U.S. Dollars per Troy Ounce)</span>   

```r
# Merging the datasets of all 4 precious metals (Measured per Troy Ounce)
precious_metals <- 
rbind(gold %>% select("Date","USD (AM)") %>% rename(USD="USD (AM)") %>% mutate(Commodity="Gold"),
silver %>% select("Date","USD") %>% mutate(Commodity="Silver"),
platinum %>% select("Date","USD AM") %>% rename(USD="USD AM") %>% mutate(Commodity="Platinum"),
palladium %>% select("Date","USD AM") %>% rename(USD="USD AM") %>% mutate(Commodity="Palladium")) %>%
mutate(Year = year(Date)) %>% filter(USD!="NA")

head(precious_metals,5)
```

<img src="/img/Learning/visualization/viz1/tbl-1.png" alt="this is a placeholder image" width="50%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:16px;">Base Metals Prices : Spot Prices (U.S. Dollars per metric ton)</span>   

```r
base_metals <-
rbind(aluminium %>% mutate(Commodity="Aluminium"),
      copper %>% mutate(Commodity="Copper"),
      lead %>% mutate(Commodity="Lead"),
      nickel %>% mutate(Commodity="Nickel"),
      tin %>% mutate(Commodity="Tin"),
      zinc %>% mutate(Commodity="Zinc")) %>%
mutate(Year = year(Date))

head(base_metals,1)
```
<img src="/img/Learning/visualization/viz1/tbl-2.png" alt="this is a placeholder image" width="50%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:16px;">CPI Data : CPI for U.S. City Average </span>   

```r
cpi_monthly_sa <-
rbind(monthly_allitems %>% mutate(Category="CPI"),
      monthly_excfoodnbev %>% mutate(Category="Core CPI"),
      monthly_apparel %>% mutate(Category="Apparel"),
      monthly_commod %>% mutate(Category="Commodities"),
      monthly_eduncomm %>% mutate(Category="Education & Communication"),
      monthly_energy %>% mutate(Category="Energy"),
      monthly_foodbev %>% mutate(Category="Food & Beverages"),
      monthly_housing %>% mutate(Category="Housing"),
      monthly_medcare %>% mutate(Category="Medical Care"),
      monthly_othergns %>% mutate(Category="Other Goods & Services"),
      monthly_otherserv %>% mutate(Category="Other Services"),
      monthly_recreation %>% mutate(Category="Recreation"),
      monthly_trnsprt %>% mutate(Category="Transportation")) %>%
mutate (Year =year(Date),Month=month(Date))

head(cpi_monthly_sa,1)
```
<img src="/img/Learning/visualization/viz1/tbl-3.png" alt="this is a placeholder image" width="50%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:16px;">Calculating Return on Bitcoin Data from Yahoo </span>   

```r
btcusd_return <-
btcusd %>% rename("Adjusted_Close" = "BTC.USD.Adjusted",
                  "Trading_Volume" = "BTC.USD.Volume",
                  "High" = "BTC.USD.High",
                  "Open" = "BTC.USD.Open",
                  "Low" = "BTC.USD.Low",
                  "Close" = "BTC.USD.Close") %>%
rownames_to_column("Date") %>% 
mutate(Return = (Adjusted_Close/lag(Adjusted_Close)-1)*100,
       Trading_Volume_millions = Trading_Volume/(10^6)) %>% filter(Return!="NA")

head(btcusd_return,1)
```
<img src="/img/Learning/visualization/viz2/tbl-4.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

<span style="font-family:Georgia; font-size:16px;"> We will also calculate monthly return for the bitcoin and IBM stock data.</span>   

```r
btcusd_monthlyret <- btcusd_return %>% 
                     mutate(Month = as.yearmon(Date)) %>% 
                     arrange(Month) %>%
                     group_by(Month) %>% 
                     summarise(MonthlyReturn = mean(Return)) 

head(btcusd_monthlyret,5)
```
<img src="/img/Learning/visualization/viz2/tbl-5.png" alt="this is a placeholder image" width="25%" height = "25%" class="center" >

```r
ibmstock_return <- ibmstock %>% 
                   rename("Adjusted_Close"="IBM.Adjusted") %>%
                   mutate(Return=(Adjusted_Close/lag(Adjusted_Close)-1)*100) %>%
                   filter(Return!="NA")

head(ibmstock_return,1)
```
<img src="/img/Learning/visualization/viz2/tbl-6.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

<span style="font-family:Georgia; font-size:16px;"> Before we proceed with visualizations, we will calculate some commonly used CPI metrics</span>   

```r
# Percent Change (1982-Present)
cpi_pctchng <- filter(cpi_monthly_sa,#Month==1,
                                     Year>1982,
                                     !(Category %in% c('Energy','Transport'))) %>%
               group_by(Category) %>%
               arrange(Date) %>%
               mutate(PercentChange = (Value/lag(Value)-1)*100) %>%
               filter(PercentChange!="NA") 

# Over-the-year percent change 
cpi_otypct <- 
cpi_monthly_sa %>% 
filter(Year>1982,Month==12) %>% 
arrange(Date) %>% 
group_by(Category) %>% 
mutate(OverYrPercentChange = (Value/lag(Value)-1)*100) %>%
filter(OverYrPercentChange!="NA")


# Annual Average, Annual Average CHange and Purchasing Power
cpi_annualavg <-
cpi_monthly_sa %>% filter(Year>1982,Year<2020) %>%
arrange(Date) %>%
group_by(Year,Category) %>%
summarise(AnnualAvg = mean(Value)) %>%
group_by(Category) %>%
mutate(AnnualAvgChange = (AnnualAvg/lag(AnnualAvg)-1)*100,
       PurchasingPower = (AnnualAvg/lag(AnnualAvg)*100)) %>%
filter(AnnualAvgChange!="NA")

```

> <span style="font-family:Georgia; font-size:18px;"> Univariate Distributions </span>   

<span style="font-family:Georgia; font-size:16px;"> A univariate distribution refers to the distribution of just one random variable and understanding their form and function is extremely useful in data science. When visualizing a univariate distribution our purpose is to see how a single variable is spread. One can use this plot when visualizing a single variable. Histograms and density plots are a popular choice for visualizing single distribution. </span>    

> <span style="font-family:Georgia; font-size:18px;"> Histogram </span>   

<span style="font-family:Georgia; font-size:16px;"> One of the simplest ways to show data spread is Histogram. To construct a histogram from a continuous variable you first need to split the data into intervals, called bins. Depending on the data distribution and the purpose of visualization, an appropriate bin width is chosen. Although software chooses a default bin width, it is vital to understand data-based binning techniques used in estimating bin width. </span>    

```r
# Histogram using geom_histogram() of Annual average change of monthly CPI
cpi_histplot <-
ggplot(cpi_annualavg, aes(x = cpi_annualavg$AnnualAvgChange)) + 
  geom_histogram(breaks=seq(-20,20,by=0.2),
                 col="darkblue",
                 fill="steelblue")  + 
  labs(x="Annual Average Change of monthly CPI",y="Weight in the CPI") +
  ggtitle("Histogram of Annual Average Change of monthly CPI(1982-2019)") +
  theme_pprabhu() +
  theme(plot.title = element_text(hjust = 0.5,face="italic"),
        axis.text.x = element_text(angle=0))    

cpi_histplot
```
<figure>
  <img src="/img/Learning/visualization/viz2/univariate-histogram" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 1: Histogram illustrating the annual average change in monthly CPI </figcaption>
</figure>


> <span style="font-family:Georgia; font-size:18px;"> Kernel Density Plots </span>   

<span style="font-family:Georgia; font-size:16px;">Kernel Density plots are a popular choice for visualizing single as well as multiple distributions because it creates a smooth curve on a given set of data. The smoothness of the curve is controlled by a bandwidth parameter that is analogous to the histogram bin width.</span>   

```r
# Kernel density estimaction using geom_density()
cpi_kerneldensity <-
  ggplot(cpi_annualavg, aes(x = cpi_annualavg$AnnualAvgChange)) + 
  geom_density(fill="#56B4E950",alpha=0.3,adjust=1/2) +
  labs(x="Annual Average Change of monthly CPI",y="Weight in the CPI") +
  ggtitle("Kernel density estimate of Annual Average Change of monthly CPI(1982-2019)") +
  theme_pprabhu() +
  theme(plot.title = element_text(hjust = 0.5,face="italic"),
        axis.text.x = element_text(angle=0))  

cpi_kerneldensity
```
<figure>
  <img src="/img/Learning/visualization/viz2/univariate-kde" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 2: Kernel Density Estimate illustrating the annual average change in monthly CPI </figcaption>
</figure>



> <span style="font-family:Georgia; font-size:18px;"> Empirical cumulative distribution function </span>   

<span style="font-family:Georgia; font-size:16px;"> An Empirical cumulative distribution function is an estimator of the Cumulative Distribution Function. The ECDF allows you to plot a feature of your data in order from least to greatest and see the whole feature as if is distributed across the data set. It has some useful properties such as being consistent and having a known confidence band. Best of all, it's non-parametric so it will work with pretty much any distribution.</span>   

```r
# Empirical cumulative distribution function in ascending order for December Over-the-year percent change in CPI
# ecdf using stat_ecdf() ; geom = "step" can be used for a step ecdf
cpi_ecdf_plot <-
ggplot(cpi_otypct, aes(x = cpi_otypct$OverYrPercentChange, 
                     y =81*..y..)) + 
  stat_ecdf(geom = "point", color = "#0072B2") +
  scale_x_continuous(limits = c(-22, 22), 
                     expand = c(0, 0),
                     name="Over-the-year percent change in CPI") +
  scale_y_continuous(limits = c(-.5, 82), 
                     expand = c(0, 0), 
                     name = "ECDF") +
  coord_cartesian(clip = "off") +
  theme_pprabhu() +
  ggtitle("ECDF of Over-the-Year Percent Change in CPI (Ascending)") +
  theme(axis.line.x = element_blank(),
        plot.title=element_text(hjust = 0.5,face="italic"),
        axis.text.x = element_text(angle=0))

cpi_ecdf_plot
```
<figure>
  <img src="/img/Learning/visualization/viz2/univariate-ecdf-asc" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 3: Empirical Cumulative Distribution Function of Over-the-year percent change in CPI.(Ascending) </figcaption>
</figure>


```r
# Empirical cumulative distribution function in descending order
ggplot(cpi_otypct, aes(x = cpi_otypct$OverYrPercentChange,  
                         y = 82-81*..y..)) + 
  stat_ecdf(geom = "step", color = "#0072B2") +
  scale_x_continuous(limits = c(-22, 22), 
                     expand = c(0, 0),
                     name="Over-the-year percent change in CPI") +
  scale_y_continuous(limits = c(-.5, 82), 
                     expand = c(0, 0), 
                     name = "ECDF") +
  coord_cartesian(clip = "off") +
  theme_pprabhu() +
  ggtitle("ECDF of Over-the-Year Percent Change in CPI (Descending)") +
  theme(axis.line.x = element_blank(),
        plot.title=element_text(hjust = 0.5,face="italic"),
        axis.text.x = element_text(angle=0))

```
<figure>
  <img src="/img/Learning/visualization/viz2/univariate-ecdf-desc" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 4: Empirical Cumulative Distribution Function of Over-the-year percent change in CPI.(Descending) </figcaption>
</figure>


```r
# Normalized ecdf 
ggplot(cpi_otypct, aes(x = cpi_otypct$OverYrPercentChange,  
                         y =..y..)) + 
  stat_ecdf(geom = "step", color = "#0072B2") +
  scale_x_continuous(limits = c(-22, 22), 
                     expand = c(0, 0),
                     name="Over-the-year percent change in CPI") +
  scale_y_continuous(limits = c(0, 1), 
                     expand = c(0, 0), 
                     name = "ECDF") +
  coord_cartesian(clip = "off") +
  theme_pprabhu() +
  ggtitle("Normalized ECDF of Over-the-Year Percent Change in CPI") +
  theme(axis.line.x = element_blank(),
        plot.title=element_text(hjust = 0.5,face="italic"),
        axis.text.x = element_text(angle=0))

```
<figure>
  <img src="/img/Learning/visualization/viz2/univariate-ecdf-norm" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 5: Normalized Empirical Cumulative Distribution Function of Over-the-year percent change in CPI </figcaption>
</figure>

> <span style="font-family:Georgia; font-size:18px;"> Multivariate Distributions </span>   

<span style="font-family:Georgia; font-size:16px;"> Visualizing multivariate distributions in a single plot arises in various situations as discussed in the following examples. For example, one might just be interested in comparing data spread of a single variable at various times for comparable data (Example: Price of precious metals); One may be curious about outliers or the density of the data points around a specified value; one might also want to compare multiple variables in a single dataset(Example: Salary distribution of male/female employees); One might be interested to know which data distribution is more volatile than the other; and so on.. The plots used in these scenarios depends on the number of distributions involved. The intention of the plot is to provide clarity on the purpose of the plot. Histograms and density plots are used when the number of distributions are less. The plots used to visualize multiple distributions includes, but not limited to, box plots, violin plot, strip chart, sina plots, ridgeline plots, boxen plots. Density plots work well for multiple distributions as they are somewhat distinct and contiguous. </span>    

```r
# Plots the Kernel density estimation for multiple distributions distinct and contiguous
cpi_annualavg_kde <- filter(cpi_annualavg,Category %in% c('Housing',
                                                          'Transportation',
                                                          'Recreation',
                                                          'Food & Beverages'))

cpi_annualavg_kdeplot <-
ggplot(cpi_annualavg_kde,
       aes(x = cpi_annualavg_kde$AnnualAvgChange,
           color=cpi_annualavg_kde$Category,
           fill=cpi_annualavg_kde$Category)) + 
  geom_density(alpha=0.3,adjust=1/2) +  
  labs(fill="CPI Category",color="CPI Category") +
  scale_x_continuous(limits = c(-20, 20), name = "Annual Average Change of monthly Consumer Price Index", expand = c(0, 0)) +
  scale_y_continuous(limits = c(0,0.75), name = "Weight in the CPI", expand = c(0, 0)) +
  coord_cartesian(clip = "off") +
  ggtitle("Kernel density estimate of CPI Components") +
  theme_pprabhu() +
  scale_fill_manual(values=pprabhu_pal("div",reverse=TRUE)(4)) +
  scale_color_manual(values=pprabhu_pal("div",reverse=TRUE)(4)) +
  theme(plot.title = element_text(hjust = 0.5,face="italic"),
        legend.position = "bottom",
        axis.text.x = element_text(angle=0)) 

cpi_annualavg_kdeplot
```

<span style="font-family:Georgia; font-size:16px;">
Thanks for reading! As I mentioned in the beginning, there are a lot of cool visualization techniques available for visualizing distributions. To modify the visualizations with your own data, Click <a href="https://colab.research.google.com/github/prabhupavitra/Data-Visualization-with-R/blob/master/Visualizing%20Amounts.ipynb"> Colab Notebook </a> to edit and run the workbook using Google Colab. 
If you want to get in touch with me, feel free to reach me on my email. You can also view the code in <a href="https://github.com/prabhupavitra/Data-Visualization-with-R"> my Github repository </a>.</span> 
