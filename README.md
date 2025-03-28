# RExamples

Work with the ‘airquality’ dataset. Construct 
dataframe using the variables ‘Ozone’, ‘Wind’, and ‘Temp’. Then, generate 
correlation plot for these variables using the GGally package. Provide an interpretation of the correlation plot. 
library(GGally) 
data("airquality") 
df = data.frame(airquality$Ozone, airquality$Wind, airquality$Temp) 
ggpairs(df) 

Obtain 
set of random samples of size 20 from an exponential distribution with mean 2. Form 
square matrix N with elements arranged in an appropriate number of rows and columns. Compute its transpose and then find the product of N and its transpose. 
set.seed(42) 
exp_sample <- rexp(20, rate = 0.5) 
N <- matrix(exp_sample, nrow = 4) 
N1 <- t(N) 
N1 %*% N 

Load the ‘mpg’ dataset. Display the structure of the dataset and determine how many variables and observations it contains. Identify how many variables are character strings and how many are numeric integers. Create 
histogram of the ‘displ’ variable, representing engine displacement in liters. Label the X and Y axes as ‘Engine Size’ and ‘Count’, respectively. Set the histogram title to ‘Histogram of Engine Displacement’. Use ‘green’ fill for the bars with ‘gray’ borders and apply 
‘classic’ theme for the background. 
library(tidyverse) 
library(hrbrthemes) 
dataset <- mpg 
str(dataset) 
engine <- dataset$displ 
ggplot(dataset, aes(x = engine)) + 
 geom_histogram(bins = 12, fill = "green", color = "gray") + 
 labs(title = "Histogram of Engine Displacement", x = "Engine Size", y = "Count") + 
 theme_classic() 

Generate two numeric vectors x1 and x2 with 60 random samples from the Normal distribution with mean 0 and standard deviation 1. Calculate their dot product (sum of the products of their corresponding elements). 
set.seed(42) 
x1 <- rnorm(60) 
x2 <- rnorm(60) 
dot_product <- t(x1) %*% x2 
dot_product

Utilize the ‘dplyr’ package for this analysis. From the mpg dataset, extract 
subset containing the car models civic, sentra, golf, altima, rogue 4wd, and malibu using the ‘filter’ function with an appropriate operator. Using this subset, produce 
barplot showing the models by manufacturer to visualize their distribution across manufacturers. Title the barplot ‘Distribution of Car Models by Manufacturer’ and label the X and Y axes as ‘Maker’ and ‘Total’, respectively. Apply 
‘minimal’ theme to the plot. Which manufacturer shows the greatest variety of car models in the barplot? (iv) Which manufacturer makes ‘malibu’ cars? 
library(dplyr) 
chosen_models <- c("civic", "sentra", "golf", "altima", "rogue 4wd", "malibu") 
filtered_dat
<- mpg %>% 
 filter(model %in% chosen_models) 
ggplot(filtered_data) + 
 geom_bar(aes(x = manufacturer, fill = model)) + 
 labs(title = "Distribution of Car Models by Manufacturer", x = "Maker", y = "Total") + 
 theme_minimal() 

Using the same subset of the ‘mpg’ data, create 
boxplot of the ‘displ’ variable (Engine displacement in liters) across different manufacturers, all within one plot. Use distinct colors for each manufacturer. Title the boxplot ‘Engine Size Across Manufacturers’ and label the X and Y axes as ‘Maker’ and ‘Displacement in Liters’, respectively. Use 
minimal theme for the plot. For which manufacturer are the engine displacement values negatively skewed? 
ggplot(filtered_data, aes(x = manufacturer, y = displ, fill = manufacturer)) + 
 geom_boxplot() + 
 labs(title = "Engine Size Across Manufacturers", x = "Maker", y = "Displacement in Liters") + 
 theme_minimal() 
