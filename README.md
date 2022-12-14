# Google-Data-Analytics-Capstone
</br>
Tyra Silaphet </br>
11/04/2022 </br>
output: html document

# Synopsis

In this capstone project, I navigate a case study using the skills and competencies that I acquired from the Google Data Analytics Professional Certificate program offered on Coursera.

### Scenario

Case Study 1: How Does a Bike-Share Navigate Speedy Success?

In this case study, I act as a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. It has a network of 692 stations across Chicago with a fleet of 5,824 bicycles. The company offers flexible pricing plans for casual riders (single-ride passes, full-day passes) and customers who wish to purchase annual memberships. The director of marketing wants to maximize the number of annual memberships by converting casual riders into members.

### Business task: Design marketing strategies aimed at converting casual riders into annual members.

-   How do annual members and casual riders differ?
-   Why would casual riders would buy a membership?
-   How can digital media affect their marketing tactics?
-   Analyze the Cyclistic historical bike data to identify trends.

The data can be downloaded here: <https://divvy-tripdata.s3.amazonaws.com/index.html>

# Data Obtainment

The data was taken from 2021 September to 2022 September for the bike sharing service's website, and the results will be given based on this 12 month time frame.

The original csv files were downloaded and then uploaded to the working directory in RStudio Cloud.

This section will install and load the required libraries for analysis, load the .csv data into the data frame and identify each table's format.

```{r Data Loading, message=FALSE, warning=FALSE}
# Load each csv file into individual data frames
Sep_2021 <- read_csv("Desktop/previous twelve months bike/202109-divvy-tripdata.csv")
Oct_2021 <- read_csv("Desktop/previous twelve months bike/202110-divvy-tripdata.csv")
Nov_2021 <- read_csv("Desktop/previous twelve months bike/202111-divvy-tripdata.csv")
Dec_2021 <- read_csv("Desktop/previous twelve months bike/202112-divvy-tripdata.csv")
Jan_2022 <- read_csv("Desktop/previous twelve months bike/202201-divvy-tripdata.csv")
Feb_2022 <- read_csv("Desktop/previous twelve months bike/202202-divvy-tripdata.csv")
Mar_2022 <- read_csv("Desktop/previous twelve months bike/202203-divvy-tripdata.csv")
Apr_2022 <- read_csv("Desktop/previous twelve months bike/202204-divvy-tripdata.csv")
May_2022 <- read_csv("Desktop/previous twelve months bike/202205-divvy-tripdata.csv")
Jun_2022 <- read_csv("Desktop/previous twelve months bike/202206-divvy-tripdata.csv")
Jul_2022 <- read_csv("Desktop/previous twelve months bike/202207-divvy-tripdata.csv")
Aug_2022 <- read_csv("Desktop/previous twelve months bike/202208-divvy-tripdata.csv")
Sep_2022 <- read_csv("Desktop/previous twelve months bike/202209-divvy-publictripdata.csv")
```

```{r Data Format Check, message=FALSE, warning=FALSE}
# Check column names for each data frame
colnames(Sep_2021)
colnames(Oct_2021)
colnames(Nov_2021)
colnames(Dec_2021)
colnames(Jan_2022)
colnames(Feb_2022)
colnames(Mar_2022)
colnames(Apr_2022)
colnames(May_2022)
colnames(Jun_2022)
colnames(Jul_2022)
colnames(Aug_2022)
colnames(Sep_2022)
# Check for data frame structure
str(Sep_2021)
str(Oct_2021)
str(Nov_2021)
str(Dec_2021)
str(Jan_2022)
str(Feb_2022)
str(Mar_2022)
str(Apr_2022)
str(May_2022)
str(Jun_2022)
str(Jul_2022)
str(Aug_2022)
str(Sep_2022)
```

# Data Cleaning & Transformation

After viewing the data, some of the columns did not share the same format. Thus, these conflicted variables were converted to character variables.

To make the data easier to read, the "started_at" and "ended_at" columns were combined to provide a total duration (seconds) of the ride.

```{r Data Transformation, message = FALSE, warning = FALSE}
## Rename the conflicted variables
Sep_2021 <- mutate(Sep_2021, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Oct_2021 <- mutate(Oct_2021, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Nov_2021 <- mutate(Nov_2021, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Dec_2021 <- mutate(Dec_2021, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Jan_2022 <- mutate(Jan_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Feb_2022 <- mutate(Feb_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Mar_2022 <- mutate(Mar_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Apr_2022 <- mutate(Apr_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
May_2022 <- mutate(May_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Jun_2022 <- mutate(Jun_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Jul_2022 <- mutate(Jul_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Aug_2022 <- mutate(Aug_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
Sep_2022 <- mutate(Sep_2022, ride_id = as.character(ride_id), rideable_type = as.character(rideable_type), start_station_id = as.character(start_station_id),end_station_id = as.character(end_station_id))
## Combine all data into one data frame
trips <- bind_rows(Sep_2021, Oct_2021, Nov_2021, Dec_2021, Jan_2022, Feb_2022, Mar_2022, Apr_2022, May_2022, Jun_2022, Jul_2022, Aug_2022, Sep_2022)
## Filter out unnecessary columns 
trips <- trips %>%
  select(-c(start_lat, start_lng, end_lat, end_lng))
```

```{r Data Cleaning, message=FALSE, warning=FALSE, include=FALSE}
## Get a glimpse of the data
colnames(trips)
dim(trips)
head(trips)
tail(trips)
str(trips)
summary(trips)
## Rename memberships
trips <- trips %>%
  mutate(member_casual = recode(member_casual, "Subscriber" ="member", "Customer" = "casual"))
table(trips$member_casual)
## Add columns with the date, month, day, and year of each ride so that data can be aggregated
trips$date <- as.Date(trips$started_at)
trips$month <- format(as.Date(trips$date), "%m")
trips$day <- format(as.Date(trips$date), "%d")
trips$year <- format(as.Date(trips$date), "%Y")
trips$day_of_week <- format(as.Date(trips$date), "%A")
## Add a "duration" calculation to trips (in seconds)
trips$duration <- difftime(trips$ended_at, trips$started_at)
## Check updated structure
str(trips)
## Convert the duration from factor to numeric for calculations (should return "TRUE" for numeric)
is.factor(trips$duration)
trips$duration <- as.numeric(as.character(trips$duration))
is.numeric(trips$duration)
## Remove the "bad" data where the bikes were taken out for quality checks or if the duration was a negative value
trips_v2 <- trips[!(trips$start_station_name == "HQ QR" | trips$duration<0),]
## Remove the NA values to make data cleaner
trips_v3 <- na.omit(trips_v2)
```

# Data Analysis

The section will organize the data by weekdays.

```{r Weekday Summary, warning=FALSE, paged.print=TRUE}
## Order the weekdays in its traditional sequence
trips_v3$day_of_week <- ordered(trips_v3$day_of_week, levels = c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))
## Summarize the data based on the type of customer
customer_summary <- trips_v3 %>%
  group_by(member_casual) %>%
  summarize(avg_duration = mean(duration), median_duration = median(duration), max_duration = max(duration), min_duration = min(duration))
## Summarize the data based on the customer type and weekday combinations 
weekday_summary <- trips_v3 %>%
  group_by(day_of_week, member_casual) %>%
  summarize(avg_duration = mean(duration), median_duration = median(duration), max_duration = max(duration), min_duration = min(duration))
```

# Results

| Customer Type | Avg Ride Length (seconds) | Med Ride Length (seconds) | Max Ride Length (seconds) | Min Ride Length (seconds) |
|---------------|---------------|---------------|---------------|---------------|
| Casual        | 1974                      | 1016                      | 3356649                   | 0                         |
| Member        | 811                       | 598                       | 573467                    | 0                         |

</br>

The results are as follows by casual customers by weekdays </br>

| Weekday   | Avg Ride Length (seconds) | Med Ride Length (seconds) | Max Ride Length (seconds) | Min Ride Length (seconds) |
|---------------|---------------|---------------|---------------|---------------|
| Sunday    | 2282                      | 1185                      | 3235296                   | 0                         |
| Monday    | 1960                      | 1016                      | 1900899                   | 0                         |
| Tuesday   | 1763                      | 902                       | 2335375                   | 0                         |
| Wednesday | 1710                      | 881                       | 2337785                   | 0                         |
| Thursday  | 1685                      | 864                       | 2946429                   | 0                         |
| Friday    | 1889                      | 949                       | 3341501                   | 0                         |
| Saturday  | 2125                      | 1135                      | 3356649                   | 0                         |

</br>

The results are as follows by member customers by weekdays </br>

| Weekday   | Avg Ride Length (seconds) | Med Ride Length (seconds) | Max Ride Length (seconds) | Min Ride Length (seconds) |
|---------------|---------------|---------------|---------------|---------------|
| Sunday    | 923                       | 672                       | 89995                     | 0                         |
| Monday    | 777                       | 572                       | 89993                     | 0                         |
| Tuesday   | 764                       | 569                       | 89996                     | 0                         |
| Wednesday | 768                       | 575                       | 573467                    | 0                         |
| Thursday  | 760                       | 569                       | 89996                     | 0                         |
| Friday    | 796                       | 586                       | 542972                    | 0                         |
| Saturday  | 905                       | 669                       | 89996                     | 0                         |

</br>

# Visualization

```{r Data Visualization, echo = FALSE, warning = FALSE}
## Data wrangling for the weekday and number of rides summary
options(dplyr.summarise.inform = FALSE)
## Plot weekday's ride count by membership type
trips_v3 %>%
  mutate(weekday = wday(started_at, label = TRUE)) %>%
  group_by(member_casual, weekday) %>%
  summarise(number_of_rides = n(), average_duration = mean(duration)) %>%
  arrange(member_casual, weekday) %>% 
  ggplot(aes(x = weekday, y = number_of_rides, fill = member_casual)) +
  geom_col(position = "dodge") + 
  ggtitle("E-Bike Membership Type's Ride Count Summary") +
  labs (x = "Weekdays", y = "# of Rides")
  ggsave("ride_count.jpg", width = 2000, height = 1000, units = c("px"))
  
##  Plot weekday's average duration
trips_v3 %>%
  mutate(weekday = wday(started_at, label = TRUE)) %>%
  group_by(member_casual, weekday) %>%
  summarise(number_of_rides = n(), average_duration = mean(duration)) %>%
  arrange(member_casual, weekday) %>% 
  ggplot(aes(x = weekday, y = average_duration, fill = member_casual)) +
  geom_col(position = "dodge") +
  ggtitle("E-Bike Membership Type's Ride Duration Average") +
  labs (x = "Weekdays", y = "Ride Duration (seconds)")
  ggsave("ridetime_avg.jpg", width = 2000, height = 1000, units = c("px"))
```
 ![e-bike membership type's ride count summary](https://user-images.githubusercontent.com/117314151/200673836-3c17e05c-9b59-4407-b1be-cb4056034bb7.jpg)
  
 ![e-bike membership type's ride duration average](https://user-images.githubusercontent.com/117314151/200673922-8d70dafa-364f-4ebc-99e7-1f70c2082cc5.jpg)

# Conclusion:

Based on the data analysis, I made the following conclusions:

1.  Members and casual customers are set apart by their average ride duration such that casual customers ride for a longer time than members.
2.  Casual riders tend to ride more on the weekends while members tend to ride during the weekdays.

Thus, after identifying these trends, I recommend the following strategies to convert casual riders to members:

1.  Have the cost for weekday riding be cheaper so that the casual riders may consider riding during the weekdays and purchase the annual membership.
2.  Make the annual membership not too high of a price so that casual riders may also consider the cost annual membership to get the best deal.
