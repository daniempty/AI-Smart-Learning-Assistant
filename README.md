# AI Smart Learning Assistant

## Software Requirements, Technology Stack & System Workflow

### 1. Software Requirements

  Software           Requirement
  ------------------ -------------------------------------------
  Operating System   Windows 10/11 (64-bit)
  Docker Desktop     Latest stable version
  WSL 2              Enabled on Windows
  Python             3.11 or higher
  Web Browser        Google Chrome, Microsoft Edge, or Firefox
  Code Editor        Visual Studio Code
  Git                Version control

### 2. Technologies Used

  Technology        Purpose
  ----------------- ---------------------------------------------
  HTML5             Creating web page structure
  CSS3              Designing and styling the interface
  JavaScript        Frontend interactions and API communication
  Python            Backend programming
  FastAPI           Building backend APIs
  Ollama            Running the AI model locally
  Qwen 2.5 (1.5B)   Generating AI responses
  SQLite            Storing user and application data
  Argon2            Secure password hashing
  Docker            Containerizing the application
  Docker Compose    Managing application services
  Git & GitHub      Version control and project management

### 3. System Architecture

The system follows a client-server architecture with a locally hosted AI
model.

**Main Components:**

1.  **Frontend:** Provides the user interface using HTML, CSS, and
    JavaScript.
2.  **Backend:** FastAPI processes user requests and manages application
    logic.
3.  **Database:** SQLite stores user registration details and
    application data.
4.  **AI Engine:** Ollama runs the Qwen 2.5 model locally and generates
    responses.
5.  **Containerization:** Docker packages application services, while
    Docker Compose manages them.

### 4. Complete System Workflow

**Step 1: Application Startup** - User starts the application through
Docker Compose. - Docker starts the FastAPI and Ollama containers. -
Ollama makes the locally available AI model accessible. - FastAPI
connects to the database and AI service.

**Step 2: User Registration** - User opens the application in a web
browser. - User enters registration information. - Frontend sends
information to the FastAPI backend. - Backend validates the
information. - Password is hashed using Argon2. - User information is
stored in SQLite.

**Step 3: User Login** - User enters login credentials. - Frontend sends
credentials to the backend. - Backend verifies the password. - Backend
creates an authentication session. - User gains access to the
application.

**Step 4: User Request Processing** - User selects a learning
function. - User enters a question, topic, or study information. -
JavaScript sends the request to the appropriate FastAPI endpoint. -
Backend validates the request and prepares an AI prompt.

**Step 5: AI Processing** - FastAPI sends the prompt to Ollama. - Ollama
passes the prompt to the Qwen 2.5 model. - The AI model processes the
request. - Generated output is returned to FastAPI.

**Step 6: Response Delivery** - FastAPI receives the AI-generated
response. - Backend sends the response to the frontend. - JavaScript
updates the interface. - User views the generated result.

**Step 7: Logout** - User selects the logout option. - Frontend sends a
logout request. - Backend invalidates the authentication session. - User
returns to the login page.

### 5. System Flow Diagram

``` text
             STUDENT
                |
                v
          WEB BROWSER
                |
                v
       HTML / CSS / JavaScript
                |
                v
          FASTAPI BACKEND
                |
        +-------+-------+
        |               |
        v               v
     SQLITE           OLLAMA
    DATABASE             |
                         v
                    QWEN 2.5
                    AI MODEL
                         |
                         v
                  AI GENERATED
                     RESPONSE
                         |
                         v
                  FASTAPI BACKEND
                         |
                         v
                    FRONTEND
                         |
                         v
                     STUDENT
```

### 6. Docker Architecture

Docker Compose manages two main services:

  Service   Responsibility
  --------- -----------------------------------------
  FastAPI   Runs backend APIs and application logic
  Ollama    Hosts and runs the local AI model

**Persistent Storage:** - SQLite database volume stores application
data. - Ollama volume stores downloaded AI models.

**Internal Communication:** - Frontend communicates with FastAPI through
HTTP API requests. - FastAPI communicates with Ollama through the
internal Docker network. - FastAPI communicates with SQLite for database
operations.

### 7. Overall System Workflow Summary

The student interacts with the application through a web browser. The
frontend communicates with the FastAPI backend, which handles
authentication, database operations, and AI requests.

When an AI response is required, FastAPI communicates with the locally
hosted Qwen 2.5 model through Ollama. The generated response is returned
to the frontend and displayed to the student.

Docker Compose manages the backend and AI services in separate
containers, while persistent volumes retain database information and
downloaded AI models.

------------------------------------------------------------------------

**Document Status:** Proposed System Design --- Implementation and
testing are separate development stages.
