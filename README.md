# Connected-Vehicles
The project involves fetching JSON data related to vehicles from an AWS S3 bucket. The retrieved data is then processed through a validation mechanism, as the JSON content may occasionally be incomplete or incorrect. An Azure Function is employed to ensure the integrity of the JSON data. Validated data is subsequently stored in an Azure SQL Server, establishing a robust and accurate repository for further utilization in the project.
## System Architecture
![image](https://github.com/bytehacktress/Connected-Vehicles/assets/68103201/9cd0a59a-4eef-4db1-9a0d-9c00d71c4625)
## Requirements
- Azure Data Lake Storage Gen 2
- Azure Data Factory
- Data Factory Pipeline
- Azure Functions
- Azure Key Vault
- Azure SQL DB
- AWS S3 Bucket
  
## Getting Started


## How It Works

1. **Fetch Data from AWS S3 Bucket:**
- Retrieve data from the AWS S3 bucket.
3. **Transfer Data to Azure Data Factory Landing Folder:**
- Use Azure Data Factory to move the data from AWS S3 to the landing folder.
5. **Validate JSON Data with Azure Function:**
  - Employ an Azure Function to check the integrity of the JSON data.
  - If validation passes, shift the data to the Staging folder.
  - In case of validation failure, relocate the data to the Rejected folder.
4. **Move Data from Staging to Azure SQL Server:**
  - Deploy Azure Data Factory to transfer data from the Staging folder to Azure SQL Server.

