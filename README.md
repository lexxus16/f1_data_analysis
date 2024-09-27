# Formula 1 Data Analysis with Azure Databricks

Welcome to my GitHub repository! Here, I’ve documented a data analysis project leveraging Azure Databricks' power to explore and analyze Formula 1 racing data. This project uses several cutting-edge tools and techniques to derive insights and create dynamic visualizations.

## Project Overview
In this project, I analyze Formula 1 racing data using various services within the Azure ecosystem. The project involves data ingestion, transformation, and analysis, resulting in insightful reports and visualizations. While this repository doesn’t include the Unity Catalog, all relevant Databricks notebooks are available.

## Tools and Technologies
- **Azure Databricks**
- **PySpark**
- **Spark SQL**
- **Delta Lake**
- **Azure Data Lake Storage Gen2**
- **Azure Data Factory**
- **Power BI**

## How to Get Started
To use the notebooks included in this repository, follow these instructions:

1. **Clone the Repository**
   - First, generate a GitHub token.
   - Link this token to your Databricks account.
   - Create a folder for GitHub within Databricks and commit your changes directly from there.

2. **Set Up Azure Databricks**
   - Launch an Azure Databricks workspace.
   - Configure the clusters and upload the notebooks from this repository into the workspace.

3. **Execute the Notebooks**
   - Open the notebooks in your Databricks workspace.
   - Follow the step-by-step instructions provided in the notebooks to run the analysis.

## Setting Up Azure Resources

### Azure Data Lake Storage Gen2
1. **Create a Storage Account**
   - Log in to the [Azure portal](https://portal.azure.com/).
   - In the left navigation pane, select **Storage accounts** and then click **Create**.
   - Choose your subscription and resource group.
   - Name your storage account, then click **Review + create** to finalize.

2. **Enable Hierarchical Namespace**
   - After creating the storage account, go to the **Data Lake Storage** settings.
   - Enable the **Hierarchical namespace** option.

3. **Create a Data Container**
   - Navigate to your storage account, and under **Containers**, click **+ Container** to create a new one for your data.

### Azure Data Factory
1. **Create a Data Factory**
   - From the Azure portal, click **Create a resource**, search for **Data Factory**, and select it.
   - Follow the prompts to choose your subscription, resource group, and region, and name your data factory.
   - Click **Review + create** to finish setup.

2. **Configure Linked Services**
   - Within the Data Factory dashboard, go to the **Manage** tab and select **Linked services**.
   - Click **+ New**, and choose **Azure Data Lake Storage Gen2** to configure the linked service with your storage account credentials.

3. **Build Pipelines**
   - Navigate to the **Author** tab, where you can create pipelines to move and transform data.
   - Use the **Copy Data** activity to transfer data from your source to your destination.

### Connecting Azure Data Lake Storage Gen2 and Azure Data Factory with Databricks
1. **Obtain Access Keys**
   - In the Azure portal, locate your storage account and go to **Security + networking**, then **Access keys**. Copy the access key provided.

2. **Configure Access in Databricks**
   - In your Databricks workspace, go to **Clusters**, select your cluster, and then click **Configuration**.
   - Add the following configuration to allow Databricks to access your Azure storage:
     ```plaintext
     spark.hadoop.fs.azure.account.key.<storage-account-name>.dfs.core.windows.net <storage-account-key>
     ```

3. **Automate Databricks Notebooks with Data Factory**
   - Add a **Databricks Notebook** activity to your Data Factory pipeline, and configure it to execute specific notebooks from your Databricks workspace.

## Workflow Summary
1. **Data Ingestion**: Data is sourced from the Ergast API, which contains a comprehensive dataset on Formula 1 races, drivers, circuits, and more. This data is stored in Azure Data Lake Storage Gen2.
2. **Data Transformation**: Using PySpark and Spark SQL, raw data is cleaned, transformed, and prepared for analysis. This includes filling in missing values, modifying data types, and generating new features.
3. **Data Analysis**: The cleaned data is analyzed to uncover trends and insights, including race outcomes, driver performance, and team statistics.
4. **Data Visualization**: The final results are visualized in Power BI, where interactive dashboards allow for easy exploration of insights.

## Key Highlights
- **Data Ingestion**: Collecting data from the Ergast API and storing it in Azure Data Lake.
- **Data Transformation**: Using PySpark and Spark SQL to clean and structure the data for analysis.
- **Data Analysis**: Applying statistical methods to discover meaningful trends and patterns in Formula 1 data.
- **Data Visualization**: Utilizing Power BI to create engaging and interactive dashboards for data interpretation.
