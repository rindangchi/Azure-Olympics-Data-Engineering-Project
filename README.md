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

   8.1. Go to Author then click plus icon then choose pipelie --> pipeline.

     ![image](https://github.com/user-attachments/assets/4b899b9b-a8c7-44b2-8a3f-39745b670ebf)

   8.2. Give name for the pipeline as data-ingestion.

     ![image](https://github.com/user-attachments/assets/6264b6f5-e683-4e83-b953-a1738fe2e626)

   8.3. The pipeline steps:

   8.3.1. Copy data from data source to the data storage. The data is stored in in Github repository, so from the github respository we will load the data to the azure data factory. We will copy the raw data URL from the gihub reporitory.

   ![image](https://github.com/user-attachments/assets/10a77ba4-1358-407c-80e7-b958ee29b766)

   1. Create source
      - Click New on the bottom section.

      ![image](https://github.com/user-attachments/assets/9d49af6f-333b-4c12-801f-4c59216b8604)

      - Choose HTTP :

      ![image](https://github.com/user-attachments/assets/11da1154-4757-41b9-8b55-dc2f98fcd4b4)

      - Then choose .csv format :

      ![image](https://github.com/user-attachments/assets/c7c069d3-08c1-4e47-b21e-1621fc3ecc27)

      - In the properties section give the file name, and create new linked service

      ![image](https://github.com/user-attachments/assets/6fd23234-5c7f-4f5d-9909-f19ee5d19d31)

      - In the linked service section, complete all the required fields, then click create button in the bottom of the page:

      ![image](https://github.com/user-attachments/assets/e7404a19-195d-40fe-b6eb-6a5428060ea1)

      - Then will back to the Properties section, click OK:

      ![image](https://github.com/user-attachments/assets/27176f4f-4bec-42b8-a0c9-db026bb77ea6)

      - In the source section, we can preview the data:

      ![image](https://github.com/user-attachments/assets/34d952f8-5cf6-458a-bb25-fba3b597ea18)

      - After clicking preview data button:

      ![image](https://github.com/user-attachments/assets/44d21a72-1361-44ba-a1a0-585e36dec6d4)

   2. Create Sink.
      - Sink is target location where we will store the data.
      In the sink tab, choose create New.

      ![image](https://github.com/user-attachments/assets/d4a797ba-9bda-4818-84cc-2398dd030295)

      - Choose Azure Data lake 2 then click continue 

        ![image](https://github.com/user-attachments/assets/4f9b5ba3-14bd-454c-a905-e7ac5577a36f)

      - Choose file type, we will choose .csv. Then click continue 

        ![image](https://github.com/user-attachments/assets/2bad942f-c234-4b25-a334-341fc74e86b5)

      - In the properties section, give name and create new linked service

        ![image](https://github.com/user-attachments/assets/bb29dd04-fcb5-46a6-9127-ff98f49acd7c)

      - In the subcription section, choose subscription and storage account name, then click create

        ![image](https://github.com/user-attachments/assets/7a83a271-5316-410c-af72-7a71379537e5)

      - In the set properties section, choose the file path where we want to store the data and give name for the data that want to be stored. For import schema choose None. Then click OK

        ![image](https://github.com/user-attachments/assets/4263f95e-0f44-4062-8157-bcc6a033cad3).


   3. Click Validate, to validate the source and sink that just created.

      ![image](https://github.com/user-attachments/assets/522395ed-8e76-4a5c-9151-0b051179a043)

      Make sure that no error found during validation:

      ![image](https://github.com/user-attachments/assets/71f89cd8-00ef-4d38-a5ba-f10ad8107527)

   4. Once it is validated, then click Debug to process the copy file from github to azure data lake:

      Wait until the Debug is success:

      ![image](https://github.com/user-attachments/assets/e2fb55c0-6e24-440e-b410-e4f7514992b4)

   5. Once it is success, we can see in our raw data folder that a new file has been succeessfully created.
  
      ![image](https://github.com/user-attachments/assets/66310941-b496-4c6f-963f-f12f1280b0d2)
   
   6. Do the same thing for all the csv files.
   7. Do validate and debug the process untill success:

      ![image](https://github.com/user-attachments/assets/893ca158-740d-4325-89c5-d179b0c4872a)

   8. Check in the raw folder, all data have successfully copied :

      ![image](https://github.com/user-attachments/assets/8fdd29bd-5a60-48a3-b00a-201423f32b8b)

      
### Data Transformation in Azure Data Bricks

1. Create Databricks
   Search databricks in the search bar and open in the new tab

   ![image](https://github.com/user-attachments/assets/8f3bab39-3a49-4613-a7ca-429719ef60aa)

   It will open the databricks panel. Then click create Azure databricks service.

   ![image](https://github.com/user-attachments/assets/1fef4b1f-2b8f-4b39-a640-b5dd6c70f9dd)


2. Complete the required fields as below:

   ![image](https://github.com/user-attachments/assets/12fac703-b1b6-4496-8cd0-d856371fcb19)

3. Click Next until tab Review+Create. Then click Create button.

   ![image](https://github.com/user-attachments/assets/dce0b27e-a370-4329-9f36-35e3807b25f5)

4. It will show the process of deploying azure databricks.

   ![image](https://github.com/user-attachments/assets/54edea09-e395-4210-ae3b-f835a62acd8d)

5. Once teh deployment is complete then click go to resources button:

   ![image](https://github.com/user-attachments/assets/399d96d8-293d-4413-b1a0-1ca78e9bf5f5)

6. After that click Launch Workspace to go to the databricks workspace

   ![image](https://github.com/user-attachments/assets/680cabe2-2c5b-42c1-9e5b-11e15c0c0b3c)

7. In the databricks workspace, first we will create a compute, a compute is place where to run the pyspark code. Choose Create Compute: 

   ![image](https://github.com/user-attachments/assets/9628c990-fb64-4ed1-9d34-543b9ee4f05c)

8. After that it will show the compute panel, jut leave the default and change the access mode to Single User. After that click Create Compute.

   ![image](https://github.com/user-attachments/assets/bdd4297d-11d9-4787-9eec-711bc54cf398)

9. Once it i green means that teh cluster and the compute is ready

   ![image](https://github.com/user-attachments/assets/7cd65720-05b2-4cc7-9a01-6d2db6908738)

   When go to compute option, it said that our compute is ready :

   ![image](https://github.com/user-attachments/assets/2b9aa7b9-6cb9-4e37-8405-106fe7a8ae80)

10. Now we are ready to write a code to get data from the raw data lake, tranform it, then save it again to transform data lake

    Goto New button --> then create Notebook

    ![image](https://github.com/user-attachments/assets/cc68ada6-85b3-40fc-8edc-2e1bc6a95da3)

 11. We will be directed to the Notebook, then put a new name for the notebook.

     ![image](https://github.com/user-attachments/assets/a0c53bea-4a6d-4b73-921b-9f26e482efb6)

 12. To enable access data from Azure Data Lake to Azure Databrick, we need to make connection. In this case we need to create an App to give access between ADL and ADB. In simple way explanation we need to attach the data file in ADL to Azure data factory so we can easily access the data to the ADB, ADF will give us authentication to access the data from ADL to ADB.

     - Create App Registration
       In this step we will create app and get credentials to create connection to the ADB. 

       ![image](https://github.com/user-attachments/assets/628f8d2e-604d-46e1-9d5c-21f943454c0b)

     - Click Register App

       ![image](https://github.com/user-attachments/assets/dfd85d10-384d-4ebb-b873-ad5d5ba5deca)

     - Give the name App001 and click Register

       ![image](https://github.com/user-attachments/assets/172e10c9-a0db-493f-ab31-1963c78c66dc)

     - We will be directed to the App panel, in this part we need applicationID and directory tenant ID. Save those two things in a save place.

       ![image](https://github.com/user-attachments/assets/b8ec8305-16fa-4489-a194-47e600e7dd50)

     - Then choose Certificates & Secrets

       ![image](https://github.com/user-attachments/assets/e97f21bd-19d6-4349-ac27-1744a0c2f9db)

     - In the new section choose create client secret. Then give name and click Add.

       ![image](https://github.com/user-attachments/assets/75d5049e-bc5d-44c4-be0b-baa8754ecd4c)

     - In the client secret section, a new client secret is created and copy the value.

       ![image](https://github.com/user-attachments/assets/24d7d543-1af4-4ffb-a09d-b4daf7d4e11a)

     - Open the notebook again and copy the application id, tenant id and secret key on the provided space. In the real implementation it is not the best practice to directly put the key on the notebook, the best practice is to store the secret key and secret id in key vault.

       ![image](https://github.com/user-attachments/assets/6c2d8a8b-36c7-4ed1-b33a-f29033621340)


     - Then put container and storage account name on the below code, and also provide the mount point like below:

       ![image](https://github.com/user-attachments/assets/612e3a55-504d-45ed-add9-2b755e491301)

     -   Before run the code, we need to give access to the App001 to enable to access the data in the Data Lake.

         - Go to storage account then Choose IAM, like below:

           ![image](https://github.com/user-attachments/assets/1a015306-9cbe-477d-ac4b-ff180e6957d5)

        - Click Add --> Add Role Assignment

          ![image](https://github.com/user-attachments/assets/8db58d42-7d69-47b3-b1d8-f72ae736dbad)

        - Choose Storage Blob Data Contributor --> we will give access to the App to write, read, delete any object in the container 

          ![image](https://github.com/user-attachments/assets/5776aec9-0642-4c0c-95c5-0ed0534f15ad)
          
        - In the Add Role Assignment page, click select member

          ![image](https://github.com/user-attachments/assets/cdf8ce68-2948-4279-b7f7-00470e46414a)

        - Select the member --> App001

          ![image](https://github.com/user-attachments/assets/5c70a057-883b-43fd-87ef-6d790269efed)

          ![image](https://github.com/user-attachments/assets/a405866d-2ff2-46f6-8580-cb1c03bc16d6)

        - The app will be available here, then click next until Review + Assign part. Then Click Review+Asign button at the bottom of the page. 

          ![image](https://github.com/user-attachments/assets/d4b2a8eb-1a56-4116-84de-3ff28f2915db)

      - Then we can run the code:

        If it is True, means the connection is success:

        ![image](https://github.com/user-attachments/assets/924752a9-870a-4a48-ae96-62e095ab04ec)

        Then try to mount the file :

        ![image](https://github.com/user-attachments/assets/4e5b3eaf-067b-49dc-a934-a3370ce74d67)

        We can see that we are succefully access the folder:

        ![image](https://github.com/user-attachments/assets/0bb1eaf3-a25e-4145-914c-8e64cc8126f5)

     - Now, try to access a file using the spark.

      ![image](https://github.com/user-attachments/assets/97848515-3ac4-40f8-a89d-c0592e5b2a8e)

     - Then show the data :
    
       ![image](https://github.com/user-attachments/assets/bb98610a-a441-49a8-bbbe-7c6bdb1b74bb)

       We can see tha the header / column name is still considered as data, so that we need to change the code as below:

       An run again the code, now can see the headers now are in the correct place:

       ![image](https://github.com/user-attachments/assets/88d84b3d-1992-4d86-bb95-7b3a2e716931)

       


         

          




          
  


          



    
       
    
     - 


       





       


     





   






        

          


        

        


      


      





      





   

       






     



   





     




   



   

   
