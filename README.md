# ANA505W5

#Revised assignment

# Install and load necessary packages
install.packages("dplyr")
library(dplyr)

# Download the dataset
download.file(url = "https://projects.fivethirtyeight.com/soccer-api/international/2022/wc_matches.csv", destfile = "WorldCup.csv")
WorldCup <- read.csv("WorldCup.csv")

# Take a look at the World Cup data
head(WorldCup)
summary(WorldCup)
str(WorldCup)

# Create a random sample of the data
mysample <- sample_n(WorldCup, size=15, replace = FALSE, weight = NULL, .env = NULL)

# Save the new sample as a CSV file
write.csv(mysample, 'WorldCupSample.csv')

# Piping to revise the code chunk
mysample3 <- mysample %>%
  arrange(date) %>%
  filter(spi1 < 80) %>%
  rename(Index1 = spi1, Index2 = spi2) %>%
  select(Index1, Index2, team1, team2) %>%
  summary()

print(mysample3)
