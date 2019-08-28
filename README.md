# CCBHC_Weekly_Report
setwd("P:/Evaluation/CCBHC IN/Data")
ccbhc_adult = read.csv("8.27 Adult data.csv", header = TRUE, na.strings = c(-1:-11))

head(ccbhc_adult, 10)
adult_base = subset(ccbhc_adult, ccbhc_adult$InterviewType_07 == 1)

library(descr)
library(Hmisc)
library(prettyR)

## Count of the number of people who did not answer anything for race
all_race_adult = data.frame(RaceWhite = adult_base$RaceWhite, RaceBlack = adult_base$RaceBlack, Asian = adult_base$RaceAsian, HispanicLatino = adult_base$HispanicLatino, RaceAmericanIndian = adult_base$RaceAmericanIndian, RaceNativeHawaiian = adult_base$RaceNativeHawaiian, RaceAlaskaNative = adult_base$RaceAlaskaNative)
all_race_adult_missing = rowSums(is.na(all_race_adult))
all_race_adult_missing = ifelse(all_race_adult_missing == 6, 1, 0)
describe.factor(all_race_adult_missing)


###Count the number of multi-racial people
all_race_adult_complete = na.omit(all_race_adult)
multi_race = apply(all_race_adult_complete, 1, sum)
multi_race = ifelse(multi_race > 1, 1, 0)
describe.factor(multi_race)

###Count for White
White_Data_complete=na.omit(adult_base$RaceWhite)
describe.factor(White_Data_complete)

###Count for Black/African American
Black_Data_complete=na.omit(adult_base$RaceBlack)
describe.factor(Black_Data_complete)

###Count for Asian
Asian_Data_complete=na.omit(adult_base$RaceAsian)
describe.factor(Asian_Data_complete)

###Count for Hispanic/Latino
HispanicLatino_Data_complete=na.omit(adult_base$HispanicLatino)
describe.factor(HispanicLatino_Data_complete)

###Count for American Indian
AmericanIndian_Data_complete=na.omit(adult_base$RaceAmericanIndian)
describe.factor(AmericanIndian_Data_complete)

###Count for Native Hawaiian
NativeHawaiian_Data_complete=na.omit(adult_base$RaceNativeHawaiian)
describe.factor(NativeHawaiian_Data_complete)

###Count for Alaska Native
AlaskaNative_Data_complete=na.omit(adult_base$RaceAlaskaNative)
describe.factor(AlaskaNative_Data_complete)

###Count for Gender
###1 = male, 2 = female, 3 = transgender, 4= other (specify)
describe.factor(adult_base$Gender)

###Count for Sexual Identity
###1 = heterosexual, 2 = gay/lesbian, 3 = bisexual, 4= other (specify)
describe.factor(adult_base$SexualIdentity)

###Count for rating of overall health
###1 = Excellent, 2 = Very Good, 3 = Good, 4 = Fair, 5 = Poor
describe.factor(adult_base$OverallHealth)

###Number of total adult people
dim(adult_base)[1]

 

###YOUTH

setwd("P:/Evaluation/CCBHC IN/Data")
ccbhc_youth = read.csv("8.27 Youth data.csv", header = TRUE, na.strings = c(-1:-11))

youth_base = subset(ccbhc_youth, ccbhc_youth$InterviewType_07 == 1)

## Count of the number of people who did not answer anything for race
all_race_youth = data.frame(RaceWhite = youth_base$RaceWhite, RaceBlack = youth_base$RaceBlack, Asian = youth_base$RaceAsian, HispanicLatino = youth_base$HispanicLatino, RaceAmericanIndian = youth_base$RaceAmericanIndian, RaceNativeHawaiian = youth_base$RaceNativeHawaiian, RaceAlaskaNative = youth_base$RaceAlaskaNative)
all_race_youth_missing = rowSums(is.na(all_race_youth))
all_race_youth_missing = ifelse(all_race_youth_missing == 6, 1, 0)
describe.factor(all_race_youth_missing)


all_race_youth_complete = na.omit(all_race_youth)
multi_race = apply(all_race_youth_complete, 1, sum)
multi_race = ifelse(multi_race > 1, 1, 0)
describe.factor(multi_race)



White_Data_youth=na.omit(youth_base$RaceWhite)
describe.factor(White_Data_youth)

Black_Data_youth=na.omit(youth_base$RaceBlack)
describe.factor(Black_Data_youth)

Asian_Data_youth=na.omit(youth_base$RaceAsian)
describe.factor(Asian_Data_youth)

HispanicLatino_Data_youth=na.omit(youth_base$HispanicLatino)
describe.factor(HispanicLatino_Data_youth)

AmericanIndian_Data_youth=na.omit(youth_base$RaceAmericanIndian)
describe.factor(AmericanIndian_Data_youth)

NativeHawaiian_Data_youth=na.omit(youth_base$RaceNativeHawaiian)
describe.factor(NativeHawaiian_Data_youth)

AlaskaNative_Data_youth=na.omit(youth_base$RaceAlaskaNative)
describe.factor(AlaskaNative_Data_youth)

###Count for Gender
###1 = male, 2 = female, 3 = transgender, 4= other (specify)
describe.factor(youth_base$Gender)

###Count for rating of overall health
###1 = Excellent, 2 = Very Good, 3 = Good, 4 = Fair, 5 = Poor
describe.factor(youth_base$OverallHealth)

#### Grant Summary Reports
## Current enrollments
dim(adult_base)[1]+dim(youth_base)[1]
## Enrollments this quarter
library(lubridate)
adult_base$InterviewDate = mdy(adult_base$InterviewDate)
youth_base$InterviewDate = mdy(youth_base$InterviewDate)
adult_base_quarter = subset(adult_base, InterviewDate >= "2018-04-01" & InterviewDate < "2019-07-01")
youth_base_quarter = subset(youth_base, InterviewDate >= "2018-04-01" & InterviewDate < "2019-07-01")
## Number this quarter
dim(adult_base_quarter)[1]+dim(youth_base_quarter)[1]






