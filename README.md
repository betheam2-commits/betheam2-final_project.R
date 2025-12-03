library(readr)
setwd("/courses/STA145/betheam2")
# Load the data 
data <- read_csv("data.csv")
# summary statistics 
summary(data$years_in_office)
summary(data$committess_no)
# scatter plot 
linear_plot <- plot(data$years_in_office, data$committess_no)
print(linear_plot)

# add x line and y line for means
meany <- mean(data$committess_no)
meanx <- mean(data$years_in_office)

abline(h = meany, col = "black")
abline(v = meanx, col = "black")



##### STEP 2: Calculate linear regression line (i.e., slope) and add to scatter plot
linear_relationship <- lm(data$committess_no ~ data$years_in_office, data = data)
summary(linear_relationship)

# Add the linear regression line to the scatter plot
# NOTE: double check the scatter plot is currently in your utilities window!
abline(linear_relationship, col = "red")

##### STEP 3: Plot the residuals

# Plot the residuals
plot(data$committess_no, residuals(linear_relationship))

# Add a horizontal line at zero to indicate the baseline
abline(h = 0, col = "red")
