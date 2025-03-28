# R Examples

## Random Distributions
Examples of generating random samples from various probability distributions:

```R
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
exp_sample <- rexp(20, rate = 0.5) #mean is inverse of rate
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

```R
x = c(-0.94, -0.97, 0.74, -0.27, 1.25, 0.42, 0.66, -0.68, -0.63)
y = c(0.40, 0.02, 2.63, -0.01, 0.72, 1.93, -0.94, -0.31, -0.30)
A = matrix(x, nrow = 3)
B = matrix(y, nrow = 3)
A + B
A %*% B
det(A)
invA = solve(A)
det(A %*% B)
egn.prod = eigen(A %*% B)
egn.values = egn.prod$values
egn.vec = egn.prod$vectors
sum(egn.values)
prod(egn.values)
```

## Data Frame Creation and Analysis

```R
df <- data.frame(
  id = 1:10,
  name = c("Alice", "Bob", "Charlie", "David", "Emma", "Frank", "Grace",
          "Hank", "Ivy", "Jack"),
  age = c(25, 30, 22, 35, 28, 26, 27, 29, 31, 33),
  gender = c("F", "M", "M", "M", "F", "M", "F", "M", "F", "M"),
  salary = c(45000, 60000, 35000, 75000, 50000, 40000, 55000, 65000, 70000, 80000)
)
head(df, 6)
df$age_sum <- df$age + df$salary
summary(df)
```

## Probability Distributions

```R
mu_m <- 180.3
var_m <- 10
mu_f <- 167.2
var_f <- 15
p_m_gt_200 <- 1 - pnorm(200, mean = mu_m, sd = sqrt(var_m))
p_m_lt_165 <- pnorm(165, mean = mu_m, sd = sqrt(var_m))
p_f_between_166_168 <- pnorm(168, mean = mu_f, sd = sqrt(var_f)) - 
                       pnorm(166, mean = mu_f, sd = sqrt(var_f))
if ((p_m_gt_200 + p_m_lt_165) > p_f_between_166_168) {
  cat("It is more likely to meet a man who is bigger than 200 cm or lesser than 165 cm.\n")
} else {
  cat("It is more likely to meet a woman who is between 166 and 168 cm.\n")
}
```

## Sequence and Plotting

```R
p <- seq(from = 0.001, to = 0.999, length.out = 1000)
log_p <- log(p)
df <- data.frame(p = p, log_p = log_p)
plot(df$p, df$log_p, type = "l", col = "blue", xlab = "p", ylab = "log(p)")
title(main = "Graph of p.log(p) for 0 < p ≤ 1")
```
