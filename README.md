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

     - We need to access all of the csv file so let's copy the code five times:

       ![image](https://github.com/user-attachments/assets/8c14ae9d-72f1-4e08-ab84-5dedb544bcff)

     - Next we can see the schema of each data by using below code:

       ![image](https://github.com/user-attachments/assets/cff20415-706f-43d1-a585-9cc1ecf24bef)

     - In this case, for the entriesgender teh format of Female, Male, and Total column is wrong, it should be in integer not in string.
    
       The entriesgender data:
    
       ![image](https://github.com/user-attachments/assets/3e1fe805-f491-4b0f-9c75-062eb2e2ae63)


       Format of each column of entriesgender table:

       ![image](https://github.com/user-attachments/assets/bc2da528-3c52-4012-bccc-60a4201e63f4)

       Now let's change the format.
       Before that we need to import those below functions.

       ![image](https://github.com/user-attachments/assets/5fecfd9f-cef3-4ebc-b6e4-402014e8ebbb)

       Let's write below codes to change data type from string to integer:

       ![image](https://github.com/user-attachments/assets/91a71920-d81a-4a3f-a48e-f7df71b6fa65)

       When we print the schema again the data type now should be in integer:

       ![image](https://github.com/user-attachments/assets/adf7d85e-65be-4b09-9a39-de999a137dac)

     - Let's access and read the medals data

       The medals data:

        ![image](https://github.com/user-attachments/assets/5b7f7728-d130-47f2-b799-1276a6a52f5c)

       medals data schema:

       We can see tha columns with numeric data still have data type string.

       ![image](https://github.com/user-attachments/assets/461c0ab5-ab1a-4e44-8349-be894a827e46)

       So that we need to change it again. There is another way we can apply to change teh data type. We can change the data type directly when we are reading the file, means that we allow the spark to understand the correct data type for ecah column.

       just revise the code like below, add option inferschema as true.

       ![image](https://github.com/user-attachments/assets/3cc73ef2-cf76-4aa0-8652-e4acfec2da48)

       When we print the schema again, we can see that the data types already change to the correct format:

       ![image](https://github.com/user-attachments/assets/5b328d38-c9fb-4731-b504-200617718d75)


   ### Load Data to the Azure Data Lake Transformation Folder

   After we successfully doing a simple tranformation, then we will load the transformed data to the transform-data folder in Azure Data Lake:

   Write below codes:

   ![image](https://github.com/user-attachments/assets/17469dea-d416-4527-8fba-e78100a3adf4)

   Then let's check the tranform-data folder, we will see that there is new folder named athletes already created.

   ![image](https://github.com/user-attachments/assets/06eba3d9-f77e-40e1-ad64-0d3e41de4180)

   When we open the folder, there will be several files. If we want to make it just in one file we can use pandas dataframe.

   ![image](https://github.com/user-attachments/assets/69e05aef-7eae-4305-b8aa-f5961fa46af5)

   Let's do for all the tables:

   ![image](https://github.com/user-attachments/assets/fe5d6d4e-9c59-467f-af23-41ec57c7d408)

   Now all data have been loaded to the transform-data folder:

   ![image](https://github.com/user-attachments/assets/c345785b-71c8-4dda-a612-b2b0a1d5069f)


   ### Analytics Using Azure Synapse

   Now after load the transformed data to the transform folder, we will do analysis using azure synapse.

   1. In the srarch bar, serach azure synapse analytics

      ![image](https://github.com/user-attachments/assets/0f163097-cfc7-4d6c-abd1-bfa052fbc6c2)

   2. Click on the create button

      ![image](https://github.com/user-attachments/assets/ac994c6c-ec30-49cb-8c33-737efbc43cf0)

   3. In the basic setting input the details like below:

      ![image](https://github.com/user-attachments/assets/2426a54e-16ac-43e7-b9b4-b7e4e906c0b9)

   4. Clikc Next until Review+Create, wait the validation until it is done then clck create.

      ![image](https://github.com/user-attachments/assets/46683184-04d9-4d12-94a6-5fdc1e9cdf5b)

   5. Wait until the deployment is complete then go to resource group

      ![image](https://github.com/user-attachments/assets/6cba638d-c9f0-4b6b-bacc-c12ba16dc1ae)

   6. It is page we can see all reource that we have created,such as databrick, datafactory, synapse, and account group.

      ![image](https://github.com/user-attachments/assets/6241797d-fbf9-4924-a90f-847df38a4df1)

   7. Click tokyo-olympic-synapse. It will be directed to synapse page that contains all information abut azure synapse. In the page choose open synapse studio.

      ![image](https://github.com/user-attachments/assets/bb5a767c-3328-4073-a174-446d910137d4)

   8. It will be directed to synapse analytic page like below:

      ![image](https://github.com/user-attachments/assets/07a45ca6-1a11-4bf7-ad4f-215184c5b7d4)

   7. First, let's load our database to the azure synapse. Choose Data --> Choose Plu button --> Choose Lake Database

      ![image](https://github.com/user-attachments/assets/96b70900-6634-4a39-9d1b-6822b3cc8896)

   8. We can see that table i still empty, and in the right side give name for the database.

      ![image](https://github.com/user-attachments/assets/e4777400-58d5-4fb5-9b94-0b833e681acc)

   9. Then create external table in the datalake and input the required fields like below. In the input file/folder choose where the tranformed data are stored.

      ![image](https://github.com/user-attachments/assets/744f6d2d-97ce-4757-9a75-ced0e8e429ec)

   10. Then click continue, and it will go to the below section, tick Infer first row as column name. Then click create button.

       ![image](https://github.com/user-attachments/assets/ecc68852-971e-43ba-9036-3d0e32373dd1)

   11. It will go to the workspace like below. We can change the data type, column name etc, juct clik validate then publish to publish the actual database in synapse.

       ![image](https://github.com/user-attachments/assets/075ea926-7297-42da-904d-a54ee8887f18)

   12. Click publish

       ![image](https://github.com/user-attachments/assets/b32e2bb2-d6ff-44cb-81e4-45a2ec5f69f6)

   13. After refresh the database, in the left ection we can see that the table is successfully loaded to the synapse:

         ![image](https://github.com/user-attachments/assets/429bb929-7228-46ea-ad5d-5c8586da24b8)

   14. Now, with the same steps, let's import all tables to the azure synapse


       ![image](https://github.com/user-attachments/assets/8f5e1d71-ad1d-4031-ac34-f77a8814bbf1)

   15. Then we can create SQL Script:


       ![image](https://github.com/user-attachments/assets/1e6d08c2-80f4-4e47-81e8-6f105248252b)

       Do some analysis using SQL script:


       ![image](https://github.com/user-attachments/assets/7d64e9d3-8f03-4cd5-aa53-fa16a505212f)


       ![image](https://github.com/user-attachments/assets/7fadda8e-9761-4041-b454-1fdf6c0b4abf)

       
### Analytics in Power BI
1. Open the power BI desktop
2. On the first page click "Get Data from another Source"

   ![image](https://github.com/user-attachments/assets/b019e1bf-0ad4-49e5-af70-910e43a91051)

3. Choose Azure then choose Azure Synapse Analytics SQL. Then choose Connect:

   ![image](https://github.com/user-attachments/assets/49c6239a-223b-4d34-aec5-0bf4e407b555)

4. There will be a pop up like below, asking to input Server and database name.

   ![image](https://github.com/user-attachments/assets/cbafaead-27bd-44fa-9e5c-d6694c259bca)

5. To get the server name, go to Azure Synapse and click Setting --> Properties, from here scroll down and copy detail from field "Serverless SQL Endpoint"

   ![image](https://github.com/user-attachments/assets/09ce2e37-f878-443d-9da4-7ba4c5bdff62)

6. After input the detail, then click OK

   ![image](https://github.com/user-attachments/assets/59143caf-2d23-478a-8bdf-2b32fa5265ca)

7. Choose microdoft account which used to createt the database

   ![image](https://github.com/user-attachments/assets/579b08af-36a6-4c1b-96d4-969047e02e12)

8. After Sign-in then click Connect

   ![image](https://github.com/user-attachments/assets/6d2004d4-b18b-4cd9-8a8a-f756b7f8d418)

9. After Connect, now we can see all the table we have created in the Azure Synapse

   ![image](https://github.com/user-attachments/assets/0d6a9175-c94c-4e2b-bc41-5edf00afc9cb)

10. Then click Load.

   ![image](https://github.com/user-attachments/assets/fc6bc80c-af59-4e9c-ac49-294857b978ba)

11. It will load the data

   ![image](https://github.com/user-attachments/assets/24c12672-675b-490e-92b7-574b1ebcf727)

 12. After Load is success, we can see the data in the right side

   ![image](https://github.com/user-attachments/assets/06d5db03-ce57-46d9-a3fb-4435d3ad07db)

 13. Then let's create the dashboard!

   ![image](https://github.com/user-attachments/assets/8ec022e5-981f-48f2-a70b-100658c5cb01)


   
    
   
   


   

   





   


      


       



       


       

      

      





      

      

      

   






   


         

       

  



  
  


       

       


         

          




          
  


          



    
       
    
     


       





       


     





   






        

          


        

        


      


      





      





   

       






     



   





     




   



   

   
