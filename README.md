<img src="https://upload.wikimedia.org/wikipedia/commons/a/a8/Microsoft_Azure_Logo.svg" alt="Azure" width="300" />

# Connect Azure AI Bot Service with Azure Functions

**Project Link:** [Azure AI Migration - BankerBot]

**Author:** N SHAMEER  
**Email:** shameernittur@gmail.com

---

## Connect Azure AI Bot Service with Azure Functions

![Image](https://learn.microsoft.com/en-us/azure/bot-service/media/how-it-works/architecture-diagram.png)

---

## Introducing Today's Project!

### What is Azure AI Bot Service?

Azure AI Bot Service (integrated with Azure AI Language) is a Microsoft service useful for creating and customizing intelligent, enterprise-grade bots that can scale across multiple channels.

### How I used Azure AI Language in this project

In today's project, I migrated my logic to Azure to create a "BankerBot." I used **Conversational Language Understanding (CLU)** to define intents like `CheckBalance` and used **Azure AI Bot Service** to handle the user interface and messaging.

### One thing I didn't expect in this project was...

One thing I didn't expect was how seamless the integration is between **Azure Functions** and the Bot Framework, allowing for complex backend logic with very low latency.

### This project took me...

This project took me above 90 mins to complete the migration and document the Azure-specific resources.

---

## Azure Functions (Serverless Logic)

**Azure Functions** is the serverless compute service that replaces AWS Lambda. It allows us to run event-driven code in the backend without managing infrastructure.

In this project, I created an **HTTP-triggered Azure Function** (Python/Node.js) to generate and return a random bank balance when the bot sends a fulfillment request.


---

## Bot Channels Registration & Deployment Slots

In Azure, we use **Deployment Slots** and **Channels** to manage different versions of the bot, replacing the concept of an AWS Lex Alias.

* **Production Slot:** The live version of the bot.
* **Staging/Test Slot:** Replaces the *TestBotAlias*, allowing me to test the BankerBot's logic before it goes live.

To connect the backend, I configured the **Messaging Endpoint** in the Azure Bot settings to point to my Azure Function URL.

---

## Logic Integration (Webhooks)

In Azure, "Code Hooks" are handled via **Webhooks** or the **Bot Framework SDK** fulfillment logic.

Even though the Bot Service is registered, I configured a webhook within the `CheckBalance` intent's fulfillment logic. This ensures that when the bot identifies the user's intent, it calls the Azure Function to process the data.

---

## The final result!

I've set up my chatbot to trigger an **Azure Function** and return a random dollar figure once the user provides their account type and date of birth for verification. The identity verification is handled by **Azure AI Language** slot filling (Entities).


---

## Customizing the Azure Function with Generative AI

To level up the connection, I integrated **Azure OpenAI (Claude or GPT-4o)** within the Azure Function. Instead of a static response, the AI now generates unique, fun descriptions for the balance.

Now, the message my users see is: *"Hello! Your Savings account balance, tucked away in the Bank of TCS, is currently $217.54. It looks like your savings are growing beautifully!"* I can customize this further by adjusting the **System Prompt** in the Azure OpenAI Studio.

---
