# ✈️ Flight Data Analysis with Python

## Project Overview  
This project analyzes a dataset of domestic flight bookings across major Indian cities to uncover key trends in airline pricing, travel duration, and scheduling. Using Python, the analysis provides actionable insights for airline and travel stakeholders by identifying patterns in fares, routes, and booking behavior.

---

## Objectives  
- **Data Exploration:** Understand how different flight attributes (airline, class, stops, etc.) relate to price.
- **Data Cleaning:** Prepare and transform the raw CSV into an analysis-ready dataset.
- **Feature Analysis:** Study how variables like stops, class, and days left until departure affect price.
- **Visualization:** Build clear visuals to communicate pricing trends, flight efficiency, and customer tradeoffs.

---

## Data and Preprocessing  

### Data Source  
The dataset was scraped from a travel booking website and contains datewise flight records across multiple Indian cities. Each row represents a single flight option between a source and destination city.

### Data Cleaning  
- **Handled missing / inconsistent values** to ensure data integrity.
- **Converted columns to correct types**, e.g. parsing times and dates into `datetime`.
- **Derived new features:**
  - `Days Left`: days between the booking date and the travel date.
  - `Departure Time` / `Arrival Time` bins: grouped time windows (e.g. Early Morning, Morning, Afternoon, Evening, Night, Late Night).
- **Standardized categorical text** (airline names, stop labels, etc.).
- **Filtered out extreme outliers** in price and duration to avoid distortion in visuals.

---

## Feature Overview  
Below are the main features in the cleaned dataset:

- **Airline**  
  Airline company name (categorical; multiple unique airlines in the dataset).

- **Flight**  
  Flight code/identifier.

- **Source City**  
  City the flight departs from.

- **Destination City**  
  City the flight arrives in.

- **Departure Time (binned)**  
  Labeled time window for when the flight leaves (e.g. Morning, Afternoon, Evening, Night).

- **Arrival Time (binned)**  
  Labeled time window for when the flight lands.

- **Stops**  
  Number of stops/layovers (e.g. Non-stop, 1 Stop, 2+ Stops).

- **Class**  
  Travel class (Economy or Business).

- **Duration**  
  Total travel time in hours from departure to arrival.

- **Days Left**  
  Days between booking date and departure date.

- **Price**  
  Ticket fare. This is the main target variable we analyze.

---

## Libraries Used  
**Data Handling:**  
- `pandas`  
- `numpy`

**Visualization:**  
- `matplotlib`  
- `seaborn`  

**Notebook Environment:**  
- Jupyter (`%matplotlib inline`)

---

## Methodology  

1. **Load & Inspect Data**  
   - Imported the CSV into a Pandas DataFrame.
   - Ran initial profiling: data types, missing values, unique value counts, distributions.

2. **Clean & Engineer Features**  
   - Created derived fields like `Days Left`, and binned departure/arrival times to make time-of-day analysis easier.
   - Ensured categorical fields (e.g. airline, stops, class) were consistent and readable.

3. **Exploratory Data Analysis (EDA)**  
   - Grouped by airline, route, class, and number of stops to summarize average price and duration.
   - Used visualizations (boxplots, bar charts, histograms) to compare pricing behavior and travel efficiency across categories.

4. **Insights Extraction**  
   - Interpreted patterns that would matter to real stakeholders (e.g. “Is it worth paying more for nonstop?”, “How much more does Business Class actually cost?”, “How risky is last-minute booking?”).

---
## Data Visualization  

The notebook includes multiple plots to surface flight behavior patterns:

- **Price by Airline**  
  Bar/box plots comparing average fares for each airline to highlight which carriers are generally cheaper or more premium.

- **Stops vs. Price and Duration**  
  Visuals showing how 0-stop, 1-stop, and 2+ stop flights differ in both total travel time and ticket price.

- **Class-wise Fare Distribution**  
  Boxplots comparing Economy vs Business class to quantify premium pricing.

- **Days Left vs. Price**  
  Line/scatter-style views to show how fares increase as the departure date gets closer.

- **Popular Routes**  
  Aggregations of the most common source–destination city pairs and their typical price range.

- **Correlation Heatmap (numerical features)**  
  Quick view of which numeric features (e.g. Duration, Days Left, Price) move together.

---

## Results  

- **Price Trends by Airline**  
  Some airlines positioned themselves as budget options with consistently lower fares, while others behaved like premium carriers and charged higher average ticket prices on the same or similar routes.

- **Impact of Stops on Price and Duration**  
  - Non-stop flights were the fastest but also the most expensive option on average.  
  - One-stop and multi-stop flights generally cost less but significantly increased total travel time.  
  - This confirms a common tradeoff for travelers: *pay more for speed, or save money and spend more hours in transit.*

- **Class-wise Fare Difference**  
  - Business class tickets were typically **3–4× higher** than economy on the same route.  
  - On certain short-haul routes, this gap narrowed, suggesting low willingness to pay for Business on quick flights.

- **Booking Lead Time (Days Left)**  
  - Flights booked very close to the travel date (within ~7 days) showed a steep jump in price.  
  - Tickets booked ~3+ weeks in advance were noticeably cheaper.  
  - This supports the intuition that **last-minute = penalty pricing**.

- **Duration vs. Price Relationship**  
  - Longer total trip duration tended to align with higher prices, but not perfectly.  
  - Exceptions appeared on short-haul nonstop flights from premium airlines, where prices were high despite short duration — indicating a brand/service premium.

- **High-Demand City Pairs**  
  - Certain routes (e.g. major metro-to-metro pairs) had both high frequency and strong price competition.  
  - Other routes showed large price swings, suggesting fluctuating demand or limited carrier competition.

Overall, the analysis shows how ticket cost is shaped by a mix of controllable factors (when you book, which class you choose, how many stops you tolerate) and less controllable ones (which city pair you’re flying, which airlines even service that route).

---

## Conclusion  

This analysis translates raw flight listings into clear business and traveler insights:
- For **travelers**: Book earlier, expect to pay a premium for nonstop and for Business class, and watch certain high-volatility routes.
- For **airlines / travel platforms**: There are clear pricing tiers by airline and cabin class, and strong signals that urgency (low “Days Left”) allows for price lift.

The project also shows the value of exploratory data analysis (EDA): with just Python and a structured CSV, we can identify which levers drive airfare and where there may be opportunities for optimization.

---

## Future Work  

- **Price Prediction Model:**  
  Train a regression or tree-based model to predict ticket price using features like airline, class, stops, days left, and city pair.

- **Route Recommendation / Optimization:**  
  Recommend cheaper alternative routes (e.g. 1-stop vs nonstop) given a user’s budget and time tolerance.

- **Interactive Dashboard:**  
  Deploy an interactive dashboard (Tableau/Plotly) so users can explore prices by route, airline, or departure window.

---

## Dependencies  

```text
pandas
numpy
matplotlib
seaborn
jupyter
