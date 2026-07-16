# Day 1 Revision Notes

## Core Definitions

| Term | Meaning |
|---|---|
| .NET | Development platform for building and running applications |
| C# | Programming language commonly used with .NET |
| ASP.NET Core | .NET framework for web applications and APIs |
| API | Interface through which applications communicate |
| Endpoint | HTTP method plus route |
| Route | URL path such as `/employees` |
| JSON | Text format used to exchange structured data |
| Serialization | Conversion of a C# object into JSON |
| Model | Class representing application data |
| Object | Instance created from a class |
| OpenAPI | Standard description of an HTTP API |
| localhost | The current computer |
| Port | Number identifying the application receiving network traffic |

## Request Flow

```text
Browser or React
       ↓
HTTP GET /employees
       ↓
ASP.NET Core endpoint
       ↓
C# List<Employee>
       ↓ serialization
JSON response
```

## Main Commands

```bash
dotnet --version
dotnet new webapi -n EmployeeAPI
dotnet run
dotnet watch run
dotnet build
```

## Git Commands

```bash
git status
git add .
git commit -m "message"
git push
```

## Important C# Syntax

### One employee

```csharp
var employee = new Employee();
```

### Multiple employees

```csharp
var employees = new List<Employee>();
```

### Object initializer

```csharp
var employee = new Employee
{
    Id = 1,
    Name = "Arundhathi"
};
```

### GET endpoint

```csharp
app.MapGet("/employees", () =>
{
    return employees;
});
```

### Named endpoint

```csharp
app.MapGet("/employees", () => employees)
   .WithName("GetEmployees");
```

## Class, Object, and List

```text
Employee                 → class/blueprint
new Employee()           → creates one object
employee                 → variable referencing one object
List<Employee>           → collection of employee objects
```

## `var` Rule

```csharp
Employee employee = new Employee();
var employee = new Employee();
```

Both variables have the type `Employee`.

`var` means compile-time type inference, not “any type.”

## Files

| File/folder | Purpose |
|---|---|
| `Program.cs` | Application startup and Minimal API endpoint mappings |
| `Models/Employee.cs` | Defines the Employee model |
| `appsettings.json` | Application configuration |
| `EmployeeAPI.csproj` | Project settings and package references |
| `Properties/launchSettings.json` | Local launch profiles and development URLs |
| `bin/` | Compiled output |
| `obj/` | Intermediate build files |
| `.gitignore` | Files Git should ignore |

## Day 1 Interview Answer Pattern

When answering an interview question:

1. Give a one-sentence definition.
2. Explain why it is used.
3. Give a small example.
4. Mention one practical consideration.

Example:

> `List<Employee>` is a generic collection that stores multiple Employee objects. It provides type safety because only Employee values can be added. For example, an API can return a `List<Employee>` from a GET endpoint. For read-only API responses, another abstraction may sometimes be more appropriate, but `List<T>` is a simple starting point.
