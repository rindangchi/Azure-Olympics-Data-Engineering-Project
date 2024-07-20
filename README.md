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

1. In the search bar, type Azure Data Factory and choose Data Factories

   ![image](https://github.com/user-attachments/assets/065a0b2d-d70b-495f-8736-d9fcb634000b)

2. It will be directed to Data Factories page, then it this page create new  a Data Factory by clicking blue button " Create Data Factory "

   ![image](https://github.com/user-attachments/assets/7d3dc2fb-2051-49fe-9bd6-95136e3ca0db)

3. Choose default subscription then choose the tokyo-olympic in the resource group section

   ![image](https://github.com/user-attachments/assets/6cae3b90-4dd0-4499-a776-79e36fc61c2c)

   Input the instance name and choose the region:

   ![image](https://github.com/user-attachments/assets/97af7790-50d4-4cba-b847-049678da770e)

4. Just go to Next until Review + Create section. Once the validation is complete, just click the create button.

   ![image](https://github.com/user-attachments/assets/ab0686aa-ff41-4d85-8fb3-516fd7e1828b)

5. When deploymeny is complete, will be directed to below page, then click go to resource button.

   ![image](https://github.com/user-attachments/assets/864dc875-7587-40b9-8d7a-f1cd786821be)

6. Then will be directed to the data factory page like below. 

   ![image](https://github.com/user-attachments/assets/a49a4373-c968-4817-8c73-b23d0e1ac6ca)

7. Then click on the launch studio button. Then it will be directed to Azure data factory panel.

   ![image](https://github.com/user-attachments/assets/3caaca05-7d1d-48ca-a970-6cf2a3490e07)

8. Create Pipeline :

   - Go to Author then click plus icon then choose pipelie --> pipeline.

     ![image](https://github.com/user-attachments/assets/4b899b9b-a8c7-44b2-8a3f-39745b670ebf)

   - Give name for the pipeline as data-ingestion.

     ![image](https://github.com/user-attachments/assets/6264b6f5-e683-4e83-b953-a1738fe2e626)

   - The pipeline steps:

     - Copy data from data source to the data storage. The data is stored in in Github repository, so from the github respository we will load the data to the azure data factory.

       ![image](https://github.com/user-attachments/assets/10a77ba4-1358-407c-80e7-b958ee29b766)








     



   





     




   



   

   
