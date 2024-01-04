# Exercise 6: Use your own data with Azure OpenAI
 
 In this exercise, you will experience the OpenAI model's tailored responses after grounding it in specific datasets, showcasing its adaptability to user-provided information.

## Lab scenario
Contoso aims to leverage Azure OpenAI Service to integrate its proprietary travel data. By grounding the OpenAI models in their specific travel information, Contoso intends to provide personalized and detailed responses to customer queries about travel destinations, accommodations, and local attractions. The goal is to create a more tailored and engaging customer experience by combining the power of OpenAI 

## Lab objectives
In this lab, you will complete the following tasks:

- Observe normal chat behavior without adding your own data
- Connect your data in the chat playground
- Chat with a model grounded in your data

## Architecture Diagram

  ![](media/lab-06-ad.png "Architecture Diagram")

## Estimated time: 20 minutes

### Task 1: Observe normal chat behavior without adding your own data

Before connecting Azure OpenAI to your data, first observe how the base model responds to queries without any grounding data.

1. Navigate to the **Chat** playground, and make sure the `gpt-35-turbo-16k` model you deployed is selected in the **Configuration** pane (this should be the default, if you only have one deployed model).

1. In the Chat session enter the following prompts, and observe the output.

    ```
    I'd like to take a trip to New York. Where should I stay?
    ```
    ```
    What are some facts about New York?
    ```
    
1. Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London, or San Francisco. You'll likely get complete responses about areas or neighborhoods, and some general facts about the city.


### Task 2: Connect your data in the chat playground

Next, add your data in the chat playground to see how it responds with your data as grounding

1. Copy this link and paste it into a browser window in the Lab VM [Download the data](https://aka.ms/own-data-brochures). Extract the PDFs in the `.zip` provided.
1. Navigate to the **Chat** playground, and select *Add your data* in the Assistant setup pane.

   ![](media/image243.png "Create storage account")

1. Select **+ Add a data source** and choose *Upload files* from the dropdown.

1. Under **Select Azure Blob Storage Resource** select **storage<inject key="Deployment ID" enableCopy="false"></inject>** from the dropdown menu.

   >**Note:** If you encounter an access permission error, click on **Turn on CORS**
   
   ![](media/cors.png "Create storage account")

1. Select **Create a new Azure AI Search resource** with the following settings. Anything not specified leave as the default.

    - **Subscription**: Default - Pre-assigned subscription (1)
    - **Resource group**: OpenAI (2)
    - **Service name**: **cognitive-search-service-<inject key="Deployment ID" enableCopy="false"></inject>** (3)
    - **Location**: Sweden Central (4)
    - **Pricing tier**: Basic (5)

    ![](media/img455.png "Create cognitive search resource")

1. Click on **Review + Create** and subsequently click on **Create**. Wait until your search resource has been deployed, then switch back to the Azure AI Studio and refresh the page.
1. Under the **Select Azure AI Search resource** select **cognitive-search-service-<inject key="Deployment ID" enableCopy="false"></inject>**.

1. Specify the following details and hit **Next**
    - Enter the index name: **cognitive-search-index**
    - **Add vector search to this search resource**: unchecked
    - **I acknowledge that connecting to an Azure Cognitive Search account will incur usage to my account**: checked

       ![](media/image456.png "Add data configurations")

1. On the **Upload files** page, select **Browse for a file** and upload the PDFs you downloaded, and then select **Upload files** and 
    **Next**.
      
    ![](media/image312.png "Upload files")

1. On the **Data management** page select the **Keyword** search type from the drop-down, and then select **Next**.
1. On the **Review and finish** page select **Save and close**, which will add your data. This may take a few minutes, during which you need to leave your window open. Once completed, verify if the data source, search resource, and index specified **cognitive-search-index** is present under the **Add your data(preview)** tab in **Assistant setup** pane.
   
    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
    > - Navigate to the Lab Validation tab, from the upper right corner in the lab guide section.
    > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
    > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
    > - If you need any assistance, please contact us at labs-support@spektrasystems.com.

### Task 3: Chat with a model grounded in your data

Now that you've added your data, ask the same questions as you did previously, and see how the response differs.

```
I'd like to take a trip to New York. Where should I stay?
```

```
What are some facts about New York?
```

You'll notice a very different response this time, with specifics about certain hotels and a mention of Margie's Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you'll see the same hotels as the model provided.

Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

> **Note**: **Add your data** is still in preview and might not always behave as expected for this feature, such as giving the incorrect reference for a city not included in the grounding data.

## Review

In this lab, you have accomplished the following:
- Explored the default behavior of Azure OpenAI model in the Chat playground.
- Integrated custom data into the model to observe enhanced responses.
- Examined the model's adaptability and tailored outputs showcasing personalized responses.

## Proceed to Exercise 7
