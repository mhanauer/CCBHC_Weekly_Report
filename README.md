# CCBHC_Weekly_Report
setwd("P:/Evaluation/CCBHC IN/Data")
ccbhc_adult = read.csv("8.2 Adult data.csv", header = TRUE, na.strings = c(-1:-11))

head(ccbhc_adult, 10)
adult_base = subset(ccbhc_adult, ccbhc_adult$InterviewType_07 == 1)

library(descr)
library(Hmisc)
library(prettyR)

## Count of the number of people who did not answer anything for race
all_race_adult = data.frame(RaceWhite = adult_base$RaceWhite, RaceBlack = adult_base$RaceBlack, Asian = adult_base$RaceAsian, HispanicLatino = adult_base$HispanicLatino, RaceAmericanIndian = adult_base$RaceAmericanIndian, RaceNativeHawaiian = adult_base$RaceNativeHawaiian)
all_race_adult_missing = rowSums(is.na(all_race_adult))
all_race_adult_missing = ifelse(all_race_adult_missing == 6, 1, 0)
describe.factor(all_race_adult_missing)


###Count the number of multi-racial people
all_race_adult_complete = na.omit(all_race_adult)
multi_race = apply(all_race_adult_complete, 1, sum)
multi_race = ifelse(multi_race > 1, 1, 0)
describe.factor(multi_race)


White_Data_complete=na.omit(adult_base$RaceWhite)
White_Data_complete
describe.factor(White_Data_complete)

Black_Data_complete=na.omit(adult_base$RaceBlack)
describe.factor(Black_Data_complete)

Asian_Data_complete=na.omit(adult_base$RaceAsian)
describe.factor(Asian_Data_complete)

HispanicLatino_Data_complete=na.omit(adult_base$HispanicLatino)
describe.factor(HispanicLatino_Data_complete)

AmericanIndian_Data_complete=na.omit(adult_base$RaceAmericanIndian)
describe.factor(AmericanIndian_Data_complete)

NativeHawaiian_Data_complete=na.omit(adult_base$RaceNativeHawaiian)
describe.factor(NativeHawaiian_Data_complete)

describe.factor(adult_base$Gender)

describe.factor(adult_base$SexualIdentity)

describe.factor(adult_base$OverallHealth)

dim(ccbhc_adult)[1]



###YOUTH

setwd("P:/Evaluation/CCBHC IN/Data")
ccbhc_youth = read.csv("8.2 Youth data.csv", header = TRUE, na.strings = c(-1:-11))

youth_base = subset(ccbhc_youth, ccbhc_youth$InterviewType_07 == 1)

all_race_youth = data.frame(RaceWhite = youth_base$RaceWhite, RaceBlack = youth_base$RaceBlack, Asian = youth_base$RaceAsian, HispanicLatino = youth_base$HispanicLatino, RaceAmericanIndian = youth_base$RaceAmericanIndian, RaceNativeHawaiian = youth_base$RaceNativeHawaiian)
all_race_youth_missing = rowSums(is.na(all_race_youth))
all_race_youth_missing = ifelse(all_race_youth_missing == 6, 1, 0)
describe.factor(all_race_youth_missing)


all_race_youth_complete = na.omit(all_race_youth)
multi_race = apply(all_race_youth_complete, 1, sum)
multi_race = ifelse(multi_race > 1, 1, 0)
describe.factor(multi_race)

White_Data_youth=na.omit(youth_base$RaceWhite)
describe.factor(White_Data_youth)
#TEST!!!!!!!!!!!!!!!!!!!1
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

describe.factor(youth_base$Gender)

describe.factor(youth_base$OverallHealth)
