Late-Arriving Data Puzzle — Microsoft Fabric DP-700
A PySpark and Delta Lake implementation of the Microsoft Fabric DP-700 Study Group Late-Arriving Data Puzzle.
Overview
This project demonstrates incremental data processing in Microsoft Fabric using PySpark and Delta Lake.
The solution uses three sets of customer and order data to deal with late arriving records and track customer information over time.
Key implementation areas
* Source-specific watermarks for incremental processing
* Duplicate detection and deduplication
* Data quality checks and default values
* Slowly Changing Dimensions (SCD) Type 1 and Type 2
* Inferred customer members
* Point-in-time customer key resolution for fact records
* Delta Lake tables for dimension and fact data
Notebook
DP700_Late_Arriving_Data_Puzzle_Final.ipynb
The notebook contains the PySpark implementation and validation steps.
Environment
* Microsoft Fabric
* Fabric Lakehouse
* PySpark
* Delta Lake
Note: The notebook was developed and executed in a Microsoft Fabric Lakehouse environment. The input CSV files are expected in the contest-provided Lakehouse Files area under Files/LateArrivingDataPuzzle_participant/.


