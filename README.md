The provided codebase outlines a comprehensive system for managing and executing tasks within tenants, leveraging Django Rest Framework (DRF) for API endpoints, OAuth2 authentication, Celery for task scheduling and execution, and custom models and serializers. Here's an overview of the key components:

### Key Components

1. **Models**:
    - `Tenant`: Represents a tenant with details like name, description, client ID, secret, base URL, and token management.
    - `Operation`: Defines operations that can be performed within tenants.
    - `OperationType`: Categorizes different types of operations.
    - `Task`: Stores task information such as source data, destination data, status, execution time, etc.
    - `TenantOperation`: A bridge between tenants and their specific operation configurations.

2. **Serializers**:
    - Serializers for each model to facilitate JSON serialization for API endpoints (`ConfigSerializer`, `OperationSerializer`, `TaskSerializer`, etc.).

3. **API Views (ViewSet)**:
    - Each model has a corresponding viewset that provides CRUD operations via the API.
    - Permissions are managed using OAuth2 scopes.

4. **Operations**:
    - Contains logic to create and manage tasks, such as creating tasks from request data and handling task lifecycle.
    - `TenantOperation`: A helper class for fetching tenant-specific operation configurations.
    
5. **Tasks (Background Jobs)**:
    - `DeleteTasks` is a Celery task responsible for periodically cleaning up old tasks based on configuration rules.

6. **Permissions**:
    - Uses OAuth2 tokens with specific scopes to control access to API endpoints.

7. **Custom Utilities and Clients**:
    - `ApiClient`: A base class for making HTTP requests using tenant-specific configurations.
    - `TaskApi`: Extends `ApiClient` specifically for task-related operations, handling request-response cycles and updating task status in the database.

### Code Organization

- **Models**: Defined under `omni_pro_oms.models`.
- **Serializers**: Located in `omni_pro_oms.serializers`, each corresponding to a model.
- **Views (API Endpoints)**: In `omni_pro_oms.views`, providing access via RESTful API endpoints.
- **Operations/Task Management**: Found in `omni_pro_oms.operations` and `omni_pro_oms.task`.
- **Permissions**: Defined under `omni_pro_oms.permissions`.

### Key Features

1. **OAuth2 Authentication**:
    - Utilizes OAuth2 tokens with read-write scopes to secure API endpoints.

2. **Task Management**:
    - Supports creating tasks from requests.
    - Manages task lifecycle including updates based on request-response cycles.
    
3. **Background Task Cleaning**:
    - Periodic Celery task for cleaning up old tasks based on configurable rules (e.g., success vs other states, retention periods).

4. **Token Management**:
    - Tenant tokens are managed within the `Tenant` model to ensure proper authentication and authorization.

5. **Custom API Client and Task Handling**:
    - Provides a robust mechanism for handling HTTP requests and responses with custom task management logic.

### Example Usage

To use this system, you would typically:

1. Define tenants, operations, and operation types.
2. Use the provided endpoints to create tasks based on tenant-specific configurations.
3. Configure Celery to periodically run background jobs like `DeleteTasks` for cleanup purposes.

This framework is well-suited for scenarios where multiple tenants need to manage a wide variety of operational tasks with detailed tracking and periodic maintenance.