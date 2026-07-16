# Product-Analysis
A Power BI dashboard built to analyze product-level supply, demand, and profitability data — helping identify shortages, losses, and profit trends across products.

## Problem Statement

Businesses dealing with multiple products often struggle to track whether they are meeting customer demand efficiently, or whether gaps between supply and demand are leading to revenue loss. Without a consolidated view, it becomes difficult to answer key questions such as:

- Which products are facing frequent shortages (demand > availability)?
- How much loss is being incurred due to unmet demand?
- Which products are the most profitable, and which are dragging down performance?
- What are the average daily trends in availability, demand, and loss?

This dashboard consolidates raw transactional data into a single interactive view, enabling quick, data-driven decisions on inventory planning, pricing, and product prioritization.

## Dataset

| Column | Description |
|---|---|
| Order Date | Date on which the order was placed |
| Product ID | Unique identifier for each product |
| Product Name | Name of the product |
| Unit Price | Price per unit of the product |
| Availability | Quantity of the product available (supply) |
| Demand | Quantity of the product demanded |
| Loss/Profit | Signed value — positive indicates profit, negative indicates loss |

## Steps Followed

- Step 1: Loaded data into Power BI Desktop,dataset in a csv file.

- Step 2: Opened Power Query Editor and, under the View tab's Data Preview section, checked "Column distribution", "Column quality", and "Column profile" for all columns
.
- Step 3: Set column profiling to be based on the entire dataset (not just the by default 1000-row sample), to get an accurate read on nulls/errors across all rows.

- Step 4: Verified data types — Order Date set to Date, Availability/Demand/Unit Price/Loss-Profit set to Numeric.

- Step 5: Checked all columns for errors and empty values; corrected/removed inconsistent rows where found.

- Step 6: In the report view, under the view tab, theme was selected and logo image.

- step 7 : New measure was created to find Total loss by each product.

  Following DAX expression was written to find Total loss 
         Total Loss = SUMX(FILTER('Demand/availability data','Demand/availability data'[LOSS/PROFIT]<0),'Demand/availability data'[LOSS/PROFIT]*'Demand/availability data'[Unit_price])* -1

A card visual was used to represent total loss
[Snap Totalloss] <img width="288" height="413" alt="Image" src="https://github.com/user-attachments/assets/a740a7d9-a1b0-49b1-a500-ffec46ec0169" /> 

- step 8 :New measure was created to find Total profit by each product.
  Following DAX expression was written to find Total profit 
          Total Profit = SUMX(FILTER('Demand/availability data','Demand/availability data'[LOSS/PROFIT]>0),'Demand/availability data'[LOSS/PROFIT]*'Demand/availability data'[Unit_price])
A card visual was used to represent total profit
[Snap Totalprofit]<img width="278" height="398" alt="Image" src="https://github.com/user-attachments/assets/b7edaf17-3d71-410b-b675-4e178838c6f4" />
 

- step 9: New measure was created to find Average daily loss by each product.
  Following DAX expression was written to find Average daily loss 
         
   Total Profit = SUMX(FILTER('Demand/availability data','Demand/availability data'[LOSS/PROFIT]>0),'Demand/availability data'[LOSS/PROFIT]*'Demand/availability data'[Unit_price])

A card visual was used to represent Average daily loss
[Snap_Averagedaily loss]  <img width="300" height="394" alt="Image" src="https://github.com/user-attachments/assets/5f726f61-eac3-4d1a-988c-d921c3beed52" />
   

- step 10 : New measure was created to find by Average availability each product.
    Following DAX expression was written to find Average availability 

    Average Availability Per Day = DIVIDE([Total Availability],[Total Numbers of Days])

A card visual was used to represent Average availibility
[Snap_Average availability]<img width="316" height="434" alt="Image" src="https://github.com/user-attachments/assets/3936ff51-d34c-4eec-8f22-4fad5c24ff98" />


 - step 11: measure was created to find Average Demand by each product.
      Following DAX expression was written to find Average Demand

      Average Demand per Day = DIVIDE([Total Demand],[Total Numbers of Days])

A card visual was used to represent Average demand 
[Snap_Averagedemand]<img width="294" height="451" alt="Image" src="https://github.com/user-attachments/assets/7607f554-946e-4bfa-ba34-b9fc3b3dec38" />


  - step 12: New measure was created to find day Total supply shortage each product.
     Following DAX expression was written to find Total supply shortage 

      Total Supply Shortage = [Total Demand]-[Total Availability]

A card visual was used to represent total supply shortage 
[Snap_Total_supplyshortage]<img width="282" height="409" alt="Image" src="https://github.com/user-attachments/assets/7dd860c8-255e-43da-bdc4-8bbc0b27fa30" />


- Step 13: Visualization Design – Built cards for KPIs (Total Loss, Total Profit, Total Supply Shortage,average demand per day ,average availibilty per day ,average daily loss).

- step 14 - Added Card visuals for each KPI measure on the canvas — one card each for 
Total Profit
Total Loss
Total Supply Shortage 
Average Availability per Day 
Average Demand per Day 
Average Daily Loss.

- Step 15 : Added slicers/filters (Product Name, Order Date range) to allow drill-down analysis.

- Step 16: Analyzed the report view to identify patterns in shortages, loss-making products, and top profit contributors.


## Insights

A single-page report was created in Power BI Desktop. Following inferences can be drawn from the dashboard:

Report snapshort [Dashboard]<img width="1386" height="741" alt="Image" src="https://github.com/user-attachments/assets/ba30eb18-02c9-429f-a3e5-5d7dae95fff9" />
<img width="1353" height="741" alt="Image" src="https://github.com/user-attachments/assets/512e3bbe-2c06-490c-bc9c-224bcfe7daea" />

[1] Overall Business Health

- Total Profit = ₹289.75K
- Total Loss = ₹7M
- Total Supply Shortage = 61K units

  Loss is over **25x** the profit — the business is losing far more to unmet demand/shortages than it is earning, making supply-demand alignment the top priority.

 [2] Daily Averages

- Average Demand per Day = 48.65 units
- Average Availability per Day = 24.70 units
- Average Daily Loss = ₹2.87K

  On average, demand is nearly *double* the availability every day — this is a systemic, recurring gap rather than an occasional dip, and it directly explains the scale of the total loss above.

# Product-Wise Breakdown

 [1] Product-Wise Contribution to Loss (Top 5)
| Product | % of Total Loss |

| 4K Smart TV | 19.70% |
| VR Headset | 14.71% |
| Digital Camera | 12.46% |
| Tablet | 11.55% |
| Smartwatch | 7.77% |

  These 5 products alone account for ~66% of total loss.

[2] Product-Wise Contribution to Profit (Top 5)
| Product | % of Total Profit |
| 4K Smart TV | 29.16% |
| VR Headset | 20.98% |
| Digital Camera | 13.87% |
| Action Camera | 4.28% |
| Gaming Keyboard | 3.89% |

  The same three products (4K Smart TV, VR Headset, Digital Camera) drive both the highest profit *and* the highest loss — since they're high unit-price items, even small shortages swing their ₹ impact heavily in either direction.

 [3] Product-Wise Contribution to Supply Shortage (Top 5)
| Product | % of Total Shortage |
| Phone Case | 10.36% |
| Wireless Mouse | 5.81% |
| Tablet | 5.76% |
| Coffee Maker | 5.64% |
| Laptop Stand | 5.61% |

  Unlike the profit/loss leaders, **Phone Case** — a low unit-price item — has the single highest unit shortage, but a comparatively small ₹ loss footprint. This points to two distinct problems: high-value products need tighter supply planning to protect margins, while high-volume low-value products like Phone Case need shortage resolution to protect sales volume.

## Tools Used

- Power BI Desktop – Data modeling, DAX measures, dashboard design

- SQL Server (SSMS)  – source system and clean the data

## How to Use

1. Open the `.pbix` file in Power BI Desktop.
2. Use the slicers to filter by Product Name or Order Date.
3. Refer to the KPI cards for a quick summary and the trend charts / product table for deeper analysis.
4. Use the Matrix table alongside the Cards for data validation — cross-check that the sum of product-wise values in the Matrix matches the overall totals shown on the Cards.
