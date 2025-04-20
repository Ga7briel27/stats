
R version 4.4.2 (2024-10-31 ucrt) -- "Pile of Leaves"
Copyright (C) 2024 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

[Previously saved workspace restored]

> install.packages(c("tidyverse", "tidymodels", "rpart", "rpart.plot", "caret", "palmerpenguins"))
Installing packages into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
--- Please select a CRAN mirror for use in this session ---
also installing the dependencies ‘proxy’, ‘e1071’, ‘ModelMetrics’, ‘plyr’, ‘pROC’, ‘reshape2’

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/proxy_0.4-27.zip'
Content type 'application/zip' length 181325 bytes (177 KB)
downloaded 177 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/e1071_1.7-16.zip'
Content type 'application/zip' length 674102 bytes (658 KB)
downloaded 658 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/ModelMetrics_1.2.2.2.zip'
Content type 'application/zip' length 480643 bytes (469 KB)
downloaded 469 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/plyr_1.8.9.zip'
Content type 'application/zip' length 1112532 bytes (1.1 MB)
downloaded 1.1 MB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/pROC_1.18.5.zip'
Content type 'application/zip' length 1168417 bytes (1.1 MB)
downloaded 1.1 MB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/reshape2_1.4.4.zip'
Content type 'application/zip' length 442884 bytes (432 KB)
downloaded 432 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/tidyverse_2.0.0.zip'
Content type 'application/zip' length 431685 bytes (421 KB)
downloaded 421 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/tidymodels_1.3.0.zip'
Content type 'application/zip' length 89269 bytes (87 KB)
downloaded 87 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/rpart_4.1.24.zip'
Content type 'application/zip' length 717069 bytes (700 KB)
downloaded 700 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/rpart.plot_3.1.2.zip'
Content type 'application/zip' length 1039349 bytes (1014 KB)
downloaded 1014 KB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/caret_7.0-1.zip'
Content type 'application/zip' length 3603797 bytes (3.4 MB)
downloaded 3.4 MB

trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/palmerpenguins_0.1.1.zip'
Content type 'application/zip' length 3005495 bytes (2.9 MB)
downloaded 2.9 MB

package ‘proxy’ successfully unpacked and MD5 sums checked
package ‘e1071’ successfully unpacked and MD5 sums checked
package ‘ModelMetrics’ successfully unpacked and MD5 sums checked
package ‘plyr’ successfully unpacked and MD5 sums checked
package ‘pROC’ successfully unpacked and MD5 sums checked
package ‘reshape2’ successfully unpacked and MD5 sums checked
package ‘tidyverse’ successfully unpacked and MD5 sums checked
package ‘tidymodels’ successfully unpacked and MD5 sums checked
package ‘rpart’ successfully unpacked and MD5 sums checked
package ‘rpart.plot’ successfully unpacked and MD5 sums checked
package ‘caret’ successfully unpacked and MD5 sums checked
package ‘palmerpenguins’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpAFBQuk\downloaded_packages
> # Load necessary libraries
> 
> library(tidyverse)
── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.4     ✔ tidyr     1.3.1
✔ purrr     1.0.4     
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
Warning messages:
1: package ‘tidyverse’ was built under R version 4.4.3 
2: package ‘lubridate’ was built under R version 4.4.3 
> 
> library(palmerpenguins)
Warning message:
package ‘palmerpenguins’ was built under R version 4.4.3 
> 
>  
> 
> # Load the penguins dataset
> 
> penguins <- penguins  # The dataset is built into the palmerpenguins package
> 
>  
> 
> # View the first few rows of the dataset
> 
> head(penguins)
# A tibble: 6 × 8
  species island    bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
  <fct>   <fct>              <dbl>         <dbl>             <int>       <int>
1 Adelie  Torgersen           39.1          18.7               181        3750
2 Adelie  Torgersen           39.5          17.4               186        3800
3 Adelie  Torgersen           40.3          18                 195        3250
4 Adelie  Torgersen           NA            NA                  NA          NA
5 Adelie  Torgersen           36.7          19.3               193        3450
6 Adelie  Torgersen           39.3          20.6               190        3650
# ℹ 2 more variables: sex <fct>, year <int>
> 
> # Remove rows with missing values
> 
> penguins <- drop_na(penguins)
> # Scatter plot: Bill Length vs. Bill Depth
> 
> ggplot(penguins, aes(x = bill_length_mm, y = bill_depth_mm, color = species)) +
+ 
+   geom_point() +
+ 
+   labs(title = "Bill Length vs. Bill Depth",
+ 
+        x = "Bill Length (mm)",
+ 
+        y = "Bill Depth (mm)") +
+ 
+   theme_minimal()
> 
> library(tidymodels)
── Attaching packages ────────────────────────────────────── tidymodels 1.3.0 ──
✔ broom        1.0.7     ✔ rsample      1.3.0
✔ dials        1.4.0     ✔ tune         1.3.0
✔ infer        1.0.7     ✔ workflows    1.2.0
✔ modeldata    1.4.0     ✔ workflowsets 1.1.0
✔ parsnip      1.3.1     ✔ yardstick    1.3.2
✔ recipes      1.2.1     
── Conflicts ───────────────────────────────────────── tidymodels_conflicts() ──
✖ scales::discard() masks purrr::discard()
✖ dplyr::filter()   masks stats::filter()
✖ recipes::fixed()  masks stringr::fixed()
✖ dplyr::lag()      masks stats::lag()
✖ yardstick::spec() masks readr::spec()
✖ recipes::step()   masks stats::step()
• Use suppressPackageStartupMessages() to eliminate package startup messages
There were 11 warnings (use warnings() to see them)
> 
>  
> 
> set.seed(42)
> 
> penguin_split <- initial_split(penguins, prop = 0.75)
> 
>  
> 
> train_data <- training(penguin_split)
> 
> test_data <- testing(penguin_split)
> library(rpart)
Error in value[[3L]](cond) : 
  Package ‘rpart’ version 4.1.23 cannot be unloaded:
 Error in unloadNamespace(package) : namespace ‘rpart’ is imported by ‘ipred’ so cannot be unloaded
In addition: Warning message:
package ‘rpart’ was built under R version 4.4.3 
> 
> library(rpart.plot)
Loading required package: rpart
Error in value[[3L]](cond) : 
  Package ‘rpart’ version 4.1.23 cannot be unloaded:
 Error in unloadNamespace(package) : namespace ‘rpart’ is imported by ‘ipred’ so cannot be unloaded
In addition: Warning messages:
1: package ‘rpart.plot’ was built under R version 4.4.3 
2: package ‘rpart’ was built under R version 4.4.3 
> 
>  
> 
> # Define a decision tree model
> 
> dtree_model <- decision_tree(mode = "classification", tree_depth = 3)
> 
>  
> 
> # Train the model using the training data
> 
> dtree_fit <- fit(dtree_model, species ~ bill_length_mm + bill_depth_mm + flipper_length_mm, data = train_data)
> # Plot the decision tree
> 
> dtree_fit %>% extract_fit_engine() %>% rpart.plot()
Error in rpart.plot(.) : could not find function "rpart.plot"
> # Plot the decision tree
> 
> dtree_fit %>% extract_fit_engine() %>% rpart.plot()
Error in rpart.plot(.) : could not find function "rpart.plot"
> # Install and load the rpart.plot package
> 
> install.packages("rpart.plot")
Installing package into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/rpart.plot_3.1.2.zip'
Content type 'application/zip' length 1039349 bytes (1014 KB)
downloaded 1014 KB

package ‘rpart.plot’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpAFBQuk\downloaded_packages
> library(rpart.plot)
Loading required package: rpart
Error in value[[3L]](cond) : 
  Package ‘rpart’ version 4.1.23 cannot be unloaded:
 Error in unloadNamespace(package) : namespace ‘rpart’ is imported by ‘ipred’ so cannot be unloaded
In addition: Warning messages:
1: package ‘rpart.plot’ was built under R version 4.4.3 
2: package ‘rpart’ was built under R version 4.4.3 
> 
> # Plot the decision tree
> 
> dtree_fit %>% 
+   extract_fit_engine() %>% 
+   rpart.plot(extra = 4, box.palette = "auto")
Error in rpart.plot(., extra = 4, box.palette = "auto") : 
  could not find function "rpart.plot"
> # Make predictions on test data
> 
> predictions <- predict(dtree_fit, test_data)
> 
>  
> 
> # Create a confusion matrix
> 
> library(caret)
Loading required package: lattice

Attaching package: ‘caret’

The following objects are masked from ‘package:yardstick’:

    precision, recall, sensitivity, specificity

The following object is masked from ‘package:purrr’:

    lift

Warning message:
package ‘caret’ was built under R version 4.4.3 
> 
> confusionMatrix(data = predictions$.pred_class, reference = test_data$species)
Confusion Matrix and Statistics

           Reference
Prediction  Adelie Chinstrap Gentoo
  Adelie        35         2      0
  Chinstrap      2        17      0
  Gentoo         0         0     28

Overall Statistics
                                          
               Accuracy : 0.9524          
                 95% CI : (0.8825, 0.9869)
    No Information Rate : 0.4405          
    P-Value [Acc > NIR] : < 2.2e-16       
                                          
                  Kappa : 0.926           
                                          
 Mcnemar's Test P-Value : NA              

Statistics by Class:

                     Class: Adelie Class: Chinstrap Class: Gentoo
Sensitivity                 0.9459           0.8947        1.0000
Specificity                 0.9574           0.9692        1.0000
Pos Pred Value              0.9459           0.8947        1.0000
Neg Pred Value              0.9574           0.9692        1.0000
Prevalence                  0.4405           0.2262        0.3333
Detection Rate              0.4167           0.2024        0.3333
Detection Prevalence        0.4405           0.2262        0.3333
Balanced Accuracy           0.9517           0.9320        1.0000
> 
