Late-Arriving Data Puzzle: Microsoft Fabric DP-700

This repo has my solution to the Microsoft Fabric DP-700 Late-Arriving Data Puzzle. I used PySpark in a Fabric Lakehouse to process customer and order data across three waves.

The tricky part was dealing with records that showed up at different times while keeping customer history accurate and making sure every order linked to the right customer record.

What the Notebook Does

The notebook works through the customer and order files one wave at a time. For each wave, it checks for duplicates, fills in missing values, and works out which records need to be inserted or updated.

Here's what it covers:

Tracks customer and order updates with separate watermarks.
Removes duplicate records before processing.
Fills in default values when customer info is missing.
Rejects orders with blank amounts.
Uses SCD Type 1 to overwrite customer details that don't need history.
Uses SCD Type 2 to keep a history of changes to selected customer attributes.
Creates inferred customer records when an order arrives before the customer's details do.
Updates those inferred records once the real customer info comes in.
Links each order to the customer version that was valid on the order date.

The final results are stored in two Delta tables: dim_customer and fact_orders.

Technologies Used
Microsoft Fabric
Fabric Lakehouse
PySpark
Delta Lake
Python
SQL
Repository Contents
File	Description
DP700_Late_Arriving_Data_Puzzle_Final.ipynb	The notebook with my solution
README.md	Project documentation
LICENSE	MIT License
Running the Notebook

To run it in Microsoft Fabric:

Create or select a Lakehouse named AuroraOutfittersLH.
Upload the contest CSV files to the Lakehouse Files directory:

Files/LateArrivingDataPuzzle_participant/

Import DP700_Late_Arriving_Data_Puzzle_Final.ipynb into your Fabric workspace.
Attach the notebook to the Lakehouse.
Run the cells in order.

The notebook expects the CSV files to be in the directory above.

Final Results

After all three waves were processed, the notebook produced:

203 rows in dim_customer, including historical and inferred customer records.
2,116 rows in fact_orders.

These numbers come from my final run on the contest data.

What I'd Improve Next

Right now everything runs through the notebook. For a production setup, I'd add a Fabric Data Factory pipeline to orchestrate the runs and a Delta control table to store the watermarks. That way processing could survive notebook restarts and handle future data arrivals more smoothly.

License

This project uses the MIT License. See the LICENSE file for details.
