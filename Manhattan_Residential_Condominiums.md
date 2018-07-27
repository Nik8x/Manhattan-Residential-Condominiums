Manhattan Residential Condominiums
================
Niket
July 26, 2018

``` r
manhtn18 <- read.csv(file.choose(), header = TRUE, skip = 1, na.strings = c("NA", "", " ", "."))
```

``` r
# remove first empty row
manhtn18 <- manhtn18[-1,]
```

``` r
str(manhtn18)
```

    ## 'data.frame':    2964 obs. of  60 variables:
    ##  $ Boro.Block.Lot                : Factor w/ 1323 levels "1-00016-7505",..: 927 296 766 505 553 773 849 783 339 480 ...
    ##  $ Condominium                   : Factor w/ 1361 levels "0001-R1","0003-R1",..: 1 2 3 4 5 6 7 8 9 10 ...
    ##  $ Address                       : Factor w/ 1336 levels "1 BOND STREET",..: 835 1163 192 1254 292 1187 1280 112 1233 853 ...
    ##  $ Neighborhood                  : Factor w/ 38 levels "ALPHABET CITY",..: 31 11 24 26 24 22 31 22 12 26 ...
    ##  $ Building.Class                : Factor w/ 4 levels "R2  -WALK-UP",..: 2 2 2 2 2 2 2 2 3 2 ...
    ##  $ Total.Units                   : int  308 70 183 109 182 226 16 230 20 113 ...
    ##  $ Year.Built                    : int  1965 1966 1963 1924 1930 1973 1925 1975 1910 1961 ...
    ##  $ Gross.SqFt                    : Factor w/ 1355 levels "1,158","1,171,064",..: 961 1242 206 262 356 925 1037 795 989 1271 ...
    ##  $ Estimated.Gross.Income        : Factor w/ 1361 levels "1,001,925","1,001,938",..: 581 809 1090 1089 262 598 494 400 229 830 ...
    ##  $ Gross.Income.per.SqFt         : num  45.9 49.9 48.8 43.5 54.5 ...
    ##  $ Estimated.Expense             : Factor w/ 1360 levels "1,001,404","1,005,144",..: 1183 177 412 529 141 1250 1193 1101 1091 26 ...
    ##  $ Expense.per.SqFt              : num  15.07 19.5 14.25 18.18 7.63 ...
    ##  $ Net.Operating.Income          : Factor w/ 1361 levels "1,001,564","1,002,036",..: 327 451 865 785 1237 341 195 281 79 646 ...
    ##  $ Full.Market.Value             : Factor w/ 1356 levels "1,057,997","1,098,001",..: 180 455 788 706 1204 245 201 1343 1329 567 ...
    ##  $ Market.Value.per.SqFt         : num  248 245 278 204 378 ...
    ##  $ Boro.Block.Lot.1              : Factor w/ 534 levels "1-00016-0180",..: 330 108 318 175 224 303 330 303 130 191 ...
    ##  $ Address.1                     : Factor w/ 534 levels "10 STANTON STREET",..: 55 464 359 343 301 224 55 224 61 103 ...
    ##  $ Neighborhood.1                : Factor w/ 37 levels "ALPHABET CITY",..: 30 11 30 26 24 23 30 23 12 26 ...
    ##  $ Building.Class.1              : Factor w/ 12 levels "C1  -WALK-UP",..: 9 5 7 9 7 9 9 9 8 7 ...
    ##  $ Total.Units.1                 : int  181 27 20 136 68 167 181 167 50 39 ...
    ##  $ Year.Built.1                  : int  1973 1910 1915 1955 1961 1983 1973 1983 1896 1924 ...
    ##  $ Gross.SqFt.1                  : Factor w/ 519 levels "10,008","10,104",..: 306 171 193 80 405 298 306 298 304 344 ...
    ##  $ Estimated.Gross.Income.1      : Factor w/ 1319 levels "1,001,475","1,002,750",..: 415 27 1233 778 596 434 399 418 92 349 ...
    ##  $ Gross.Income.per.SqFt.1       : num  44.6 50.6 40.1 36.7 53.3 ...
    ##  $ Estimated.Expense.1           : Factor w/ 1319 levels "1,003,190","1,003,217",..: 861 911 528 380 964 997 671 992 809 948 ...
    ##  $ Expense.per.SqFt.1            : num  13.88 20.91 11.06 16.8 8.77 ...
    ##  $ Net.Operating.Income.1        : Factor w/ 1320 levels "1,001,011","1,001,539",..: 318 1013 1042 445 416 335 313 316 1185 201 ...
    ##  $ Full.Market.Value.1           : Factor w/ 525 levels "1,065,000","1,076,000",..: 483 340 378 210 511 482 483 482 517 466 ...
    ##  $ Market.Value.per.SqFt.1       : num  217 228 236 196 168 ...
    ##  $ Distance.from.Condo.in.miles  : num  0.24 0.14 0.47 0.18 0.37 0.54 0.47 0.21 0.05 0.22 ...
    ##  $ Boro.Block.Lot.2              : Factor w/ 579 levels "1-00016-0180",..: 332 112 241 200 240 359 332 359 137 183 ...
    ##  $ Address.2                     : Factor w/ 579 levels "10 WEST 74 STREET",..: 244 495 318 406 379 61 244 61 526 568 ...
    ##  $ Neighborhood.2                : Factor w/ 38 levels "ALPHABET CITY",..: 23 11 24 26 24 31 23 31 12 26 ...
    ##  $ Building.Class.2              : Factor w/ 12 levels "C1  -WALK-UP",..: 9 8 7 9 7 9 9 9 8 7 ...
    ##  $ Total.Units.2                 : int  167 54 68 119 126 181 167 181 53 77 ...
    ##  $ Year.Built.2                  : int  1983 1900 1961 1950 1912 1973 1983 1973 1979 1930 ...
    ##  $ Gross.SqFt.2                  : Factor w/ 557 levels "10,008","10,060",..: 306 411 425 45 481 320 306 320 416 356 ...
    ##  $ Estimated.Gross.Income.2      : Factor w/ 1331 levels "1,001,000","1,002,707",..: 432 544 562 899 781 454 421 445 332 390 ...
    ##  $ Gross.Income.per.SqFt.2       : num  45.9 49.9 48.8 43.7 58.4 ...
    ##  $ Estimated.Expense.2           : Factor w/ 1329 levels "1,003,844","1,004,292",..: 889 1323 1234 168 1235 1043 700 1038 1259 1007 ...
    ##  $ Expense.per.SqFt.2            : num  15.1 19.5 14.2 17.3 10.2 ...
    ##  $ Net.Operating.Income.2        : Factor w/ 1330 levels "1,000,642","1,001,985",..: 1266 218 292 568 604 338 1262 330 1258 204 ...
    ##  $ Full.Market.Value.2           : Factor w/ 566 levels "1,030,000","1,074,000",..: 515 93 549 256 137 516 515 516 95 103 ...
    ##  $ Market.Value.per.SqFt.2       : num  232 268 168 254 233 ...
    ##  $ Distance.from.Condo.in.miles.1: num  0.28 0.15 0.52 0.1 0.39 0.89 0.44 0.53 0.06 0.32 ...
    ##  $ Boro.Block.Lot.3              : Factor w/ 540 levels "1-00016-0020",..: 331 116 228 174 226 331 331 331 130 204 ...
    ##  $ Address.3                     : Factor w/ 540 levels "10 WEST 138 STREET",..: 129 27 348 370 359 129 129 129 315 169 ...
    ##  $ Neighborhood.3                : Factor w/ 36 levels "ALPHABET CITY",..: 29 12 24 26 24 29 29 29 12 26 ...
    ##  $ Building.Class.3              : Factor w/ 12 levels "C1  -WALK-UP",..: 9 5 7 9 8 9 9 9 5 7 ...
    ##  $ Total.Units.3                 : int  103 58 126 160 48 103 103 103 31 34 ...
    ##  $ Year.Built.3                  : int  1962 1910 1912 1950 1940 1962 1962 1962 1920 1925 ...
    ##  $ Gross.SqFt.3                  : Factor w/ 516 levels "1,881,621","10,008",..: 146 294 452 104 315 146 146 146 149 159 ...
    ##  $ Estimated.Gross.Income.3      : Factor w/ 1251 levels "1,000,295","1,001,805",..: 1182 256 673 906 385 345 1119 332 962 8 ...
    ##  $ Gross.Income.per.SqFt.3       : num  52.9 49.8 53.9 43.5 54.5 ...
    ##  $ Estimated.Expense.3           : Factor w/ 1252 levels "1,000,186","1,003,190",..: 692 1138 40 443 633 715 446 710 364 630 ...
    ##  $ Expense.per.SqFt.3            : num  18.15 20.76 15.69 18.18 7.63 ...
    ##  $ Net.Operating.Income.3        : Factor w/ 1253 levels "1,000,810","1,004,293",..: 958 1250 390 521 217 1051 944 963 773 1076 ...
    ##  $ Full.Market.Value.3           : Factor w/ 534 levels "1,023,000","1,030,000",..: 366 70 130 301 77 366 366 366 395 464 ...
    ##  $ Market.Value.per.SqFt.3       : num  230 339 233 206 330 ...
    ##  $ Distance.from.Condo.in.miles.2: num  0.65 0.19 0.52 0.14 0.45 1.23 0.71 0.9 0.1 0.32 ...

We should only include columns with Brooklyn listings without comparable rentals, which is 1 to 15 columns

``` r
manhtn <- manhtn18[,1:15]
```

------------------------------------------------------------------------

------------------------------------------------------------------------

``` r
summary(manhtn$Building.Class)
```

    ##  R2  -WALK-UP R4  -ELEVATOR  R9  -CONDOPS  RR  -CONRENT          NA's 
    ##            84           998           177           102          1603

R2 CONDO; RESIDENTIAL UNIT IN WALK-UP BLDG. R4 CONDO; RESIDENTIAL UNIT IN ELEVATOR BLDG. R9 CO-OP WITHIN A CONDOMINIUM RR CONDO RENTALS

Elevator or walk-up (but walk-up must be lower than 3rd floor) and Must be condominium (not co-op or condop) so we should drop R9 and Missing values(NA's)

``` r
manhtn <- manhtn[!manhtn$Building.Class == "R9  -CONDOPS",]
manhtn <- manhtn[!is.na(manhtn$Building.Class),]
# manhtn_1 <- manhtn_1[!manhtn$Building.Class == "RR  -CONRENT",]
```

``` r
summary(manhtn$Building.Class)
```

    ##  R2  -WALK-UP R4  -ELEVATOR  R9  -CONDOPS  RR  -CONRENT 
    ##            84           998             0           102

------------------------------------------------------------------------

------------------------------------------------------------------------

Market Value: less than $3,500,000

``` r
manhtn$Full.Market.Value <- as.numeric(gsub(",", "", manhtn$Full.Market.Value)) #As the numerical values in Price column are comma seperated, remove comma

summary(manhtn$Full.Market.Value)
```

    ##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
    ##    210000   5344249  13317503  28204331  33982746 346132985

``` r
manhtn <- manhtn[manhtn$Full.Market.Value < 3500000,]

summary(manhtn$Full.Market.Value)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  210000 1497502 2221000 2145594 2859000 3488998

------------------------------------------------------------------------

------------------------------------------------------------------------

Price per square foot: less than $2,000

``` r
# manhtn$Market.Value.per.SqFt <- as.numeric(gsub(",","", manhtn$Market.Value.per.SqFt)) #As the numerical values in Price.per.sq.foot column are comma seperated, remove comma

summary(manhtn$Market.Value.per.SqFt)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   47.55  146.82  198.99  205.49  261.82  492.96

All the data is under $2,000, but we can still clean for future purposes

``` r
manhtn <- manhtn[manhtn$Market.Value.per.SqFt < 2000,]

summary(manhtn$Market.Value.per.SqFt)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   47.55  146.82  198.99  205.49  261.82  492.96

------------------------------------------------------------------------

------------------------------------------------------------------------

Close by Location: Manhattan south of 96th Street

``` r
manhtn$Address <- as.character(manhtn$Address)
```

Add NY to all the address

``` r
manhtn$Address <- paste0(manhtn$Address, " NY")
```

``` r
# install.packages("ggmap") # an R interface to the Google Maps API
```

``` r
sum(is.na(manhtn)) #check for missing values
```

    ## [1] 0

``` r
# calculate distance between two place names
# we added NY to the address so that it does not pick location from another state
library(ggmap)
```

    ## Warning: package 'ggmap' was built under R version 3.4.4

    ## Loading required package: ggplot2

``` r
dist_96 <- mapdist(from = manhtn$Address, to = "Manhattan south of 96th Street")
```

    ## by using this function you are agreeing to the terms at :

    ## http://code.google.com/apis/maps/documentation/distancematrix/

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1+ELDRIDGE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=101+ALLEN+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=102+MADISON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=103+AVENUE+A+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1049+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=105+3+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=107+AVENUE+A+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=107+EAST+BROADWAY+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=108+EAST+116+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=108+WEST+138+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=11+MONROE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=110+EAST+116+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=111+WEST+113+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=111+WEST+28+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1115+1+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=112+RIVINGTON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=113+ELDRIDGE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=114+EAST+27+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=117+EAST+102+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1175+YORK+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=133+NORFOLK+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=139+WEST+126+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=14+EAST+77+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1405+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=142+HENRY+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=147+WEST+142+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=149+EAST+62+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=15+EAST+15+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=15+ST+MARK'S+PLACE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=151+ALLEN+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=151+EAST+20+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=155+WEST+126+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=157+LUDLOW+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=158+EAST+100+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=159+WEST+126+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=161+WEST+133+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1628+2+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1630+MADISON+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=164+WEST+83+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=165+EAST+104+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=169+EAST+102+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=171+WEST+107+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1724+2+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=173+EAST+102+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=175+PAYSON+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=179+EAST+78+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=18+ELDRIDGE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=18+WEST+129+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=186+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=186+EAST+2+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=1908+3+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=195+PRINCE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=199+PRINCE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2+AMSTERDAM+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2+PRINCE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=20+RENWICK+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=200+WEST+78+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=201+WEST+112+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=203+WEST+112+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2056+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=206+EAST+124+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=207+EAST+120+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2072+FRED+DOUGLASS+BOULEVARD+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2082+FREDERICK+DOUGLASS+BLVD.+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=21+EAST+74+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=211+EAST+3+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=211+WEST+88+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=212+AVENUE+B+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=212+EAST+70+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2141+2+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=217+EAST+5+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=218+WEST+14+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=220+WEST+111+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=225+EAST+111+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2257+ADAM+C.+POWELL+BOULEVARD+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=227+WEST+116+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2279+3+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=229+EAST+2+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=229+WEST+97+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2292+FREDERICK+DOUGLASS+BLVD.+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=23+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=23+EAST+128+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=232+EAST+118+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=234+WEST+148+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=237+EAST+24+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=237+EAST+88+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=2373+ADAM+C.+POWELL+BOULEVARD+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=239+EAST+10+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=239+WEST+135+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=24+WEST+131+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=24+WEST+30+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=240+EAST+15+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=240+EAST+HOUSTON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=241+ELDRIDGE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=242+EAST+15+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=245+WEST+115+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=25+WEST+131+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=252+WEST+123+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=256+WEST+123+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=26+LUDLOW+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=26+WEST+97+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=262+MOTT+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=266+EAST+10+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=266+WEST+115+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=27+GREAT+JONES+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=272+MANHATTAN+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=273+WEST+136+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=276+WEST+119+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=28+PERRY+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=297+WEST+137+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=3+WEEHAWKEN+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=3+WEST+122+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=30+RUTGERS+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=30+WEST+9+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=302+BROOME+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=302+EAST+19+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=303+WEST+146+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=304+WEST+114+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=304+WEST+115+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=306+MOTT+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=311+AMSTERDAM+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=311+EAST+104+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=316+WEST+116+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=32+WEST+132+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=323+EAST+89+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=328+EAST+119+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=340+CABRINI+BOULEVARD+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=344+EAST+50+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=345+GREENWICH+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=346+EAST+119+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=348+EAST+89+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=355+GREENWICH+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=360+CENTRAL+PARK+WEST+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=362+ST.+NICHOLAS+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=362+WEST+127+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=368+ST.+NICHOLAS+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=371+WEST+126+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=38+STUYVESANT+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=40+WEST+76+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=411+MANHATTAN+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=414+EAST+120+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=44+MARKET+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=443+WEST+151+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=461+WEST+150+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=469+WEST+152+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=47+EAST+19+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=47+GREAT+JONES+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=47+WEST+131+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=479+WEST+152+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=496+LA+GUARDIA+PLACE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=5+WEST+127+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=50+EAST+129+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=50+HUDSON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=51+EAST+128+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=51+MERCER+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=513+HUDSON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=519+WEST+135+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=529+WEST+147+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=53+WEST+76+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=5420+WEST+BROADWAY+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=55+WEST+131+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=55+WEST+84+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=58+WEST+106+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=58+WEST+129+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=597+BROADWAY+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=61+LENOX+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=62+RIVINGTON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=625+EAST+11+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=631+EAST+9+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=65+NORTH+MOORE+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=680+RIVERSIDE+DRIVE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=69+WEST+106+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=7+LISPENARD+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=7+WEST+131+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=74+WEST+85+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=75+ALLEN+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=77+ALLEN+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=77+HORATIO+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=8+WEST+65+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=807+RIVERSIDE+DRIVE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=8077+5+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=828+7+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=845+2+AVENUE+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=87+BOWERY+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=87+ELIZABETH+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=95+MADISON+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

    ## Information from URL : http://maps.googleapis.com/maps/api/distancematrix/json?origins=95+VANDAM+STREET+NY&destinations=Manhattan+south+of+96th+Street&mode=driving&sensor=false

``` r
# fill distance from 96th street in our data
manhtn$Distance.to.96.Street <- dist_96$miles[match(manhtn$Address, dist_96$from)]
```

``` r
# Looking at the distance
summary(manhtn$Distance.to.96.Street)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  0.3256  1.9105  2.9579  4.0892  6.3998 14.4898

------------------------------------------------------------------------

------------------------------------------------------------------------

Rental yield of 2% or more = Net Income divided by Total Price

``` r
# Rename BROOKLYN.Ã.Â.Â..CONDOMINIUMS.COMPARABLE.PROPERTIES.Ã.Â.Â..Net.Operating.Income to Net.Operating.Income
# colnames(manhtn_1)[colnames(manhtn_1)=="BROOKLYN.Ã.Â.Â..CONDOMINIUMS.COMPARABLE.PROPERTIES.Ã.Â.Â..Net.Operating.Income"] <- "Net.Operating.Income"
```

``` r
manhtn$Net.Operating.Income <- as.numeric(gsub(",", "", manhtn$Net.Operating.Income)) #As the numerical values in Price.per.sq.foot column are comma seperated, remove comma

summary(manhtn$Net.Operating.Income)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   26221  190549  277229  270090  359359  467005

``` r
manhtn$Rental.Yield <- ((manhtn$Net.Operating.Income / manhtn$Full.Market.Value) * 100) 
```

``` r
manhtn <- manhtn[manhtn$Rental.Yield >= 2,] # Rental yield of 2% or more

summary(manhtn$Rental.Yield)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   12.41   12.42   12.45   12.59   12.68   14.15

------------------------------------------------------------------------

------------------------------------------------------------------------

Look for the closest locations(under 5 miles) order by Market Value

``` r
distance_order <- manhtn[with(manhtn,order(Distance.to.96.Street)),]
distance_order <- distance_order[distance_order$Distance.to.96.Street < 5,]
```

``` r
price_order <- distance_order[with(distance_order, order(Full.Market.Value)),]
price_order[1:30,]
```

    ##      Boro.Block.Lot Condominium                          Address
    ## 533    1-01151-7501     0759-R3            2 AMSTERDAM AVENUE NY
    ## 351    1-01869-7501     0516-R2            229 WEST 97 STREET NY
    ## 421    1-01025-7501     0606-R2                  828 7 AVENUE NY
    ## 453    1-01458-7502     0645-R2              1175 YORK AVENUE NY
    ## 976    1-02067-7501     1823-R1           469 WEST 152 STREET NY
    ## 1223   1-01209-7502     2359-R1         360 CENTRAL PARK WEST NY
    ## 466    1-01632-7501     0666-R1           165 EAST 104 STREET NY
    ## 578    1-01729-7501     0846-R2            47 WEST 131 STREET NY
    ## 298    1-01630-7501     0441-R1           169 EAST 102 STREET NY
    ## 299    1-01630-7501     0441-R2           173 EAST 102 STREET NY
    ## 729    1-01728-7501     1280-R2            25 WEST 131 STREET NY
    ## 856    1-01828-7503     1540-R1  2072 FRED DOUGLASS BOULEVARD NY
    ## 730    1-01728-7501     1280-R3            32 WEST 132 STREET NY
    ## 914    1-01828-7505     1684-R1 2082 FREDERICK DOUGLASS BLVD. NY
    ## 224    1-01676-7501     0342-R1           311 EAST 104 STREET NY
    ## 569    1-01497-7501     0825-R2                 1049 5 AVENUE NY
    ## 142    1-01397-7502     0230-R1            149 EAST 62 STREET NY
    ## 732    1-01614-7501     1285-R1           1630 MADISON AVENUE NY
    ## 935    1-01807-7501     1732-R1           414 EAST 120 STREET NY
    ## 500    1-01660-7501     0716-R1                 2141 2 AVENUE NY
    ## 1032   1-01917-7501     1926-R1 2257 ADAM C. POWELL BOULEVARD NY
    ## 891    1-01627-7501     1628-R1           158 EAST 100 STREET NY
    ## 728    1-01728-7501     1280-R1            24 WEST 131 STREET NY
    ## 849    1-01753-7501     1525-R1            23 EAST 128 STREET NY
    ## 577    1-01729-7501     0846-R1            55 WEST 131 STREET NY
    ## 1259   1-01846-7504     2462-R1          272 MANHATTAN AVENUE NY
    ## 1126   1-01795-7502     2125-R1           346 EAST 119 STREET NY
    ## 1283   1-01643-7502     2534-R1           110 EAST 116 STREET NY
    ## 904    1-01831-7501     1657-R1           245 WEST 115 STREET NY
    ## 983    1-01928-7503     1831-R2           256 WEST 123 STREET NY
    ##                  Neighborhood Building.Class Total.Units Year.Built
    ## 533   UPPER WEST SIDE (59-79)  R4  -ELEVATOR           1       1991
    ## 351  UPPER WEST SIDE (96-116)  R4  -ELEVATOR           1       1901
    ## 421              MIDTOWN WEST  R4  -ELEVATOR           3       1916
    ## 453   UPPER EAST SIDE (59-79)  R4  -ELEVATOR           4       1958
    ## 976              HARLEM-UPPER  R4  -ELEVATOR           6       1920
    ## 1223  UPPER WEST SIDE (79-96)  R4  -ELEVATOR           2       1929
    ## 466               HARLEM-EAST   R2  -WALK-UP          12       1910
    ## 578            HARLEM-CENTRAL   R2  -WALK-UP           4       1880
    ## 298               HARLEM-EAST   R2  -WALK-UP          17       1920
    ## 299               HARLEM-EAST   R2  -WALK-UP          17       1920
    ## 729            HARLEM-CENTRAL   R2  -WALK-UP           5       1900
    ## 856            HARLEM-CENTRAL   R2  -WALK-UP          13       1900
    ## 730            HARLEM-CENTRAL   R2  -WALK-UP           5       1900
    ## 914            HARLEM-CENTRAL   R2  -WALK-UP          14       1900
    ## 224               HARLEM-EAST   R2  -WALK-UP          12       1900
    ## 569   UPPER EAST SIDE (79-96)  R4  -ELEVATOR          12       1928
    ## 142   UPPER EAST SIDE (59-79)  R4  -ELEVATOR          12       1915
    ## 732  UPPER EAST SIDE (96-110)  R4  -ELEVATOR          11       2003
    ## 935               HARLEM-EAST  R4  -ELEVATOR          12       2006
    ## 500               HARLEM-EAST   R2  -WALK-UP          10       1910
    ## 1032           HARLEM-CENTRAL  R4  -ELEVATOR          10       2005
    ## 891               HARLEM-EAST  R4  -ELEVATOR          12       2004
    ## 728            HARLEM-CENTRAL   R2  -WALK-UP           5       1900
    ## 849            HARLEM-CENTRAL  R4  -ELEVATOR          12       2005
    ## 577            HARLEM-CENTRAL  R4  -ELEVATOR          34       1910
    ## 1259         MANHATTAN VALLEY  R4  -ELEVATOR           9       1920
    ## 1126              HARLEM-EAST  R4  -ELEVATOR          11       2007
    ## 1283              HARLEM-EAST   RR  -CONRENT          12       1910
    ## 904            HARLEM-CENTRAL   R2  -WALK-UP          20       1900
    ## 983            HARLEM-CENTRAL   R2  -WALK-UP           6       1910
    ##      Gross.SqFt Estimated.Gross.Income Gross.Income.per.SqFt
    ## 533         945                 45,398                 48.04
    ## 351       1,466                 55,195                 37.65
    ## 421       1,567                 82,753                 52.81
    ## 453       2,764                119,709                 43.31
    ## 976       6,390                189,016                 29.58
    ## 1223      2,632                123,441                 46.90
    ## 466       7,690                212,167                 27.59
    ## 578       5,224                167,168                 32.00
    ## 298       9,590                221,241                 23.07
    ## 299       9,590                227,283                 23.70
    ## 729       8,320                197,267                 23.71
    ## 856       6,866                221,085                 32.20
    ## 730       8,640                204,854                 23.71
    ## 914       6,846                254,192                 37.13
    ## 224       6,092                244,655                 40.16
    ## 569       3,812                230,588                 60.49
    ## 142       4,777                230,060                 48.16
    ## 732       7,742                258,041                 33.33
    ## 935       9,745                252,785                 25.94
    ## 500       6,504                265,753                 40.86
    ## 1032     11,679                300,501                 25.73
    ## 891       6,342                263,256                 41.51
    ## 728       8,800                255,816                 29.07
    ## 849      12,018                283,144                 23.56
    ## 577      28,408                547,138                 19.26
    ## 1259      8,999                256,022                 28.45
    ## 1126     12,026                304,378                 25.31
    ## 1283      7,322                349,699                 47.76
    ## 904       7,852                298,690                 38.04
    ## 983       6,601                277,770                 42.08
    ##      Estimated.Expense Expense.per.SqFt Net.Operating.Income
    ## 533             11,642            12.32                33756
    ## 351              9,148             6.24                46047
    ## 421              9,715             6.20                73038
    ## 453             45,026            16.29                74683
    ## 976            106,330            16.64                82686
    ## 1223            39,533            15.02                83908
    ## 466            123,963            16.12                88204
    ## 578             76,427            14.63                90741
    ## 298            126,013            13.14                95228
    ## 299            125,054            13.04               102229
    ## 729             78,874             9.48               118393
    ## 856             87,885            12.80               133200
    ## 730             61,430             7.11               143424
    ## 914            107,003            15.63               147189
    ## 224             96,193            15.79               148462
    ## 569             81,691            21.43               148897
    ## 142             80,588            16.87               149472
    ## 732            104,285            13.47               153756
    ## 935             90,823             9.32               161962
    ## 500            106,601            16.39               159152
    ## 1032           121,812            10.43               178689
    ## 891             91,071            14.36               172185
    ## 728             78,144             8.88               177672
    ## 849             99,028             8.24               184116
    ## 577            355,668            12.52               191470
    ## 1259            76,312             8.48               179710
    ## 1126           114,006             9.48               190372
    ## 1283           160,498            21.92               189201
    ## 904            107,965            13.75               190725
    ## 983             84,493            12.80               193277
    ##      Full.Market.Value Market.Value.per.SqFt Distance.to.96.Street
    ## 533             272000                287.83             1.8511506
    ## 351             370000                252.39             0.3256136
    ## 421             588000                375.24             3.3710950
    ## 453             601000                217.44             3.6898732
    ## 976             651999                102.03             4.7512244
    ## 1223            675000                256.46             0.3653832
    ## 466             689002                 89.60             1.9232330
    ## 578             719998                137.83             2.5110774
    ## 298             725998                 75.70             1.5168374
    ## 299             783000                 81.65             1.5261584
    ## 729             906000                108.89             2.5670034
    ## 856            1057997                154.09             1.1763102
    ## 730            1098001                127.08             2.9578640
    ## 914            1180004                172.36             1.2005448
    ## 224            1194002                196.00             2.2463610
    ## 569            1198002                314.27             1.4926028
    ## 142            1202996                251.83             3.0119258
    ## 732            1225001                158.23             1.6504384
    ## 935            1255996                128.89             3.0249752
    ## 500            1281001                196.96             2.1133814
    ## 1032           1385000                118.59             2.3818262
    ## 891            1385998                218.54             1.6274466
    ## 728            1397000                158.75             2.5676248
    ## 849            1406999                117.07             2.9050450
    ## 577            1409998                 49.63             2.5179128
    ## 1259           1411999                156.91             1.0271742
    ## 1126           1472005                122.40             2.6633204
    ## 1283           1523000                208.00             2.1202168
    ## 904            1531000                194.98             1.3384956
    ## 983            1555001                235.57             1.7585620
    ##      Rental.Yield
    ## 533      12.41029
    ## 351      12.44514
    ## 421      12.42143
    ## 453      12.42646
    ## 976      12.68192
    ## 1223     12.43081
    ## 466      12.80170
    ## 578      12.60295
    ## 298      13.11684
    ## 299      13.05607
    ## 729      13.06766
    ## 856      12.58983
    ## 730      13.06228
    ## 914      12.47360
    ## 224      12.43398
    ## 569      12.42878
    ## 142      12.42498
    ## 732      12.55150
    ## 935      12.89510
    ## 500      12.42403
    ## 1032     12.90173
    ## 891      12.42318
    ## 728      12.71811
    ## 849      13.08572
    ## 577      13.57945
    ## 1259     12.72735
    ## 1126     12.93284
    ## 1283     12.42292
    ## 904      12.45754
    ## 983      12.42938

------------------------------------------------------------------------

------------------------------------------------------------------------
