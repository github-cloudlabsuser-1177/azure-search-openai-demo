# App Backend

The backend of the application is primarily implemented in the Python file app/backend/app.py. It uses the Quart framework for handling HTTP requests and Azure services for storage and authentication.

# Key Components
Blueprint: The Blueprint object bp is used to group related routes, error handlers, and other functionally related components.

Routes: The application defines several routes for handling different types of requests. Some of the key routes include:

/upload: Handles file uploads.
/delete_uploaded: Handles deletion of uploaded files.
/list_uploaded: Lists uploaded files.
/chat: Handles chat requests.
/auth_setup: Sends MSAL.js settings to the client UI.
/config: Handles configuration requests.
Authentication: The @authenticated decorator is used to ensure that certain routes are only accessible to authenticated users.

File Uploads: The upload function handles file uploads. It uses the Azure Blob Storage service to store the uploaded files.

Configuration: The application uses several configuration variables, such as CONFIG_USER_BLOB_CONTAINER_CLIENT and CONFIG_INGESTER, which are likely defined in an external configuration file or environment variables.

# Infrastructure
The infrastructure for the backend is defined in the Bicep file infra/main.bicep. It specifies the settings for the Azure App Service that hosts the backend, including the runtime version, command line for starting the application, and app settings.

# Running the Backend
The backend can be started using the "Start App" task defined in .vscode/tasks.json. This task runs the appropriate start script for the operating system (either app/start.sh for Unix-based systems or app/start.ps1 for Windows).

# Requirements from app/backend/requirements.txt file
urllib3==2.2.1
    # via requests
uvicorn==0.27.1
    # via -r requirements.in
werkzeug==3.0.1
    # via
    #   flask
    #   quart
wrapt==1.16.0
    # via
    #   deprecated
    #   opentelemetry-instrumentation
    #   opentelemetry-instrumentation-aiohttp-client
    #   opentelemetry-instrumentation-dbapi
    #   opentelemetry-instrumentation-urllib3
wsproto==1.2.0
    # via hypercorn
yarl==1.9.4