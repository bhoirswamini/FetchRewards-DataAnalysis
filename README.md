# FetchRewards-DataAnalysis
ER - diagram, Data Analysis and SQL script has been uploaded on Github repository 
Raw data files can be found here

# Part 1: Relational Data Modelling:
Used draw.io to design the ER diagram.

# Data Files:
## File 1: users.json
    _id: user Id
    state: state abbreviation
    createdDate: when the user created their account
    lastLogin: last time the user was recorded logging in to the app
    role: constant value set to 'CONSUMER'
    active: indicates if the user is active; only Fetch will de-activate an account with this flag

## File 2: brands.json
    _id: brand uuid
    barcode: the barcode on the item
    brandCode: String that corresponds with the brand column in a partner product file
    category: The category name for which the brand sells products in
    categoryCode: The category code that references a BrandCategory
    cpg: reference to CPG collection
    topBrand: Boolean indicator for whether the brand should be featured as a 'top brand'
    name: Brand name

## File 3: receipts.json
    _id: uuid for this receipt
    bonusPointsEarned: Number of bonus points that were awarded upon receipt completion
    bonusPointsEarnedReason: event that triggered bonus points
    createDate: The date that the event was created
    dateScanned: Date that the user scanned their receipt
    finishedDate: Date that the receipt finished processing
    modifyDate: The date the event was modified
    pointsAwardedDate: The date we awarded points for the transaction
    pointsEarned: The number of points earned for the receipt
    purchaseDate: the date of the purchase
    purchasedItemCount: Count of number of items on the receipt
    rewardsReceiptItemList: The items that were purchased on the receipt
    rewardsReceiptStatus: status of the receipt through receipt validation and processing
    totalSpent: The total amount on the receipt
    userId: string id back to the User collection for the user who scanned the receipt

rewardsReceiptItemList contains list of items i.e. receipts has nested json so I flatten it into receipts and orders/reciptItem data and connected them with receipt_id

# Part 2: Queries to answer business questions

1. What are the top 5 brands by receipts scanned for most recent month?

2. How does the ranking of the top 5 brands by receipts scanned for the recent month compare to the ranking for the previous month?

3. When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

4. When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?

5. Which brand has the most spend among users who were created within the past 6 months?

6. Which brand has the most transactions among users who were created within the past 6 months?

Used Pandas sql - Read [SQL script]((https://github.com/bhoirswamini/FetchRewards-DataAnalysis/blob/f6d02da71551019c2e1b4742290986e1e1329a2b/Part%202%20-%20SQL%20Script.ipynb)https://github.com/bhoirswamini/FetchRewards-DataAnalysis/blob/f6d02da71551019c2e1b4742290986e1e1329a2b/Part%202%20-%20SQL%20Script.ipynb)

# Part 3: Addressed Data Quality issues 
The python script for the data quality issue is [here] 


