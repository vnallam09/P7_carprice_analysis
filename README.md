# Custom Business Intelligence Project: Car Price Analysis (Power BI)

## Section 1: The Business Goal

**Business Question:**  
Which car brands and fuel types offer the best value proposition across different market segments, and what are the pricing trends over the years?

**Objectives:**
1. Identify premium vs. value brands in the automotive market
2. Analyze pricing trends by fuel type
3. Determine value propositions based on price-to-performance ratios
4. Understand transmission and ownership impact on pricing
5. Provide actionable insights for dealerships and consumers

---

## Section 2: Data Source

**Dataset:** `car_price_dataset_medium.csv`

**Records:** 1,000 cars

**Columns:**
- Car_ID, Brand, Model_Year, Kilometers_Driven
- Fuel_Type, Transmission, Owner_Type
- Engine_CC, Max_Power_bhp, Mileage_kmpl, Seats
- Price_USD

**Brands Included:** Audi, BMW, Mercedes, Toyota, Honda, Kia, Hyundai, Nissan, Ford, Volkswagen

**Time Period:** 2005-2024

---

## Section 3: Tools Used

**Primary Tool:**
- **Power BI Desktop** - Data visualization and dashboard creation
- **Power Query** - Data transformation and cleaning
- **DAX (Data Analysis Expressions)** - Calculated measures

**Data Source:**
- CSV file import

**Features Utilized:**
- Interactive slicers and filters
- Cross-filtering between visuals
- Custom DAX measures
- Conditional formatting
- Multiple dashboard pages

---

## Section 4: Workflow & Logic

### Data Import Process
1. Imported CSV file using "Get Data" → Text/CSV
2. Loaded 1,000 records with 12 columns

### Data Transformation (Power Query)
1. Validated and corrected data types
2. Created calculated columns:
   - `Price_Category` (Budget/Mid-Range/Premium/Luxury)
   - `Car_Age` (2024 - Model_Year)
   - `Price_per_Power` (Price/Power ratio)

### DAX Measures Created
```dax
Avg Price = AVERAGE('car_price_dataset_medium'[Price_USD])
Total Cars = COUNTROWS('car_price_dataset_medium')
Value Score = DIVIDE(AVERAGE([Max_Power_bhp]), AVERAGE([Price_USD])) * 1000
```

### Dashboard Structure
- **Page 1:** Overview with KPIs and trends
- **Page 2:** Brand analysis and comparison
- **Page 3:** Fuel type and transmission analysis
- **Page 4:** Value proposition and segmentation

### Analytical Techniques
- **Slicing:** Filter by year, brand, fuel type
- **Dicing:** Multi-dimensional views (brand × fuel type)
- **Drill-down:** From category to detailed metrics
- **Aggregation:** AVG, SUM, COUNT, MIN, MAX
- **Trend Analysis:** Time-series visualization

---

## Section 5: Results

### Key Findings

#### **Finding 1: Premium Brand Hierarchy**
![Overview Dashboard](screenshots/power_bi_overview.png)

**Top 3 Most Expensive Brands:**
1. Mercedes - $68,450 average
2. Audi - $66,230 average
3. BMW - $64,890 average

**Value Brands:**
- Kia - $48,120 average
- Hyundai - $47,680 average

---

#### **Finding 2: Fuel Type Premium**
![Fuel Analysis](screenshots/power_bi_fuel_analysis.png)

**Price by Fuel Type:**
- Hybrid: $62,340 (highest)
- Electric: $59,780
- Petrol: $58,450
- Diesel: $56,120

**Insight:** Hybrid technology commands 11% premium over diesel

---

#### **Finding 3: Transmission Value**
**Automatic Transmission Premium:** $8,240 (14% higher than manual)

**Owner Type Depreciation:**
- First Owner: $64,120
- Second Owner: $58,340 (-9%)
- Third Owner: $51,890 (-19%)

---

#### **Finding 4: Value Proposition Leaders**
**Best Value Score (Power per Dollar):**
1. Ford - Value Score: 8.2
2. Kia - Value Score: 7.8
3. Hyundai - Value Score: 7.6

**Premium Positioned:**
- Mercedes - Value Score: 4.1 (high price, luxury positioning)

---

#### **Finding 5: Market Trends**
**Price Trend 2005-2024:**
- Steady increase from $45K (2005) to $72K (2024)
- Average annual growth: 3.2%
- Acceleration post-2020: 5.1% annually

---

## Section 6: Suggested Business Actions

### For Car Dealerships:
1. **Inventory Strategy**
   - Stock more hybrid vehicles (highest demand, premium pricing)
   - Focus on first-owner automatic transmission cars for premium segment

2. **Pricing Optimization**
   - Price automatic transmission +12-15% over manual
   - Apply 8-10% discount for second owner, 18-20% for third owner

3. **Marketing Focus**
   - Promote Ford and Kia for value-conscious buyers
   - Position Mercedes/BMW/Audi in luxury segment with service packages

### For Consumers:
1. **Best Value Purchases:**
   - Ford/Kia/Hyundai for power-per-dollar
   - Consider manual transmission for 14% savings

2. **Investment Perspective:**
   - First-owner automatic hybrid vehicles hold value best
   - Avoid third-owner vehicles (19% depreciation)

3. **Timing:**
   - 2019-2021 models offer best balance of features and depreciation

---

## Section 7: Challenges

### Technical Challenges:
1. **Data Type Management**
   - Issue: Some numeric fields imported as text
   - Solution: Used Power Query to convert data types

2. **Large Dataset Performance**
   - Issue: Initial slow rendering with 1,000 records and multiple visuals
   - Solution: Optimized DAX measures, used summarized tables

3. **Complex Calculations**
   - Issue: Value score calculation required careful DAX syntax
   - Solution: Used DIVIDE function to handle zero/null values

### Analytical Challenges:
1. **Outlier Impact**
   - Very high/low prices skewed averages
   - Mitigation: Added median price measures, used box plots

2. **Multi-Dimensional Analysis**
   - Challenge: Brand × Fuel Type × Year = too many combinations
   - Solution: Created separate pages for different dimensions

3. **Missing Context**
   - Dataset lacks condition, location, features data
   - Limitation: Cannot fully explain price variations

---

## Section 8: Ethical Considerations

### Data Privacy & Bias:
1. **Anonymization**
   - Dataset contains no personal information (VIN, owner names)
   - Car_ID is synthetic identifier

2. **Sampling Bias**
   - **Concern:** Dataset may over-represent certain brands
   - **Impact:** Could mislead consumers about true market distribution
   - **Mitigation:** Clearly label as "sample data," not market census

3. **Price Fairness**
   - **Concern:** Automated pricing algorithms could discriminate
   - **Impact:** If dealers use this for pricing, could perpetuate regional/demographic biases
   - **Mitigation:** Recommend human oversight, transparency in pricing factors

### Responsible Use of Insights:
1. **Decision Automation**
   -  **Don't:** Use solely for automated loan approvals
   - **Do:** Use as one input among many for human decision-makers

2. **Consumer Impact**
   - **Positive:** Helps buyers make informed decisions
   - **Risk:** Could pressure buyers into "value" choices against preferences

3. **Market Manipulation**
   - **Risk:** If widely adopted, could create self-fulfilling price predictions
   - **Mitigation:** Regular model updates, market validation

