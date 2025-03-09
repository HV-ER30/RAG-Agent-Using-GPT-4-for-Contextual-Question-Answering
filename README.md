# RAG-Agent-Using-GPT-4-for-Contextual-Question-Answering
This project implements a Retrieval-Augmented Generation (RAG) agent using GPT-4 to generate factually grounded answers based on retrieved documents. It ensures response accuracy through hallucination detection, relevance grading, and conditional decision-making, refining the search or retrying as needed.

# Features

- **Document Retrieval:** Fetches relevant documents based on the input question.
- **Document Grading:** Evaluates the quality and relevance of the retrieved documents.
- **Hallucination Detection:** Ensures responses are factually supported by documents.
- **Question-Answering Validation:** Verifies whether the generated response directly addresses the question.
- **Workflow Management:** Implements a decision-making process to refine search or retry when necessary.

# Project Structure

The notebook follows a structured approach with multiple steps. Below is a breakdown of each cell and its function:

## 1. Setup and Imports
- Loads necessary libraries such as `openai`, `langchain`, and other required dependencies.
- Initializes API keys and configurations.

## 2. Define Workflow and State Management
- Establishes a `state` dictionary to track the progress of the workflow.
- Sets up helper functions to manage and update workflow states.

## 3. Document Retrieval
- Implements a function to fetch relevant documents from a predefined knowledge base.
- Uses embeddings and similarity search for retrieving contextually relevant information.

## 4. Document Grading
- Grades the retrieved documents based on their relevance and quality.
- Determines whether the retrieved documents are sufficient for generating a response.

## 5. Decision Making: Generate or Web Search
- If retrieved documents are insufficient, initiates a web search.
- If documents are of high quality, proceeds to response generation.

## 6. Response Generation Using GPT-4
- Calls GPT-4 using `rag_chain.invoke()` to generate an answer based on retrieved documents.

## 7. Hallucination Detection
- Uses a hallucination grader to check whether the generated response is grounded in the retrieved documents.

## 8. Question Relevance Evaluation
- Evaluates whether the generated response adequately answers the given question.
- If valid, marks the response as **"useful"**; otherwise, initiates a retry or web search.

## 9. Conditional Workflow Execution
- Implements a decision-based workflow:
  - If the response is grounded and useful, return it as the final output.
  - If the response is not useful, refine the search or retry.
  - If hallucination is detected, restart the process.

## 10. Output the Final Response
- Displays the generated response along with supporting documents.

# Usage

1. Run the notebook step-by-step to initialize and execute the workflow.
2. Input a question, and the system will retrieve relevant documents and generate an answer.
3. If needed, the system will refine its search and retry the process automatically.
4. The final response will be displayed along with a validation status.

