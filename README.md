# Building-an-Azure-Data-Lake-for-Bike-Share-Data-Analytics
### The goal of this project is to develop a data lake solution using Azure Databricks using a lake house architecture

In this project, you'll build a data lake solution for Divvy bikeshare.

Divvy is a bike sharing program in Chicago, Illinois USA that allows riders to purchase a pass at a kiosk or use a mobile application to unlock a bike at stations around the city and use the bike for a specified amount of time. The bikes can be returned to the same station or to another station. The City of Chicago makes the anonymized bike trip data publicly available for projects like this where we can analyze the data. The dataset looks like this:

![image](https://user-images.githubusercontent.com/61830624/196221683-aa224d16-e11f-493c-b5ce-dd98a7dfb869.png)


### The goal of this project is to develop a data lake solution using Azure Databricks using a lake house architecture. We will:
- Design a star schema based on the business outcomes listed below;
- Import the data into Azure Databricks using Delta Lake to create a Bronze data store;
- Create a gold data store in Delta Lake tables;
- Transform the data into the star schema for a Gold data store;

## The business outcomes we are designing for are as follows:
### 1. Analyze how much time is spent per ride
- Based on date and time factors such as day of week and time of day
- Based on which station is the starting and / or ending station
- Based on age of the rider at time of the ride
- Based on whether the rider is a member or a casual rider

### 2. Analyze how much money is spent
- Per month, quarter, year
- Per member, based on the age of the rider at account start

### 3. Analyze how much money is spent per member
- Based on how many rides the rider averages per month
- Based on how many minutes the rider spends on a bike per month


# Star Schema Design
Star schema I constructed based on the business questions:

![image](https://user-images.githubusercontent.com/61830624/196258984-aef0fe34-44bf-4024-8f1f-c502105ddfeb.png)

# Extract Step
### Step 1 Create Azure Databricks workspace
![image](https://user-images.githubusercontent.com/61830624/196225584-0c4496f4-4e21-4dc2-872c-7f1a7db325d8.png)

### Step 2 Create Spark cluster in Databricks Workspace
![image](https://user-images.githubusercontent.com/61830624/196231321-a43e23d8-6c05-49da-8710-955aeabb0542.png)

### Step 3 Upload data to DBFS
![image](https://user-images.githubusercontent.com/61830624/196242488-7ec06f1d-3988-455c-875e-859484a38b00.png)
![image](https://user-images.githubusercontent.com/61830624/196243725-047d8634-f9cc-4039-adfe-2709e0a525a8.png)

### Step 4 Extract information from CSV files stored in Databricks and write it to the Delta file system.
Load data into DataFrame
![image](https://user-images.githubusercontent.com/61830624/196245703-caa3cd6a-d837-4fe9-bc75-018c34650bea.png)

Get data from DataFrame to Delta Lake
![image](https://user-images.githubusercontent.com/61830624/196249525-595ee934-7b1d-4c05-8108-4ead408f77c7.png)

Data Successfully loaded to delta files
![image](https://user-images.githubusercontent.com/61830624/196250017-b36f6dc7-cb59-4e46-8cc4-a601406c6f79.png)

# Load Step
Create Tables & Load data from Delta Files 
![image](https://user-images.githubusercontent.com/61830624/196250991-be84db92-b332-427d-9cfa-7d186df26f13.png)

Tables have successfully been created
![image](https://user-images.githubusercontent.com/61830624/196251318-85552802-6be1-4fbb-a42f-302be48a36aa.png)

# Transform Step
Create riders dimension
![image](https://user-images.githubusercontent.com/61830624/196252724-c8f013c2-7725-48a9-ae19-d248dc117a4a.png)

Station dimension
![image](https://user-images.githubusercontent.com/61830624/196253012-aa0642c3-0154-4c4d-8d36-b0a742c89e89.png)

We do the same process for the other dimension and Facts tables
All tables have been successfully created
![image](https://user-images.githubusercontent.com/61830624/196257583-3499e03e-5e26-4080-82f8-0e3958733384.png)





