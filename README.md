# Nextech Coding Challenge
 
<details>
<summary>Hacker News API - Backend Challenge</summary>
===================================

Overview
--------

This project is a .NET 8.0 web API that provides an interface to fetch the newest stories from Hacker News. It acts as a wrapper around the official Hacker News API, providing pagination capabilities and caching to improve performance.

Features
--------

-   Fetch the newest stories from Hacker News with pagination support
-   Memory caching of story IDs to reduce API calls
-   Docker support for containerized deployment
-   Swagger UI for API documentation and testing
-   Comprehensive unit tests

Prerequisites
-------------

-   [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
-   [Docker](https://www.docker.com/products/docker-desktop/) (optional, for containerized deployment)
-   Visual Studio 2022 or Visual Studio Code (optional, for development)

Getting Started
---------------

### Clone the Repository

```
git clone https://your-repository-url/Backend-Challenge.git
cd Backend-Challenge

```

### Build and Run Locally

#### Using .NET CLI

```
# Navigate to the project directory
cd "Backend Challenge"

# Restore dependencies
dotnet restore

# Build the project
dotnet build

# Run the application
dotnet run

```

The API will be available at `http://localhost:5037` by default.

#### Using Visual Studio

1.  Open the solution file `Backend Challenge.sln` in Visual Studio
2.  Press F5 or click the "Start" button to build and run the project


API Documentation
-----------------

Once the application is running, you can access the Swagger UI at:

-   Local Development: `http://localhost:5037/swagger`

### Available Endpoints

#### GET /api/Stories

Fetches a paginated list of newest stories from Hacker News.

**Parameters:**

-   `amount` (int): Number of stories per page
-   `page` (int): Page number (starting from 1)

**Example:**

```
GET /api/Stories?amount=10&page=1

```

Testing
-------

### Running Unit Tests

```
# Navigate to the project directory
cd "Backend Challenge"

# Run the tests
dotnet test

```

### Manual Testing

You can manually test the API using:

1.  **Swagger UI**: Navigate to the Swagger UI endpoint after starting the application
2.  **Curl**:

    ```
    curl -X GET "http://localhost:5037/api/Stories?amount=10&page=1" -H "accept: application/json"

    ```

3.  **Postman or similar API testing tool**

Implementation Details
----------------------

-   The application uses RestSharp to communicate with the Hacker News API
-   Stories are cached for 5 minutes to reduce the load on the Hacker News API
-   Error handling is implemented at multiple levels to ensure a robust application

Troubleshooting
---------------

If you encounter any issues:

1.  Ensure the Hacker News API is accessible (https://hacker-news.firebaseio.com/)
2.  Check application logs for detailed error information
3.  Verify your network connection if running in Docker


</details>
<details>
<summary>Hacker News API - Frontend Challenge</summary>
================================

Overview
--------

This is an Angular-based frontend application that displays the newest stories from Hacker News. The application connects to a backend API to fetch stories, provides pagination functionality, and includes search capabilities.

Features
--------

-   Browse newest Hacker News stories with a clean, card-based UI
-   Paginate through stories with a configurable page size
-   Search functionality to filter stories by keyword
-   Responsive design using Angular Material components
-   Comprehensive unit tests

Prerequisites
-------------

-   [Node.js](https://nodejs.org/) (v16 or later)
-   [Angular CLI](https://angular.io/cli) (`npm install -g @angular/cli`)
-   Backend API running on `http://localhost:5037` (or configured URL)

Project Structure
-----------------

```
frontend-app/
??? src/
?   ??? app/
?   ?   ??? components/
?   ?   ?   ??? search-bar/     # Search input component
?   ?   ?   ??? story-list/     # Story display component
?   ?   ??? models/             # TypeScript interfaces
?   ?   ??? pages/
?   ?   ?   ??? home/           # Main page component
?   ?   ??? services/
?   ?       ??? story-api/      # API service for backend communication
?   ??? assets/                 # Static resources
?   ??? environments/           # Environment configuration
??? package.json                # Dependencies and scripts

```

Getting Started
---------------

### Installation

```
# Clone the repository (if you haven't already)
git clone <repository-url>
cd <repository-name>/frontend-app

# Install dependencies
npm install

```

### Running the Application

```
# Start the development server
ng serve

# Alternatively, to specify a port
ng serve --port 4200

```

The application will be available at `http://localhost:4200` by default.

### Configuration

The application is configured to connect to a backend API at `http://localhost:5037`. If your backend is running at a different URL, you'll need to update the `baseUrl` in `src/app/services/story-api.service.ts`:

```
private baseUrl = 'http://your-backend-url/api';

```

Usage
-----

-   **Browse Stories**: The main page displays the newest stories from Hacker News
-   **Pagination**: Use the paginator at the bottom to navigate between pages
-   **Change Page Size**: Select different page sizes (5, 10, 25, 100) from the paginator
-   **Search**: Enter keywords in the search bar and press Enter or click the search icon
-   **Clear Search**: After searching, a "Clear Search" button appears to return to all stories

Components
----------

### App Component

The root component that serves as the entry point for the application.

### Home Component

The main page component that orchestrates:

-   Story fetching
-   Pagination
-   Search functionality
-   Displaying results

### Search Bar Component

A reusable component that:

-   Provides a Material Design search input
-   Emits search events to the parent component

### Story List Component

Displays the stories as cards with:

-   Title and author information
-   Link to the original story
-   Loading spinner when fetching data

Services
--------

### Story API Service

Handles communication with the backend API:

-   `getNewStories(amount, page)`: Fetches paginated stories
-   `searchStories(query)`: Searches for stories matching the query

Testing
-------

The application includes comprehensive unit tests for all components and services.

```
# Run unit tests
ng test

# Run tests with code coverage report
ng test --code-coverage

```

### Key Test Cases

-   Component creation and initialization
-   API service calls and responses
-   Pagination functionality
-   Search behavior
-   UI state management

Building for Production
-----------------------

```
# Build the application for production
ng build --configuration production

```

The build artifacts will be stored in the `dist/` directory.

Troubleshooting
---------------

### Common Issues

1.  **API Connection Errors**: Ensure the backend API is running and accessible at the configured URL.

2.  **CORS Issues**: If you see CORS errors in the console, ensure the backend API has CORS configured to allow requests from your frontend origin.

3.  **Material Component Errors**: Make sure all Angular Material dependencies are correctly installed and imported.

</details>