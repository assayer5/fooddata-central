## Project: FoodData Central
### Overview
Cleaning, organizing, and filtering ~2M entries from the USDA FoodData Central database for later visualization in [Tableau Public](https://public.tableau.com/app/profile/j.c4963/vizzes).


### Some Details
The USDA FoodData Central database stores label and nutrition information on foods sold in the United States. The data on packaged food is spread across multiple tables:
- *branded_food.csv*: a table containing columns for text data such as the product brand, food category, and ingredients
- *food.csv*: a table containing the product descriptions
- *nutrient.csv*: a reference table of nutrient names and their unit of measure, with a numerical identifier for each nutrient
- *food_nutrient.csv*: a table listing the nutrient amounts present in each food product
  
I was interested in looking at the nutrient composition of the packaged foods available to us. Maybe the data could help me make choices at the grocery store! To this end, I divided the data cleaning process into two stages: text cleaning and numerical cleaning.

Text cleaning:
>*clean_brandedfood_csv.ipynb*
>
>Using the product ID to link database entries across tables, I joined the brand, category, and ingredient information with the product descriptions. This allowed me to use key words in the product descriptions to recategorize food products that were either incorrectly categorized or uncategorized (aka NaN values). I further harmonized the data by taking the numerous food categories present in the database and narrowing it down to a handful, creating subcategories to add a bit of granularity, and dropping entries that I wasn't interested in visualizing (such as condiments and baking mixes. I don't consider those foods that you consume by themselves.).
  
Numerical cleaning:
>*clean_nutrientinfo_csv.ipynb*
>
>For the nutrient data, I used the reference table to associate the nutrient names and units with their corresponding amounts present in each food product. To focus on the most common nutrients listed on food labels, I only kept a subset of the nutrient names. Where necessary, I condensed multiple nutrient names referring to the same thing into a single common name. Turning my attention to the nutrient values, I sought to clean up unreasonable values. Where needed, I scaled the values to a 100g portion and corrected unit conversion errors that put values multiple decimal places out of reason.

Once the text and numerical cleaning stages were complete, I combined the resulting datasets and dropped duplicate entries in the notebook file *clean_joined_csvs.ipynb*. The visualization summarizing the nutrient composition of the resulting food products is available on [Tableau Public](https://public.tableau.com/app/profile/j.c4963/vizzes).

If processing these database entries were to become a regular occurance, these notebooks could serve as a reference to guide the the design of functions and scripts. Ideally, the data retrieval and cleaning would be systematic and automated.


### Language
Python

### Packages Used
pandas, numpy, matplotlib, seaborn

### Resources
[FoodData Central](https://fdc.nal.usda.gov/index.html)

