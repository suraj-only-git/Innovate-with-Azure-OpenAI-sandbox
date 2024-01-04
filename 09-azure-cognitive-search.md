# Exercise 8: Knowledge Mining with Azure Cognitive Search

In this exercise, you'll embark on a journey of knowledge mining using Azure Cognitive Search. Unleash the power of AI to organize, extract valuable insights, and transform unstructured data into actionable knowledge

## Lab Scenario
Contoso aims to enhance its customer experience and business intelligence capabilities through advanced knowledge mining. Leveraging Azure Cognitive Search and Azure OpenAI, Contoso plans to organize and extract valuable insights from vast amounts of unstructured data, including customer reviews, product descriptions, and industry reports.

## Lab objectives

In this lab, you will perform the following:

- Provision an Azure OpenAI resource
- Deploy a model
- Provision an Azure AI service
- Set up the configuration for AI Orchestration and perform various tasks related to ACS.

## Architecture Diagram

   ![](media/arc9.png)

## Task 1: Provision an Azure AI services

Before you can use Azure AI services, you must provision an Azure AI services resource in your Azure subscription.

1. In the **Azure portal**, search for **AI Search** and select **AI Search**.

   ![](media/ai-search.png)
   
1. Select **AI Search** and select **cognitive-search-service-<inject key="Deployment ID" enableCopy="false"></inject>**

   ![](media/img001.png)

1. In the **cognitive-search-service-<inject key="Deployment ID" enableCopy="false"></inject>**, click on **Keys** under Setting from the left menu, copy the **Primary admin key**, and paste the values it a Notepad we need this value in the future exercise.

     ![](media/ai-search-key.png)

## Task 2: Setup configuration for AI Orchestration

1. Open **Visual Studio Code** from the Lab VM desktop by double-clicking on it.

   ![](media/vscode.png "Deploy model configurations")

1. In Visual Studio Code from menu bar select **File(1)>open folder(2)**.   

   ![](media/image-rg-02.png "Deploy model configurations")

1. Within **File Explorer**, navigate to **C:\LabFiles** select **intro-to-intelligent-apps-main**(1) click on **Select folder(2)**

   ![](media/select-folder.png "Deploy model configurations")

1. In **Visual Studio Code**, click on **Yes, I trust the authors** when **Do you trust the authors of the files in this folder?** window prompted.

   ![](media/image-rg-18.png "Deploy model configurations")

1. Click on **.env** file replace the values and save the file by pressing **ctrl + s**.

   | **Variables**                            | **Values**                                                                              |
   | ---------------------------------------- |-----------------------------------------------------------------------------------------|                                          
   | AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME   | **text-embedding-ada-002**                                                              |
   | AZURE_COGNITIVE_SEARCH_SERVICE_NAME      |  **cognitive-search-service-<inject key="Deployment ID" enableCopy="false"></inject>**  |
   | AZURE_COGNITIVE_SEARCH_ENDPOINT_NAME     | Replace the value with the **COGNITIVE SEARCH Url** which you noted from Exercise 8 Task 1 step 6   |
   | AZURE_COGNITIVE_SEARCH_INDEX_NAME        | **cognitive-search-lc-python-index**                                                    |
   | AZURE_COGNITIVE_SEARCH_API_KEY           | Replace the value with the **COGNITIVE SEARCH API Key** which you noted from Exercise 8 Task 1 step 7|

   ![](media/ai-env.png)

## Task 3: AI Orchestration with Azure Cognitive Search

In this task, we'll walk through using one of Azure's vector stores, Azure Cognitive Search.

1. In the Visual Studio Code navigate to **intro-to-intelligent-apps-main\labs\03-orchestration\04-ACS** folder and select **acs-lc-python.ipynb**.

   ![](media/lc-python.png)

   > **Note**: In Task 4 we have already updated the values for **AZURE_COGNITIVE_SEARCH_SERVICE_NAME, AZURE_COGNITIVE_SEARCH_ENDPOINT_NAME, AZURE_COGNITIVE_SEARCH_INDEX_NAME, AZURE_COGNITIVE_SEARCH_API_KEY**.

1. From the right corner click on **select Kernal** and on the Choose a Kernel source pop-up, select available **Python 3.10.0** env. This will set the Python Environment.

   ![](media/python310.png)

1. **Execute the notebook cell by cell** (using either Ctrl + Enter to stay on the same cell or Shift + Enter to advance to the next cell) and observe the **results of each cell** execution.
  
   > **Note**: Make sure **Python Environmen** is in a ready State, If not please wait for 15 to 20 seconds.

      ![](media/lc-python-first.png)   

1. In the Visual Studio Code navigate to **intro-to-intelligent-apps-main\labs\03-orchestration\04-ACS** folder and select **acs-sk-csharp.ipynb**.

   ![](media/sk-cshart.png)

1. From the right corner click on **select Kernal** and on the Choose a Kernel source pop-up, select available **Select Another Kernal**. As we required .Net Kernal to perform  the exercise. 

   ![](media/SemanticKernel-kernel.png)

1. Select **.Net Interactive** as a kernel

   ![](media/net-kernal.png)

1. In the Visual Studio Code navigate to **.env**, update the **AZURE_COGNITIVE_SEARCH_INDEX_NAME** with **cognitive-search-sk-csharp-index**,  and save the file by pressing **ctrl + s** .

      ![](media/sk-csharp-index.png) 

1. Navigate back to **acs-sk-csharp.ipynb** file, **execute the notebook cell by cell** (using either Ctrl + Enter to stay on the same cell or Shift + Enter to advance to the next cell), and observe the **results of each cell** execution. 

   > **Note**: Make sure **.Net Interactive** is in ready State, If not please wait for 15 to 20 seconds.

      ![](media/acs-sk-csharp-first-cell.png) 

1. In the Visual Studio Code navigate to **intro-to-intelligent-apps-main\labs\03-orchestration\04-ACS** folder and select **acs-sk-python.ipynb**.

   ![](media/sk-python.png)

1. From the right corner click on **select Kernal** and on the Choose a Kernel source pop-up, select available **Python 3.10.0** env. This will set the Python Environment.

   ![](media/python-kennla-new.png)

1. In the Visual Studio Code navigate to **.env**, update the **AZURE_COGNITIVE_SEARCH_INDEX_NAME** with **cognitive-search-sk-python-index**, and save the file by pressing **ctrl + s**.

      ![](media/sk-index.png) 

1. Navigate back to **acs-sk-python.ipynb** file, **Execute the notebook cell by cell** (using either Ctrl + Enter to stay on the same cell or Shift + Enter to advance to the next cell) and observe the **results of each cell** execution.
  
   > **Note**: Make sure **Python Environmen** is in a ready State, If not please wait for 15 to 20 seconds.

      ![](media/sk-python-first.png)  

## Review

In this lab, you have accomplished the following:
- Provisioned Azure AI services and deployed models for knowledge mining.
- Effectively configured AI orchestration, enhancing search experiences with Azure Cognitive Search.

## Proceed to Exercise 9a
