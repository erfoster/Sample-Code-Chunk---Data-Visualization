# Sample-Code-Chunk---Data-Visualization

## Assignment: Display a self-contained chunk of code that highlights a specific skill in R. 

### What the code does: 
The code demonstrates data visualization skills in R for creating tables and graphs. It specifically uses the packages `kableExtra`, `ggplot2`, `tidyverse`, `dplyr`, `formattable`, and `patchwork`. 

### Data:
Data comes from the `datasets` package in R; this code chunk uses the iris dataset.

### Code:
```{r, WARNING = FALSE, ECHO = FALSE, ouput = TRUE}
## setup 
    # loading packages 
library(kableExtra)
library(ggplot2)
library(datasets)
library(tidyverse)
library(dplyr)
library(formattable)
library(patchwork)
    
    # loading R data 
data(iris)

## creating the table 
iris %>%
  group_by(Species) %>%
  kbl(caption = "Sample Table with Iris Data") %>%
  kable("html", escape = F) %>%
  kable_styling("hover", full_width = F, html_font = "Cambria") %>%

## creating the plots

  # setosa plot 
p1 = iris %>% 
  filter(Species == "setosa") %>%
  ggplot(aes(x = Sepal.Length, y = Sepal.Width)) +
  geom_point(color = "#9370DB") +
  scale_y_continuous(
    limits = c(1.5, 4.5),
    breaks = c(1.5, 2, 2.5, 3, 3.5, 4, 4.5)
  ) +
  scale_x_continuous(
    limits = c(4.5, 7),
    breaks = c(4.5, 5, 5.5, 6, 6.5, 7)
  ) + 
  labs(y = "Sepal Width", 
       x = "Sepal Length",
       title = "Setosa") + 
  geom_smooth(method=lm, color = "purple", se = F) + 
  theme_minimal()

  # versicolor plot 
p2 = iris %>% 
  filter(Species == "versicolor") %>%
  ggplot(aes(x = Sepal.Length, y = Sepal.Width)) +
  geom_point(color = "lightblue") +
  scale_y_continuous(
    limits = c(1.5, 4.5),
    breaks = c(1.5, 2, 2.5, 3, 3.5, 4, 4.5)
  ) +
  scale_x_continuous(
    limits = c(4.5, 7),
    breaks = c(4.5, 5, 5.5, 6, 6.5, 7)
  ) + 
  labs(y = "Sepal Width", 
       x = "Sepal Length",
       title = "Versicolor") + 
  geom_smooth(method=lm, color = "#0082cb", se = F) + 
  theme_minimal()

  # virginica plot
p3 = iris %>% 
  filter(Species == "virginica") %>%
  ggplot(aes(x = Sepal.Length, y = Sepal.Width)) +
  geom_point(color = "pink") +
  scale_y_continuous(
    limits = c(1.5, 4.5),
    breaks = c(1.5, 2, 2.5, 3, 3.5, 4, 4.5)
  ) +
  scale_x_continuous(
    limits = c(4.5, 7),
    breaks = c(4.5, 5, 5.5, 6, 6.5, 7)
  ) + 
  labs(y = "Sepal Width", 
       x = "Sepal Length",
       title = "Virginica") + 
  geom_smooth(method=lm, color = "#F36196", se = F) + 
  theme_minimal()


## patching the plots together  

p1 + p2 + p3 + 
plot_annotation(title = bquote(~bold("Comparing Iris Types: Sepal Width and Length")),
                caption = "Source: R Datasets")

```


### Output: 


