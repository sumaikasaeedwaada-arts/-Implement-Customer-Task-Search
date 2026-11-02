# -Implement-Customer-Task-Searchhttps://github.com/sumaikasaeedwaada-arts/-Implement-Customer-Task-Search# Task: Implement Customer & Task Search in HisabDo-AI

Act as a senior Python FastAPI developer. Inspect my existing HisabDo-AI repository and implement individual search functionality for customers and tasks using the existing database, backend services, and project architecture.

## 1. Analyze Existing Project
First inspect:
- FastAPI routes and API structure.
- Customer database models and schemas.
- Task database models and schemas.
- Existing search or filtering functionality.
- Authentication and authorization.
- Database relationships and assigned-user information.
- Existing frontend search components, if available.

Reuse existing models, services, and database queries. Do not create duplicate tables or unnecessary files.

## 2. Customer Search Functionality
Implement customer search that allows users to find customer records using:
- Customer name.
- Email address.
- Phone number.
- Company name.
- Other relevant customer fields available in the database.

Requirements:
- Support partial and case-insensitive matching.
- Allow searching using complete or partial customer details.
- Return only authorized customer records.
- Handle empty search queries appropriately.
- Avoid duplicate search results.
- Support pagination if the existing project architecture uses it.

## 3. Task Search Functionality
Implement task search that allows users to find tasks using:
- Task title.
- Task description.
- Assigned user.
- Task status.
- Priority.
- Other relevant fields available in the existing task model.

Requirements:
- Support partial and case-insensitive matching.
- Search task titles and descriptions.
- Allow searching by assigned user where supported.
- Respect business and user permissions.
- Return relevant matching task records.
- Support existing task filters and pagination.

## 4. Separate Search APIs
Implement separate API endpoints following existing FastAPI conventions.

Suggested endpoints:

GET /customers/search?q=ahmed

GET /tasks/search?q=report

Adapt the routes to the current API structure if similar endpoints already exist.

Use Pydantic schemas where appropriate and return consistent JSON responses.

Example customer response:

{
  "success": true,
  "results": [
    {
      "id": 1,
      "name": "Ahmed Khan",
      "email": "ahmed@example.com"
    }
  ],
  "total": 1
}

Example task response:

{
  "success": true,
  "results": [
    {
      "id": 10,
      "title": "Prepare Monthly Report",
      "description": "Prepare the monthly business report",
      "status": "pending",
      "assigned_user": "Ahmed"
    }
  ],
  "total": 1
}

These are illustrative examples. Use the actual database fields and existing response conventions. Never expose sensitive customer information unnecessarily.

## 5. Dynamic Search Results
If a frontend search interface already exists:
- Connect customer search to the customer search API.
- Connect task search to the task search API.
- Display matching records dynamically.
- Update results when the user changes the search query.
- Show a loading indicator during requests.
- Display a clear message when no records match.
- Display useful error messages when searches fail.
- Prevent outdated requests from overwriting newer search results if requests overlap.

If the frontend is not part of the existing project, implement and document the backend APIs without inventing an unrelated frontend architecture.

## 6. Database Query Optimization
- Use efficient database queries.
- Avoid loading all records into memory just to search.
- Use appropriate case-insensitive matching supported by the existing database.
- Add indexes only when justified by query patterns and existing schema.
- Prevent SQL injection by using parameterized queries or ORM query methods.
- Maintain existing database relationships.

## 7. Security and Validation
- Enforce existing authentication and authorization.
- Ensure users cannot search another business's private records.
- Validate query length and parameters.
- Handle empty and invalid search queries.
- Do not expose private information in search responses.
- Use consistent JSON error responses.

## 8. Error Handling
Handle:
- Empty search queries.
- No matching records.
- Database connection errors.
- Invalid query parameters.
- Unauthorized access.
- Unexpected server errors.

Use appropriate HTTP status codes and application logging.

## 9. Automated Testing
Create or update tests covering:

Customer search:
- Search by full customer name.
- Search by partial customer name.
- Search by email.
- Search by phone number.
- Search with no matching records.
- Case-insensitive search.

Task search:
- Search by task title.
- Search by partial description.
- Search by assigned user.
- Search by status and priority where supported.
- Search with no matching records.

General:
- Empty and invalid queries.
- Authorization and business data isolation.
- Correct JSON response structure.
- Pagination where supported.
- Database error handling.
- Existing API compatibility.

Run the tests and report actual results. Do not claim tests passed unless they actually execute successfully.

## 10. Technical Report
Create `CUSTOMER_TASK_SEARCH_REPORT.md` containing:
- Existing project structure.
- Customer and task database models used.
- Implementation details.
- Files created or modified.
- API endpoints and example requests.
- Example responses.
- Query optimization and security measures.
- Tests executed and actual results.
- Remaining issues and limitations.

## 11. Final Verification
- Run available automated tests.
- Verify customer search using actual database records.
- Verify task search using actual database records.
- Confirm that matching results are returned dynamically.
- Verify authorization and data isolation.
- Fix implementation-related errors.
- Provide commands to run the application and tests.
- Capture successful API test screenshots if supported.
- Clearly report any incomplete functionality.

## Important Rules
- Inspect the existing repository before modifying code.
- Reuse the existing database and architecture.
- Do not create fake customer or task records as real results.
- Do not hardcode customer data.
- Do not break existing functionality.
- Do not fabricate test results.
- Implement the actual working feature, not just sample code.

## Expected Deliverable
A working Customer & Task Search feature that allows users to search customers by name and relevant details, search tasks by title, description, and assigned user, and dynamically display authorized matching records.

Start by inspecting the repository, implement both search functionalities, run the tests, and report the actual changes and results.
