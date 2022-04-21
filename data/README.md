## Datasets

We will introduce the datasets we used for this study, how and where the data were acquired

### 1. [Multiple Listing Service House Price Index](https://www.crea.ca/housing-market-stats/mls-home-price-index/hpi-tool/)

The Multiple Listing Service House Price Index dataset from Statistics Canada provides information of average home price and price index for various different types of real estates (Ex. Townhouse, apartment, etc) at different time point. The dataset includes such information for numerous cities, as well as Canada on an aggregate level.

### 2. [Canada Mortgage and Housing Corporation, Absorptions and Unabsorbed Inventory, Newly Completed Dwellings](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=3410014901)

The Canada Mortgage and Housing Corporation, Absorptions and Unabsorbed Inventory, Newly Completed Dwellings dataset from Statistics Canada contains information of the number of absorbed complete dwelling units (newly completed units) and the number of unabsorbed inventory (second-hand housing) by different geographical regions such as Toronto, Ottawa, and Census metropolitan areas.

### 3. [Mortgages in Arrears](https://www.cmhc-schl.gc.ca/en/blog/2021/new-report-sresidential-mortgages-shows-30-year-low-arrears)

Follow the link to the website, we wanted to scrape the table "Mortgages in arrears (delinquent for 90 or more days) continued downward trend across all lender types". The table contains information about mortgage in arrears across different lender types from 2020 Q1 to 2021 Q1.

The following code were used to scrape the table:

```{r}
url <- "https://www.cmhc-schl.gc.ca/en/blog/2021/new-report-residential-mortgages-shows-30-year-low-arrears"

mortgage_arrears <- read_html(url)
table <- xml_find_all(mortgage_arrears, xpath='/html/body/div[3]/main/section/div[9]/div/figure/div/div[2]/div/table')
table <- html_table(table)

tibble <- table[[1]]
tibble %>% kable()
```

### 4. [Financial Market Statistics](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1010014501)

The Financial Market Statistics dataset from Statistics Canada provides information about various financial market rates such as bank rate, interest rates, government bond yields, treasury bills, etc, on a weekly basis.

### 5. [Chartered Bank Assets and Liabilities and Monetary Aggregates](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1010011601)

The Chartered Bank Assets and Liabilities and Monetary Aggregates dataset from Statistics Canada provides information of the assets, liabilities and the money circulating in the Canadian economy (monetary aggregates).

### 6. [Consumer Price Index](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1810000401)

The Consumer Price Index (CPI)  reflects the consumer prices that the Canadian is experiencing. The dataset from Statistics Canada provides the value of CPI of each time points for different product groups, recorded on a monthly basis.