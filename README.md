# FBA_Celigo_autoMapping
This application is tailored for small businesses that integrate Celigo and NetSuite with Amazon Seller Central for Fulfillment by Amazon (FBA) shipments. Its main purpose is to simplify the management of product aliases in FBA shipments and automate the repetitive task of manually inputting FBA transfer orders. Please note that the NetSuite CSV import mapping is not provided; this program is specifically designed to map the FBA CSV file to the corresponding NetSuite CSV import file. You have the freedom to customize for your specific NS intergration.

## how to use PyInstaller to create an executable from the Python script
pyinstaller --onefile script_name.py


## How the Program Works:
CSV File Input: The application begins by prompting the user to input the file paths for two CSV files:

FBA CSV: This file contains shipment details from Amazon Seller Central FBA, orginal shippement detail file from Amazon, do not alter the file

Celigo CSV: This file holds data from Celigo, particularly product aliases under the Name column.
Validation: The program first checks whether the provided file paths are valid and whether the files exist. If any of the paths are incorrect, the program alerts the user and prompts them to try again. 

Note: export celigo alias eTail file in NS

## Data Processing:

The program loads the FBA CSV file, skipping the first 9 rows, which are often unformatted or contain irrelevant data.
It then loads the Celigo CSV file to prepare for data merging.
Merging Data:

The application merges the two CSV files based on the SKU column from the FBA CSV and the Name column from the Celigo CSV. This left join ensures that every SKU in the FBA file is matched with its corresponding alias data from the Celigo file.

## Data Transformation:

The merged data includes renaming the Parent Item column to Item and Total units to QTY. This renaming helps standardize the output, ensuring consistency with your data processing and reporting needs.

Output:

The program then selects the relevant columns (SKU, Item, QTY) and overwrites the original FBA CSV file with this newly merged and formatted data. This step ensures that your FBA shipment file is updated in place with the most accurate product alias information from Celigo.
Completion: Once the process is complete, the program informs the user that the FBA CSV has been successfully updated.

## Customization:
The source code provided above allows for easy customization. You can adjust column names, modify the merge logic, or expand the application to handle additional business logic specific to your workflow. This flexibility makes the application adaptable to various business needs, ensuring seamless integration between your NetSuite/Celigo system and Amazon FBA operations.


