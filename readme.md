# Real Estate Market Trends Analysis \| Power BI

![Power
BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/Analytics-DAX-blue)
![Project](https://img.shields.io/badge/Project-Real%20Estate%20Market%20Trends-success)

## 1. Project Overview

A four-page interactive Power BI report developed for the CodeAlpha
Power BI virtual internship task. It analyses a **synthetic**
real-estate dataset to explore property inventory, listed prices, price
per square foot, rental yields, estimated market values, demand and
supply indices, new listings, reported transaction counts, geographic
differences, and selected economic indicators.

The report is designed to answer questions such as: - How do listed
prices and rental yields differ across cities? - Which property types
have higher average prices per square foot? - How have market values,
demand, supply, rents, new listings, and reported transactions changed
over time? - How do market tiers compare on listed price and rental
yield? - Which cities are above or below the market-average listed-price
benchmark? - What geographic and economic context accompanies the
observed patterns?

**Data disclaimer:** The datasets are synthetic and intended for
educational and analytical demonstration. Results do not represent
verified real-world market conditions.

## 2. Report Pages and Actual Contents

### Page 1 --- Real Estate Market Overview

**KPI cards** - Property Count - Average Listed Price - Average Price
per Sq Ft - Average Rental Yield

**Visuals** 1. **Average Listed Price by City** --- horizontal bar chart
comparing average listed prices across cities. 2. **Average Price per Sq
Ft by Property Type** --- column chart comparing price intensity by
property type. 3. **Average Rental Yield by City** --- horizontal bar
chart comparing average gross rental yield by city. 4. **Listing Status
Mix** --- donut chart showing Available, Rented, Under Construction, and
Sold property records.

**Slicers:** City, PropertyType, ListingStatus, Date range.

### Page 2 --- Trends, Demand & Rental Yield

**KPI cards** - Average Market Value - Latest Month MoM Change % -
Rental Record Occupancy Rate - Annualized Rental Income - Demand-Supply
Gap - Transactions-to-Listings Ratio

**Visuals** 1. **Demand and Supply Index Trends** --- line chart with
Average Demand Index and Average Supply Index by Year-Month. 2.
**Estimated Market Value Trend** --- line chart showing Average Market
Value over time. 3. **Listed Price vs Gross Rental Yield** --- scatter
chart comparing Average Listed Price and Average Rental Yield by City,
with MarketTier as the legend. 4. **Average Monthly Rent Trend** ---
line chart showing Average Monthly Rent over time. 5. **Monthly New
Listings vs Transactions** --- clustered column chart comparing New
Listings and reported Transactions by month.

**Slicers:** Year-Month, MarketTier, PropertyType, City.

**Transactions interpretation:** `Transactions` is the sum of
`realestate_market_snapshots[TransactionsCount]`. It is a count, not
currency. The dataset does not identify individual completed sales, so
describe it as a reported market transaction count, not verified
property sales.

### Page 3 --- Geographic Hotspots & Economic Context

**Visuals** 1. **Average Home Loan Rate Trend Over Time** --- line chart
using average HomeLoanRatePct by Year-Month. 2. **Average Market Value
Trend Over Time** --- line chart showing Average Market Value by
Year-Month. 3. **Average Listed Price by MarketTier** --- horizontal bar
chart comparing Low, Medium, and High tiers. 4. **Average Rental Yield
by MarketTier** --- separate horizontal bar chart comparing average
rental yield by tier. 5. **City-level Market Hotspots** --- bubble map
using city-centre coordinates; Property Count is used for bubble size
and city-level market measures appear in the tooltip. 6. **GDP Growth
Trend Over Time** --- line chart showing GDPGrowthPct by Year-Month,
with InflationPct in the tooltip.

**KPI cards** - Average Home Loan Rate - Average GDP Growth

**Slicers:** City, PropertyType, MarketTier, Year-Month.

**Geographic limitation:** Latitude and longitude are city-centre
coordinates, not property-level coordinates. The map is a city-level
visualization.

**Economic interpretation:** Comparing home-loan rates and market values
over time does not establish that one caused changes in the other.

**Explicit exclusion:** `Price Premium vs Market Average %` and
`Average City Price Premium %` were not used on Page 3. They were added
to Page 4.

### Page 4 --- Investment Signals & Performance Analysis

**KPI card** - **Cities Above Market Average** --- counts cities with a
positive price premium in the current filter context.

**Visuals** 1. **City Investment Signal Classification** --- table with
City, Average Listed Price, Price Premium vs Market Average %, Average
Rental Yield, and City Investment Signal. 2. **Monthly Market Value
Growth (%)** --- line chart using Market Value MoM Change % by
Year-Month. Tooltips: Average Market Value and Previous Month Market
Value. 3. **Annualized Rental Income Represented by Occupied Records in
Each City** --- horizontal bar chart using the occupied-rental-record
annualization measure. 4. **City Price Premium vs Market Average** ---
horizontal bar chart showing each city's percentage difference from the
market benchmark. 5. **Cumulative Transactions Over Time** --- line
chart showing the running total of reported transaction counts.

**Slicers:** OwnershipType, PropertyType, MarketTier, Year-Month.

**Interpretation notes** - The market-value growth visual is
**month-over-month (MoM)**, not year-over-year (YoY). - Annualized
occupied rental income multiplies each occupied rental record's monthly
rent by 12 and sums the results. Since multiple monthly records may
exist for one property, the same property's rent may be counted
repeatedly. It is not verified annual rental revenue. - Cumulative
Transactions is a running total of the reported `TransactionsCount`
values, not a count of individually identified property sales. -
Investment signals are descriptive screening categories, not investment
advice.

## 3. Data Sources

Five CSV datasets were used. Record counts below are the counts
documented during project setup.

  --------------------------------------------------------------------------------------------------
  CSV / Power BI table                                           Rows Main fields
  -------------------------------------- ---------------------------- ------------------------------
  `realestate_locations.csv` /                                     12 LocationID, City, State,
  `realestate_locations`                                              Latitude, Longitude,
                                                                      MarketTier

  `realestate_properties.csv` /                                   850 PropertyID, PropertyType,
  `realestate_properties`                                             AreaSqFt, ListedPriceINR,
                                                                      PricePerSqFtINR,
                                                                      ListingStatus,
                                                                      ConstructionStatus, LocationID

  `realestate_market_snapshots.csv` /                          28,900 EstimatedMarketValueINR,
  `realestate_market_snapshots`                                       DemandIndex, SupplyIndex,
                                                                      NewListingsCount,
                                                                      TransactionsCount,
                                                                      SnapshotDate, PropertyID

  `realestate_rental_records.csv` /                             6,000 MonthlyRentINR,
  `realestate_rental_records`                                         OccupancyStatus, PeriodDate,
                                                                      GrossRentalYieldPct,
                                                                      PropertyID

  `realestate_economic_indicators.csv` /                          408 GDPGrowthPct, InflationPct,
  `realestate_economic_indicators`                                    UnemploymentPct,
                                                                      InfrastructureSpendINRCrore,
                                                                      HomeLoanRatePct, PeriodDate,
                                                                      LocationID
  --------------------------------------------------------------------------------------------------

The synthetic monthly data spans January 2024 through October 2026 (34
months).

## 4. Data Model and Relationships

The model uses locations and properties as dimensions/parent tables,
related market snapshots, rental records and economic indicators, plus a
shared Date table.

  ------------------------------------------------------------------------------------
  One side                  Many side                          Relationship
  ------------------------- ---------------------------------- -----------------------
  `realestate_locations`    `realestate_properties`            LocationID → LocationID

  `realestate_locations`    `realestate_economic_indicators`   LocationID → LocationID

  `realestate_properties`   `realestate_market_snapshots`      PropertyID → PropertyID

  `realestate_properties`   `realestate_rental_records`        PropertyID → PropertyID

  `Date`                    `realestate_market_snapshots`      Date\[Date\] →
                                                               SnapshotDate

  `Date`                    `realestate_rental_records`        Date\[Date\] →
                                                               PeriodDate

  `Date`                    `realestate_economic_indicators`   Date\[Date\] →
                                                               PeriodDate
  ------------------------------------------------------------------------------------

These are one-to-many relationships from the first table to the second.
The rental-record and market-snapshot fact tables are **not** directly
joined. Slicer propagation depends on active relationships and the
visual interactions configured in the PBIX.

### Date table

``` dax
Date =
CALENDAR(
    DATE(2023, 1, 1),
    DATE(2027, 12, 31)
)
```

Calculated columns:

``` dax
Year = YEAR('Date'[Date])

Month Number = MONTH('Date'[Date])

Month = FORMAT('Date'[Date], "MMM")

Year-Month = FORMAT('Date'[Date], "YYYY-MM")

YearMonthSort = YEAR('Date'[Date]) * 100 + MONTH('Date'[Date])
```

`Month` is sorted by `Month Number`; `Year-Month` is sorted by
`YearMonthSort`; the table is marked as the Date table using
`Date[Date]`.

## 5. DAX Measures

The following are the named measures used or confirmed during the
project. Economic fields such as GDPGrowthPct, InflationPct, and
HomeLoanRatePct were also used directly in visuals with the Average
aggregation; they are not represented here as separately authored
measures.

### Core measures

``` dax
Property Count =
DISTINCTCOUNT(realestate_properties[PropertyID])

Average Listed Price =
AVERAGE(realestate_properties[ListedPriceINR])

Average Price per Sq Ft =
AVERAGE(realestate_properties[PricePerSqFtINR])

Average Market Value =
AVERAGE(realestate_market_snapshots[EstimatedMarketValueINR])

Average Rental Yield =
AVERAGE(realestate_rental_records[GrossRentalYieldPct]) / 100

Average Monthly Rent =
AVERAGE(realestate_rental_records[MonthlyRentINR])

Average Demand Index =
AVERAGE(realestate_market_snapshots[DemandIndex])

Average Supply Index =
AVERAGE(realestate_market_snapshots[SupplyIndex])

New Listings =
SUM(realestate_market_snapshots[NewListingsCount])

Transactions =
SUM(realestate_market_snapshots[TransactionsCount])
```

`Average Rental Yield` divides the stored percentage-point value by 100
so it can be formatted using Power BI Percentage formatting.

### Page 2 supporting measures

``` dax
Previous Month Market Value =
CALCULATE(
    [Average Market Value],
    DATEADD('Date'[Date], -1, MONTH)
)

Demand-Supply Gap =
[Average Demand Index] - [Average Supply Index]

Transactions-to-Listings Ratio =
DIVIDE([Transactions], [New Listings], 0)

Annualized Rental Income =
SUMX(
    realestate_rental_records,
    realestate_rental_records[MonthlyRentINR] * 12
)

Occupied Rental Records =
CALCULATE(
    COUNTROWS(realestate_rental_records),
    realestate_rental_records[OccupancyStatus] = "Occupied"
)

Occupancy Rate =
DIVIDE(
    [Occupied Rental Records],
    COUNTROWS(realestate_rental_records),
    0
)
```

The Page 2 `Latest Month MoM Change %` card uses the latest available
snapshot month when no Year-Month selection is made, and the selected
month when the Year-Month slicer is filtered:

``` dax
Latest Month MoM Change % =
VAR HasMonthSelection =
    ISFILTERED('Date'[Year-Month])
VAR SelectedDate =
    MAX('Date'[Date])
VAR LatestSnapshotDate =
    CALCULATE(
        MAX(realestate_market_snapshots[SnapshotDate]),
        REMOVEFILTERS('Date')
    )
VAR TargetDate =
    IF(HasMonthSelection, SelectedDate, LatestSnapshotDate)
VAR CurrentMonthStart =
    DATE(YEAR(TargetDate), MONTH(TargetDate), 1)
VAR PreviousMonthStart =
    EDATE(CurrentMonthStart, -1)
VAR CurrentValue =
    CALCULATE(
        [Average Market Value],
        REMOVEFILTERS('Date'),
        DATESBETWEEN(
            'Date'[Date],
            CurrentMonthStart,
            EOMONTH(CurrentMonthStart, 0)
        )
    )
VAR PreviousValue =
    CALCULATE(
        [Average Market Value],
        REMOVEFILTERS('Date'),
        DATESBETWEEN(
            'Date'[Date],
            PreviousMonthStart,
            EOMONTH(PreviousMonthStart, 0)
        )
    )
RETURN
    IF(
        ISBLANK(TargetDate),
        BLANK(),
        DIVIDE(CurrentValue - PreviousValue, PreviousValue)
    )
```

### Page 4 measures

``` dax
Price Premium vs Market Average % =
VAR MarketAverage =
    CALCULATE(
        [Average Listed Price],
        REMOVEFILTERS(realestate_locations[City])
    )
RETURN
    DIVIDE(
        [Average Listed Price] - MarketAverage,
        MarketAverage
    )
```

``` dax
Average City Price Premium % =
AVERAGEX(
    VALUES(realestate_locations[City]),
    [Price Premium vs Market Average %]
)
```

``` dax
City Price Rank =
RANKX(
    ALL(realestate_locations[City]),
    CALCULATE([Average Listed Price]),
    ,
    DESC,
    DENSE
)
```

``` dax
Market Value MoM Change % =
VAR CurrentValue = [Average Market Value]
VAR PreviousValue = [Previous Month Market Value]
RETURN
    IF(
        ISBLANK(CurrentValue) || ISBLANK(PreviousValue),
        BLANK(),
        DIVIDE(CurrentValue - PreviousValue, PreviousValue)
    )
```

``` dax
Cumulative Transactions =
VAR CurrentDate = MAX('Date'[Date])
VAR LatestTransactionDate =
    CALCULATE(
        MAX(realestate_market_snapshots[SnapshotDate]),
        REMOVEFILTERS('Date')
    )
RETURN
    IF(
        CurrentDate > LatestTransactionDate,
        BLANK(),
        CALCULATE(
            [Transactions],
            FILTER(
                ALLSELECTED('Date'[Date]),
                'Date'[Date] <= CurrentDate
            )
        )
    )
```

``` dax
Annualized Occupied Rental Income =
SUMX(
    FILTER(
        realestate_rental_records,
        realestate_rental_records[OccupancyStatus] = "Occupied"
    ),
    realestate_rental_records[MonthlyRentINR] * 12
)
```

``` dax
Market Average Rental Yield =
CALCULATE(
    [Average Rental Yield],
    REMOVEFILTERS(realestate_locations[City])
)
```

``` dax
City Investment Signal =
VAR Premium = [Price Premium vs Market Average %]
VAR Yield = [Average Rental Yield]
VAR MarketYield = [Market Average Rental Yield]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(Premium) || ISBLANK(Yield), "Insufficient Data",
        Premium <= 0 && Yield > MarketYield, "Value + Higher Yield",
        Premium > 0 && Yield > MarketYield, "Premium + Higher Yield",
        Premium <= 0 && Yield <= MarketYield, "Value + Lower Yield",
        "Premium + Lower Yield"
    )
```

``` dax
Cities Above Market Average =
COUNTROWS(
    FILTER(
        ALLSELECTED(realestate_locations[City]),
        [Price Premium vs Market Average %] > 0
    )
)
```

## 6. Data Preparation and Visualization Notes

-   IDs were treated as text identifiers, date fields as Date, and
    coordinates/prices/rents/indexes as numeric.
-   Latitude and Longitude were set to Decimal Number and used as
    coordinates. In the map visual, both coordinate fields were set to
    **Don't summarize**.
-   The map uses city-centre coordinates, not property-level
    coordinates.
-   Rental-yield values are stored as percentage points (for example,
    5.42 means 5.42%). Formatting was handled to avoid displaying 542%.
-   The Date table was marked as a date table and the month fields were
    sorted chronologically.
-   The MoM measure returns blank when current or previous month market
    value is blank, preventing a missing month from appearing as a false
    -100% change.
-   The cumulative transaction measure returns blank after the latest
    available snapshot date rather than carrying the last cumulative
    value into future periods.

## 7. Key Interpretations and Limitations

1.  **Synthetic data:** Findings are demonstrations, not verified market
    conditions.
2.  **Map:** Coordinates represent city centres only.
3.  **Transactions:** Counts from `TransactionsCount`; not currency and
    not individually identified property sales.
4.  **Annualized occupied rental income:** Repeated monthly records for
    a property may be annualized and summed repeatedly. Do not describe
    this as verified annual revenue.
5.  **Price premium:** Positive means a city average is above the market
    benchmark; negative means below. The measure removes the City filter
    while retaining other applicable filters.
6.  **Investment signal:** A rule-based comparison of price premium and
    rental yield, not investment advice or a return guarantee.
7.  **Economic context:** Co-movement between indicators does not
    establish causation.
8.  **Date coverage:** The Date table spans 2023--2027; the synthetic
    monthly fact data discussed in the project spans January
    2024--October 2026.

## 8. Tools and Technologies

-   Microsoft Power BI Desktop
-   Power Query
-   DAX
-   CSV datasets
-   Microsoft Bing map visual

## 9. Suggested Repository Structure

``` text
Real-Estate-Market-Trends-PowerBI/
├── data/
│   ├── realestate_locations.csv
│   ├── realestate_properties.csv
│   ├── realestate_market_snapshots.csv
│   ├── realestate_rental_records.csv
│   └── realestate_economic_indicators.csv
├── screenshots/
│   ├── page-1-market-overview.png
│   ├── page-2-trends-demand-rental-yield.png
│   ├── page-3-geographic-hotspots-economic-context.png
│   └── page-4-investment-signals-performance-analysis.png
├── Real_Estate_Market_Trends.pbix
└── README.md
```

Only include datasets and screenshots that you actually publish. If CSV
files are not included, document how the report's source data is made
available.

## 10. How to Use

1.  Clone or download the repository.
2.  Open `Real_Estate_Market_Trends.pbix` in Power BI Desktop.
3.  If the CSVs are included, update source paths in Power Query if
    necessary.
4.  Refresh the data.
5.  Explore the four report pages and use their slicers.

## 11. Project Outcome

The completed report demonstrates a multi-table Power BI workflow: data
import, relationship modeling, a shared Date dimension, DAX measures,
interactive slicers, geographic visualization, time-based analysis, and
intermediate iterator/filter/logical calculations. It provides
descriptive market, rental, geographic, economic, and city-screening
views while clearly documenting the limitations of the synthetic
dataset.
