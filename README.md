# Importing-Excel-files-into-R
# Importing excel files into R programming ### 
 
library(tidyverse)
library(readxl)
### Reading the dataset (School Breakfast program Participation and Meals served)

breakfast <- read_excel('breakfast.xlsx')

### looking at the content of the data by using the glimpse command
glimpse(breakfast)

### you can see that all the variable name can found in fouth line
### so we use the skip command to remove the first 3  columns or variables

breakfast <- read_excel('breakfast.xlsx', skip = 3)
glimpse(breakfast)
view(breakfast) 

### After viewing the data, you realized that the second line is messed up so clean the data 

names <- c('Year', 'FreeStudents', 'ReducedStudents', 'PaidStudents', 'Totalstudents', 
           'MealsServed', 'PercentageFree')
breakfast <- read_excel('breakfast.xlsx', skip = 5, col_names = names)
glimpse(breakfast)
view(breakfast)

### Remember the dataset was in million so we use the mutate command to do that 
breakfast <- breakfast %>%
  mutate( FreeStudents = FreeStudents *1000000,
          ReducedStudents = ReducedStudents * 1000000,
          PaidStudents = PaidStudents * 1000000,
          Totalstudents = Totalstudents * 1000000,
          MealsServed = MealsServed * 1000000,
          PercentageFree = PercentageFree / 100)

glimpse(breakfast)
view(breakfast)
  
  
  
  
  
  
  
  
  
  
  









