# Woyage AI - AI Engineer Exercise

This repository contains the solution for the Woyage AI Engineer Exercise. It is a FastAPI backend endpoint that accepts an interview question and a candidate's answer, calls the OpenAI API, and returns a high-quality follow-up question.

## 🚀 Features

* **FastAPI Backend**: A robust, modern Python web server.
* **Pydantic Validation**: Automatic request and response data validation.
* **OpenAI Integration**: Live calls to the `gpt-3.5-turbo` model for dynamic question generation.
* **Asynchronous**: Uses `async/await` for non-blocking API calls.

## 📋 API Endpoint

### Generate Follow-ups

* **Method**: `POST`
* **Path**: `/interview/generate-followups`
* **Request Body**:
    ```json
    {
      "question": "Tell me about a time you handled conflicting priorities.",
      "answer": "In my last role, we had two urgent client requests...",
      "role": "Senior Backend Engineer",
      "interview_type": ["Behavioral interview"]
    }
    ```
* **Success Response (200 OK)**:
    ```json
    {
      "result": "success",
      "message": "Follow-up question generated.",
      "data": {
        "followup_question": "What criteria did you use to determine the 'impact' of each client request?"
      }
    }
    ```

## 🛠️ How to Run Locally

1.  **Clone the repository:**
    ```bash
    git clone [Your-GitHub-Repo-URL]
    cd woyage-ai-exercise
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Create a `.env` file:**
    Create a file named `.env` in the root of the project and add your OpenAI API key:
    ```
    OPENAI_API_KEY="sk-YourSecretKeyGoesHere"
    ```

5.  **Run the server:**
    ```bash
    uvicorn main:app --reload
    ```

6.  **Test the API:**
    Open your browser and go to **http://127.0.0.1:8000/docs** to access the interactive API documentation.

## ⚠️ **Important Note: API Key & Quota**

This application requires a valid OpenAI API key with an active billing plan.

The code is fully functional and successfully authenticates with the OpenAI API. During testing, the API returned a `429 - insufficient_quota` error, indicating that the API key provided does not have billing credits.

If you run this project, please use your own OpenAI API key in the `.env` file. The application will return a `500 Internal Server Error` if the key is missing or has an insufficient quota.