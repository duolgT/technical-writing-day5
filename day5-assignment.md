Exercise A: User Manual Procedure
Creating a GitHub Repository and Making a First Commit
Prerequisites
Before starting, make sure you have:
A computer with an internet connection.
A GitHub account.
Git installed on your computer.
Git Bash, Command Prompt, or another terminal.
A text editor such as Visual Studio Code.
Basic familiarity with creating folders and files on your computer.
Procedure
Step 1: Open GitHub.
Expected result: The GitHub website opens in your web browser.
Step 2: Sign in to your GitHub account.
Expected result: Your GitHub account dashboard appears.
Step 3: Select the "+" button in the upper-right corner of GitHub.
Expected result: A menu containing repository creation options appears.
Step 4: Select "New repository."
Expected result: The "Create a new repository" page appears.
Step 5: Enter a name for the repository.
Expected result: The repository name appears in the repository name field.
Step 6: Enter a short description for the repository.
Expected result: The description appears below the repository name field.
Step 7: Select "Public" as the repository visibility.
Expected result: The Public option is selected.
Step 8: Select "Create repository."
Expected result: GitHub displays the new empty repository page.
Step 9: Open Git Bash.
Expected result: A terminal window opens and displays a command prompt.
Step 10: Create a project folder.
Expected result: A new folder is created for the project files.
Step 11: Open the project folder in the terminal.
Expected result: The terminal is working inside the project folder.
Step 12: Initialize Git in the project folder.
Expected result: Git creates a local repository inside the project folder.
Step 13: Create a project file named README.md.
Expected result: The README.md file appears in the project folder.
Step 14: Add the project files to Git's staging area.
Expected result: Git marks the project files as ready to be committed.
Step 15: Create the first commit.
Expected result: Git records the staged files as the first commit in the local repository.
Step 16: Connect the local repository to the GitHub repository.
Expected result: The local repository has a remote connection to GitHub.
Step 17: Push the commit to GitHub.
Expected result: The committed files appear in the GitHub repository.
Screenshot Description
Include a screenshot of the GitHub repository page after the first push. The screenshot should show the repository name, the README.md file, and the first commit listed in the repository history. This demonstrates that the local project was successfully uploaded to GitHub.
Troubleshooting
Problem: git is not recognized as a command.
This usually means Git is not installed or its installation was not added to the system PATH.
Solution: Install Git, restart the terminal, and run git --version to confirm that Git is available.


Exercise B: API Reference Entry
Create a Task
Endpoint
POST /projects/{projectId}/tasks
Description
Creates a new task inside a specified project. The request must be authenticated, and the task must include a title, assignee, due date, and priority. A description is optional.

Path Parameters
Parameter
Type
Required
Description
projectId
string
Yes
Unique identifier of the project where the task will be created.


Query Parameters
This endpoint does not require any query parameters.

Request Headers
Header
Required
Description
Authorization
Yes
Bearer token used to authenticate the user.
Content-Type
Yes
Must be application/json.

Example:
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json


Request Body
The request body must be a JSON object containing the following fields:
Field
Type
Required
Description
title
string
Yes
The name of the task.
description
string
No
Additional information about the task.
assigneeId
string
Yes
Unique ID of the user assigned to the task.
dueDate
string
Yes
Date when the task is due, using YYYY-MM-DD format.
priority
string
Yes
Task priority. Accepted values are low, medium, or high.

Example Request
POST /projects/proj_1024/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json

{
  "title": "Prepare project documentation",
  "description": "Complete the technical documentation for the new project management feature.",
  "assigneeId": "usr_2048",
  "dueDate": "2026-10-15",
  "priority": "high"
}


Response Codes
Status Code
Meaning
201 Created
The task was successfully created.
400 Bad Request
The request contains invalid JSON or malformed data.
401 Unauthorized
Authentication is missing or the access token is invalid or expired.
403 Forbidden
The authenticated user does not have permission to create a task in the project.
404 Not Found
The specified project or assignee does not exist.
409 Conflict
The request conflicts with an existing task or project state.
422 Unprocessable Entity
The request format is valid, but one or more field values fail validation, such as an invalid priority or date.
429 Too Many Requests
The client has exceeded the API request rate limit.
500 Internal Server Error
An unexpected error occurred on the server.


Successful Response
A successful request returns 201 Created and the newly created task.
Example Successful Response
{
  "id": "task_3056",
  "projectId": "proj_1024",
  "title": "Prepare project documentation",
  "description": "Complete the technical documentation for the new project management feature.",
  "assigneeId": "usr_2048",
  "dueDate": "2026-10-15",
  "priority": "high",
  "status": "todo",
  "createdAt": "2026-09-26T13:45:20Z"
}

Response Field Descriptions
Field
Type
Description
id
string
Unique identifier assigned to the new task.
projectId
string
Identifier of the project containing the task.
title
string
Name of the task.
description
string
Optional task description.
assigneeId
string
ID of the user assigned to the task.
dueDate
string
Task deadline in YYYY-MM-DD format.
priority
string
Task priority: low, medium, or high.
status
string
Current task status. A newly created task starts with todo.
createdAt
string
Date and time when the task was created, using ISO 8601 format.


