# R Examples

## Random Distributions
Examples of generating random samples from various probability distributions:

```R
set.seed(42)  # For reproducibility

# Normal distribution (mean = 0, sd = 1)
normal_samples <- rnorm(20, mean = 0, sd = 1)

# Uniform distribution (between 0 and 1)
uniform_samples <- runif(20, min = 0, max = 1)

# Exponential distribution (rate = 0.5) inverse of mean
exp_samples <- rexp(20, rate = 0.5)

# Poisson distribution (lambda = 4)
poisson_samples <- rpois(20, lambda = 4)

# Binomial distribution (n = 10 trials, p = 0.5)
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
