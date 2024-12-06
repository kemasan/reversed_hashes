# reversed_hashes
This repository consists of a reversed hashes tracker notebook and a folder for checking results

## Objective:   
To identify and exclude transaction hashes with failed traces due to reversed calls, ensuring consistency in data between Flipside and Dune Analytics.

## Background:   
Transaction hashes may be labelled as successful in ethereum.core.fact_traces table on Flipside but failed in ethereum.traces table on Dune Analytics because some of the calls in the hashes were reversed. This discrepancy can affect data analysis accuracy. To address this, hashes with reversed calls should be excluded from calculations.


## Requirements:
- Dune Analytics account;
- Flipside account;
- python, pip, jupyter notebook (any other working environment)

## Instruction:
- create and activate a virtualenv
- clone the notebook
  

## Working notebook
Steps to Identify and Exclude Failed Traces:
Daily comparison of amounts:
- Run the Flipside query to save the daily amounts in Lido Buffer for the checking period on Flipside in CSV file (flipside_amount_date.csv)
- Run the Notebook to save the daily amounts in Lido Buffer for the same period on Dune Analytics in CSV file (dune_amount_date.csv)
- Compare the daily amounts, if there is a discrepancy in amounts, save the dates and amounts of mismatched data in a CSV file (mismatched_date.csv).

Daily comparison of hashes:
- For each date in mismatched_date.csv, run a query to get the hashes for the giving day on both Dune Analytics and Flipside.
- Save the results as dune_hashes_date.csv and flipside_hashes_date.csv respectively.
- Compare the hashes in dune_hashes_date.csv with flipside_hashes_date.csv to identify hashes that exist in the Flipside list but not in the Dune list.
- Save found hashes in a CSV file named to_check_date.csv.

Note: Exclude the current date from the comparison due to differences in table update times across platforms







