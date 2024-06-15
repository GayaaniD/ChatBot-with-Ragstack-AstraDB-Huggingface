# Building a Retrieval-Augmented Generation (RAG) Pipeline with RAGStax Astra DB and LangChain
![image](https://github.com/GayaaniD/ChatBot-with-Ragstack-AstraDB-Huggingface/assets/125920863/4cc9180a-a260-4526-81ce-0c4b40f9c106)

This project is about exploring how to construct a Question-Answering (QA) system using RAGStack, a data stack specifically designed for the Retrieval-Augmented Generation (RAG) technique. RAG leverages the strengths of both retrieval models and large language models (LLMs) to deliver improved information retrieval and question answering capabilities.

## Prerequisites
**1. Create an Astra Vector Database :**

  - Sign Up : Head over to the [Astra DB signup page](https://accounts.datastax.com/session-service/v1/login)
  - Complete Signup : Follow the on-screen instructions to create your free Astra DB account.
  - Create Database : Once logged in, navigate to the Astra DB dashboard and Click the “Create Database” button. Here, choose the “Serverless (Vector)” deployment type as we’re working with vector embeddings. Enter a descriptive name, like “datastax_demo”. Select a preferred region (usually choose the one closest to you for optimal performance) and click the “Create Database” button.
  
**2. Create an Astra DB Access Token with Administrator Permissions and API Endpoint :**

  - Database Selection : In the Astra DB dashboard, select the database you created (e.g., “datastax_demo”).
  - Tokens : Navigate to the “Tokens” section.
  - Token Role : Select the “Administrator User” as token role. This grants full access to the database.
  - Create Token : Click the “Generate Token” button which will generate a file with token. In this file , extract the Token which is Astra DB **Access Token with Administrator Permission.**
    ![image](https://github.com/GayaaniD/ChatBot-with-Ragstack-AstraDB-Huggingface/assets/125920863/0959c6bd-90a0-4da5-8d28-79ec6f25b3f4 "Astra DB Access Token with Administrator Permission")
    
  - Get Your Astra DB Endpoint as shown below,
    ![image](https://github.com/GayaaniD/ChatBot-with-Ragstack-AstraDB-Huggingface/assets/125920863/be000efc-cc75-4e45-b98f-e9849ee92b53 "Astra DB Endpoint")
    
  - [Diagram Link](https://www.canva.com/design/DAGHDanafsA/RHTuuMmxIeZcwS9vtpiBxg/view?utm_content=DAGHDanafsA&utm_campaign=designshare&utm_medium=link&utm_source=editor) : This link leads to a visual guide that illustrates the vector database creation process. It also provides the necessary requirements (Astra DB Access Token & Astra DB Endpoint) to seamlessly connect your code with Astra DB

**3. Create an OpenAI API Key :**

  - OpenAI Platform : Go to the [OpenAI platform](https://platform.openai.com/playground/chat)
  - Sign In/Up : If you don’t have an account, create one or log in if you already have one.
  - API Keys : Navigate to the “API Keys” tab under your profile settings. Click the “Create New API Key” button and create a API key.

## Project Flow
1. Data Preparation : Begin by loading a sample dataset containing quotes, authors, and tags. This data will serve as the foundation for our knowledge base. [DATASET](https://huggingface.co/datasets/datastax/philosopher-quotes?source=post_page-----c4bb228cc42d--------------------------------)
2. Embedding and Storage : Next, Create vector embeddings of the quotes using OpenAI’s embedding model. These embeddings will be stored within Astra DB’s vector store, enabling efficient retrieval based on semantic similarity.
3. Building the RAG Pipeline : Construct a RAG pipeline using LangChain, a Python library that streamlines building and deploying NLP models. This pipeline will encompass the following components:
  - Retriever : This component retrieves relevant documents (quotes in our case) from the vector store based on a given question.
  
  - Prompt : This component defines a template incorporating the retrieved context and the user’s question, guiding the LLM towards generating an answer.
  
  - LLM : This component, powered by OpenAI, utilises the provided prompt and its knowledge to formulate a response to the user’s question.

## Overall workflow
To create a Retrieval-Augmented Generation (RAG) pipeline using Astra DB and LangChain, start by installing the necessary libraries with **pip install ragstack-ai datasets**. Configure your environment variables to store your Astra DB endpoint, API token, and OpenAI API key. Set up the embedding model using OpenAIEmbeddings and configure the AstraDB vector store with the collection name, embedding model, API token, and endpoint. Load a sample dataset, such as "philosopher-quotes," using the datasets library and preprocess the data to create LangChain documents. Each document includes metadata like author information and tags. Insert these documents into the vector store to generate embeddings. To build the RAG pipeline, define a retriever for fetching relevant documents, create a prompt template for formatting questions and context, and set up the model to generate answers. Chain these components together, allowing the pipeline to retrieve context-specific documents, format them into a prompt, and generate an accurate response based on the input question.
