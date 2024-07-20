# Azure-Olympics-Data-Engineering-Project
This project is to do end to end data engineering using Azure Technologies for Olympics Data 2021

## Sign Up Azure Account

## Data Pipeline 

![image](https://github.com/user-attachments/assets/2e7c272b-ffab-4f0c-a4ca-0da63509a985)


1. Data source : Tokyo Olympics Data 2021 from Google.
   Containing below tables.
2. Copy the data from data source to Azure data storage using data factory --> take raw data
3. Create simple pipeline to upload data to data lake gen 2
4. Azure data bricks : create simple data transformation. Create simple pyspark code. remove duplicates, drop some columns, rename columns
5. Upload the transformed data into data lake gen 2
6. Create sql query in azure synapse
7. Build dashboard uing powerbi

## Steps

1. Go to Azure portal

   ![image](https://github.com/user-attachments/assets/e4bd0d0d-61fd-4b19-9df3-47e72f6f132e)


   Data ingestion from external source to data lake storage
   
### Create Storage Account
   
   - Go to Storage Accounts

   ![image](https://github.com/user-attachments/assets/b6ea467a-8640-42d6-97f8-95cc0540c36b)

  
   - There will be a storage account dashboard like below:
  
   ![image](https://github.com/user-attachments/assets/1b191c99-71b7-49ce-83cb-5878b290bf5b)

   - Then click Create Storage Account
  
   - Then will be directed to the create storage dashboard, then in this page choose the default subscription (it should be free trial) and after that create resource group, just create tokyo-olimppic

     ![image](https://github.com/user-attachments/assets/d022aaed-b577-42a3-98d4-ca5796557290)

   - Add storage account name and put the region, choose the nearest region from your location 

     ![image](https://github.com/user-attachments/assets/062319ac-6ab5-4ff3-b009-720b278437f0)

   - Then click Next :

     In this part tick on : Enable Hierarchical Namespace

     ![image](https://github.com/user-attachments/assets/4cfda9ce-b2b1-4b7f-a540-fef9a11f453a)

   - Then click Next
  
   - In this part, do not need to do anything (do not make any change on this part)

     ![image](https://github.com/user-attachments/assets/93fe560c-c4e1-4055-b697-7f975ea6d09b)

   - Just go next until Review+Create Part and wait until the validation process is complete
     After validation is complete then just click create button.

     ![image](https://github.com/user-attachments/assets/470cd5ac-5c48-4ed8-9069-aa220e9a9677)

   - Now deployment is complete and will show like this:

     ![image](https://github.com/user-attachments/assets/459d9e20-1d3b-43e7-b163-8b12665a3856)

   - Then go to the storage account and we will see the entire storage account like below :

     ![image](https://github.com/user-attachments/assets/355a137c-d45f-4ef3-af5b-f40cc7d164cf)


### Create Container

Container is a place where we store our data. 

- Click Conatainer

![image](https://github.com/user-attachments/assets/9974536b-db19-4ff9-bb96-e5d3445b3a5b)

     
- Then give name for the container, then click create button

![image](https://github.com/user-attachments/assets/56cdbd22-8f19-4f8d-b3d6-2d41843ebabd)

- A new container will be created

![image](https://github.com/user-attachments/assets/cb37420d-77ae-438a-804f-cd8db4be2965)

- Click om the container and create 2 folders. One for raw data and the second is for transformed data. To create new folder click on the directory section.

![image](https://github.com/user-attachments/assets/15aa3cf2-066d-4012-81f1-a393461dd052)

### Data Ingestion in Azure Data Factory 





     




   



   

   
