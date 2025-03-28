# R Examples

## Random Distributions
Examples of generating random samples from various probability distributions:

```R
normal_samples <- rnorm(20, mean = 0, sd = 1)
uniform_samples <- runif(20, min = 0, max = 1)
exp_samples <- rexp(20, rate = 0.5)
poisson_samples <- rpois(20, lambda = 4)
binomial_samples <- rbinom(20, size = 10, prob = 0.5)
```

## Airquality Dataset Analysis
Work with the ‘airquality’ dataset. Construct a dataframe using the variables ‘Ozone’, ‘Wind’, and ‘Temp’. Then, generate a correlation plot for these variables using the GGally package. Provide an interpretation of the correlation plot.

```R
library(GGally)
data("airquality")
df = data.frame(airquality$Ozone, airquality$Wind, airquality$Temp)
ggpairs(df)
```

## Exponential Distribution Sampling
Obtain a set of random samples of size 20 from an exponential distribution with mean 2. 
1. Form a square matrix N with elements arranged in an appropriate number of rows and columns
2. Compute its transpose and then find the product of N and its transpose

```R
set.seed(42)
exp_sample <- rexp(20, rate = 0.5)
N <- matrix(exp_sample, nrow = 4)
N1 <- t(N)
N1 %*% N
```

## MPG Dataset Exploration
Load the ‘mpg’ dataset:
1. Display the structure of the dataset and determine how many variables and observations it contains
2. Identify how many variables are character strings and how many are numeric integers
3. Create a histogram of the ‘displ’ variable (engine displacement in liters)

```R
library(tidyverse)
library(hrbrthemes)
dataset <- mpg
str(dataset)
engine <- dataset$displ
ggplot(dataset, aes(x = engine)) +
  geom_histogram(bins = 12, fill = "green", color = "gray") +
  labs(title = "Histogram of Engine Displacement", 
       x = "Engine Size", 
       y = "Count") +
  theme_classic()
```

## Normal Distribution Dot Product
Generate two numeric vectors x1 and x2 with 60 random samples from the Normal distribution with mean 0 and standard deviation 1. Calculate their dot product (sum of the products of their corresponding elements).

```R
set.seed(42)
x1 <- rnorm(60)
x2 <- rnorm(60)
dot_product <- t(x1) %*% x2
dot_product
```

## MPG Dataset Analysis with dplyr
Utilize the ‘dplyr’ package for this analysis:
1. Extract a subset containing the car models: civic, sentra, golf, altima, rogue 4wd, and malibu
2. Produce a barplot showing the models by manufacturer
3. Identify which manufacturer shows the greatest variety of car models
4. Determine which manufacturer makes ‘malibu’ cars

```R
library(dplyr)
chosen_models <- c("civic", "sentra", "golf", "altima", "rogue 4wd", "malibu")
filtered_data <- mpg %>%
  filter(model %in% chosen_models)
ggplot(filtered_data) +
  geom_bar(aes(x = manufacturer, fill = model)) +
  labs(title = "Distribution of Car Models by Manufacturer", 
       x = "Maker", 
       y = "Total") +
  theme_minimal()
```

## Engine Displacement Boxplot
Using the same subset of the ‘mpg’ data, create a boxplot of the ‘displ’ variable across different manufacturers:
- Use distinct colors for each manufacturer
- Identify which manufacturer's engine displacement values are negatively skewed

```R
ggplot(filtered_data, aes(x = manufacturer, y = displ, fill = manufacturer)) +
  geom_boxplot() +
  labs(title = "Engine Size Across Manufacturers", 
       x = "Maker", 
       y = "Displacement in Liters") +
  theme_minimal()
```

## Matrix Operations
Given two vectors v1 and v2, perform various matrix operations using matrices M1 and M2:

```R
v1 = c(-0.94, -0.97, 0.74, -0.27, 1.25, 0.42, 0.66, -0.68, -0.63)
v2 = c(0.40, 0.02, 2.63, -0.01, 0.72, 1.93, -0.94, -0.31, -0.30)
M1 = matrix(v1, nrow = 3)
M2 = matrix(v2, nrow = 3)
M1 + M2
M1 %*% M2
det(M1)
invM1 = solve(M1)
det(M1 %*% M2)
egn_result = eigen(M1 %*% M2)
egn_vals = egn_result$values
egn_vectors = egn_result$vectors
sum(egn_vals)
prod(egn_vals)
```

## Data Frame Creation and Analysis
Create a data frame 'people' with personal information and perform basic operations:

```R
employees <- data.frame(
  emp_id = 101:110,
  full_name = c("Sarah", "Mike", "Tom", "Lisa", "Kelly", "James", "Rachel", 
                "Peter", "Nina", "Alex"),
  years = c(23, 27, 31, 29, 24, 33, 26, 28, 30, 32),
  sex = c("F", "M", "M", "F", "F", "M", "F", "M", "F", "M"),
)
head(employees, 5)
employees$years_income_total <- employees$years + employees$income
summary(employees)
```

## Probability Distributions
Given height distribution parameters for males and females, calculate and compare specific probabilities:

```R
mean_male <- 180.3
variance_male <- 10
mean_female <- 167.2
variance_female <- 15
prob_male_over_200 <- 1 - pnorm(200, mean = mean_male, sd = sqrt(variance_male))
prob_male_under_165 <- pnorm(165, mean = mean_male, sd = sqrt(variance_male))
prob_female_166_168 <- pnorm(168, mean = mean_female, sd = sqrt(variance_female)) - 
                       pnorm(166, mean = mean_female, sd = sqrt(variance_female))
if ((prob_male_over_200 + prob_male_under_165) > prob_female_166_168) {
  cat("It is more likely to meet a man who is bigger than 200 cm or lesser than 165 cm.\n")
} else {
  cat("It is more likely to meet a woman who is between 166 and 168 cm.\n")
}
```

## Sequence and Plotting
Generate a sequence of values and create a plot of their logarithmic transformation":

```R
values <- seq(from = 0.001, to = 0.999, length.out = 1000)
log_values <- log(values)
data_set <- data.frame(p = values, log_p = log_values)
plot(data_set$p, data_set$log_p, type = "l", col = "blue", xlab = "p", ylab = "log(p)")
title(main = "Graph of p.log(p) for 0 < p ≤ 1")
```
