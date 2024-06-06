
# Customer Cohort Analysis Using Excel - Step-by-Step Guide
## Introduction
In this guide, I'll walk you through the process of creating a customer cohort chart using an Excel sheet downloaded from KPMG. We'll clean up the data, generate the necessary columns, and create a pivot table to visualize the cohorts. Additionally, we'll calculate the retention ratio for each cohort over different months.

The Client Cohort Chart is a powerful tool for business that work on suscriptions but business who work on punctual transactions.


### Step 1: Data Cleanup
First, I eliminated the columns that don't play a role in the client cohort chart. The columns removed are:

- online_order
- order_status
- brand
- product_line
- product_class
- product_size
- list_price
- standard_cost
- product_first_sold_date

I preserved the following 4 columns:

- transaction_id
- product_id
- customer_id
- transaction_date

**Please check that in your business, there are clients who convey more than one transaction. If not, the analysis is not going to work. In the column customer_id there should be repeated values 
** transaction_id and product_id are not really necessary as well for this purpose 

### Step 2: Generate Acquisition Date
With the transaction_date and customer_id, I generated another column called acquisition_date. The formula used is:

The formula that I used in EXCEL is: 
```excel
=MINIFS($D$2:$D$20001, $C$2:$C$20001, C2)
```
Where: 
- Column C is customer_id
- Column D is transaction_date
- Row 1 is the header
- Row 2 is the first value 
- Record 20001 is the last transaction recorded 
This formula finds the earliest transaction date for each customer, marking their acquisition date.

### Step 3: Create a Pivot Table
Select the entire table:
Click and drag to select the range of data including the new acquisition_date column.
Insert a Pivot Table:
Go to the Insert tab and click on Pivot Table.
#### Choose to insert the pivot table in a new worksheet.
Configure the Pivot Table
Rows: Drag the acquisition_date field to the Rows area.
Columns: Drag the transaction_date field to the Columns area.
Values: Drag the customer_id field to the Values area and set it to count (Count of customer_id).

| <01.01.2017 | Jan | Feb | Mrz | Apr | Mai | Jun | Jul | Aug | Sep | Okt | Nov | Dez | Grand Total |
|-------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-------------|
| Jan         | 1682| 613 | 633 | 632 | 649 | 602 | 662 | 670 | 620 | 668 | 617 | 626 | 8674        |
| Feb         |     | 1010| 406 | 384 | 399 | 350 | 372 | 403 | 350 | 410 | 386 | 373 | 4843        |
| Mrz         |     |     | 617 | 215 | 222 | 217 | 228 | 221 | 223 | 268 | 237 | 235 | 2683        |
| Apr         |     |     |     | 424 | 139 | 151 | 199 | 192 | 148 | 174 | 167 | 163 | 1757        |
| Mai         |     |     |     |     | 276 | 109 | 103 | 106 | 82  | 92  | 92  | 103 | 963         |
| Jun         |     |     |     |     |     | 152 | 58  | 59  | 60  | 61  | 60  | 67  | 517         |
| Jul         |     |     |     |     |     |     | 95  | 32  | 35  | 41  | 43  | 33  | 279         |
| Aug         |     |     |     |     |     |     |     | 66  | 24  | 24  | 29  | 13  | 156         |
| Sep         |     |     |     |     |     |     |     |     | 30  | 9   | 9   | 10  | 58          |
| Okt         |     |     |     |     |     |     |     |     |     | 24  | 9   | 9   | 42          |
| Nov         |     |     |     |     |     |     |     |     |     |     | 16  | 6   | 22          |
| Dez         |     |     |     |     |     |     |     |     |     |     |     | 6   | 6           |
| Grand Total | 1682| 1623| 1656| 1655| 1685| 1581| 1717| 1749| 1572| 1771| 1665| 1644| 20000       |


### Step 5: Calculate Customer Retention Ratio
To calculate the retention ratio for each cohort and each month, follow these steps:

Add a new column next to your pivot table for retention ratios.
Divide the number of customers that made transactions in a given month (column) by the number of customers acquired in that month (row).
Multiply by 100 to get the retention ratio percentage.

| <01.01.2017 | Jan  | Feb  | Mrz  | Apr  | Mai  | Jun  | Jul  | Aug  | Sep  | Okt  | Nov  | Dez  |
|-------------|------|------|------|------|------|------|------|------|------|------|------|------|
| Jan         | #REF!| 36   | 38   | 38   | 39   | 36   | 39   | 40   | 37   | 40   | 37   | 37   |
| Feb         |      | 100  | 40   | 38   | 40   | 35   | 37   | 40   | 35   | 41   | 38   | 37   |
| Mrz         |      |      | 100  | 35   | 36   | 35   | 37   | 36   | 36   | 43   | 38   | 38   |
| Apr         |      |      |      | 100  | 33   | 36   | 47   | 45   | 35   | 41   | 39   | 38   |
| Mai         |      |      |      |      | 100  | 39   | 37   | 38   | 30   | 33   | 33   | 37   |
| Jun         |      |      |      |      |      | 100  | 38   | 39   | 39   | 40   | 39   | 44   |
| Jul         |      |      |      |      |      |      | 100  | 34   | 37   | 43   | 45   | 35   |
| Aug         |      |      |      |      |      |      |      | 100  | 36   | 36   | 44   | 20   |
| Sep         |      |      |      |      |      |      |      |      | 100  | 30   | 30   | 33   |
| Okt         |      |      |      |      |      |      |      |      |      | 100  | 38   | 38   |
| Nov         |      |      |      |      |      |      |      |      |      |      | 100  | 38   |
| Dez         |      |      |      |      |      |      |      |      |      |      |      | 100  |
