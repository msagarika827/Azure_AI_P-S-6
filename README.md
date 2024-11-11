# Creating a Question Answering Solution

This lab demonstrates how to create a Question Answering (QnA) solution using Azure AI Language, where a knowledge base of frequently asked questions (FAQs) can be queried using natural language input. This solution uses Azure AI's Language service to integrate question-answering capabilities that can support users, typically through a bot, by providing answers to common queries.

## Prerequisites

- An Azure account with an active subscription.
- Visual Studio Code with the necessary extensions for C# or Python (depending on your choice).
- Git installed locally (if cloning the repository).

## Lab Steps

### 1. Provision Azure AI Language Resource

1. **Log in to the [Azure portal](https://portal.azure.com)**.
2. **Create a new resource** by searching for "Language service" and selecting **Create**.
3. **Configure the Language service**:
   - Set **Subscription** to your Azure subscription.
   - Choose **Resource Group** or create a new one.
   - Set **Region** to a preferred location.
   - Enter a **Name** for the service.
   - Choose the **Pricing Tier** (preferably F0).
   - Enable **Azure Search** in the same global region.
4. **Review and create** the Language service.
5. After deployment, navigate to the **Keys and Endpoint** section. Note the keys and endpoint, as these will be used later in the app configuration.

### 2. Create a Question Answering Project in Language Studio

1. Open the [Language Studio portal](https://language.cognitive.azure.com/) and log in.
2. Configure the Language Studio project:
   - Select the Azure Directory, Subscription, and Resource name.
   - Set up the **Custom Question Answering** with the following details:
     - **Name**:  
     - **Description**: 
     - **Default Answer**: 
3. **Add Sources**:
   - Add the **Learn FAQ Page** from `https://docs.microsoft.com/en-us/learn/support/faq`.
   - Import **Chit Chat** for friendly conversation responses.
4. **Edit the Knowledge Base**:
   - Add custom question-answer pairs.
   - Include follow-up prompts for additional detail where necessary.

### 3. Train and Test the Knowledge Base

1. **Save** your changes and then use the **Test** button to simulate question inputs:
   - Try questions like "Hello."
   - Test follow-up prompts as needed.

### 4. Deploy the Knowledge Base

1. In the Language Studio, go to **Deploy Knowledge Base** and select **Deploy**.
2. Retrieve the **Prediction URL** for accessing the REST endpoint.

### 5. Configure the Application in Visual Studio Code

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MicrosoftLearning/mslearn-ai-language
   ```
2. Open the repository in **Visual Studio Code**.
3. Install the Azure AI Language SDK in the terminal:
   - For C#: `dotnet add package Azure.AI.Language.QuestionAnswering`
   - For Python: `pip install azure-ai-language-questionanswering`
4. **Edit Configuration**:
   - Update `.env` (Python) or `appsettings.json` (C#) with your endpoint, keys, project name, and deployment details.

### 6. Add Code to Submit Questions

1. Open `Program.cs` (C#) or `qna-app.py` (Python).
2. Import necessary SDKs for connecting to Azure AI Language and submitting questions.
3. Implement code to create a client, submit questions, and display answers.

### 7. Run the Application

1. Run the app in the terminal:
   - For C#: `dotnet run`
   - For Python: `python qna-app.py`
2. Test with different questions, such as "What is a learning path?" and view the responses.
3. Type `quit` to exit.
