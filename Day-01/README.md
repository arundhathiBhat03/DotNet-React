# Day 1 – ASP.NET Core Web API Fundamentals

## Goal

Build and understand a small ASP.NET Core Minimal API using .NET 10.

## What You Built

- Created an ASP.NET Core Web API project named `EmployeeAPI`
- Ran the API locally
- Opened the generated OpenAPI document
- Called the `/weatherforecast` endpoint
- Created a custom `/employees` endpoint
- Created an `Employee` model
- Returned a `List<Employee>` as JSON
- Added `.gitignore`
- Committed and pushed the project to GitHub

## Learning Flow

1. Read `Theory.md`
2. Review `Notes.md`
3. Complete `Exercises.md`
4. Answer `InterviewQuestions.md`
5. Check `SetupChecklist.md`
6. Review the code inside `Code/EmployeeAPI`

## Project Structure

```text
Day-01/
├── README.md
├── Theory.md
├── Notes.md
├── Exercises.md
├── InterviewQuestions.md
├── SetupChecklist.md
└── Code/
    └── EmployeeAPI/
        ├── Models/
        │   └── Employee.cs
        ├── Program.cs
        ├── appsettings.json
        └── EmployeeAPI.csproj
```

## Commands Used

```bash
dotnet new webapi -n EmployeeAPI
cd EmployeeAPI
dotnet run
dotnet watch run
```

## API Endpoints

| Method | Route | Purpose |
|---|---|---|
| GET | `/weatherforecast` | Generated example endpoint |
| GET | `/employees` | Returns the employee collection |
| GET | `/openapi/v1.json` | Returns the OpenAPI description |

## Expected Employee Response

```json
[
  {
    "id": 1,
    "name": "Arundhathi",
    "department": "Engineering",
    "email": "arundhathi@example.com",
    "salary": 50000
  }
]
```

## Completion Checklist

- [x] Created the project
- [x] Ran the API
- [x] Tested `/weatherforecast`
- [x] Created `/employees`
- [x] Created the `Employee` model
- [x] Used `List<Employee>`
- [x] Added `.gitignore`
- [x] Committed the changes
- [x] Pushed the changes to GitHub
- [ ] Review the interview questions aloud
- [ ] Complete the exercises without copying
