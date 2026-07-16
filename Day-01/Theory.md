# Day 1 Theory – ASP.NET Core Web API Fundamentals

## 1. What is .NET?

.NET is a development platform created by Microsoft. It provides the runtime, libraries, compilers, and tools needed to build and run applications.

.NET can be used to build:

- Web APIs
- Web applications
- Desktop applications
- Mobile applications
- Cloud services
- Background services

.NET is not a programming language. C# is one of the programming languages commonly used with .NET.

```text
C# source code
      ↓
.NET compiler and SDK
      ↓
.NET application
      ↓
.NET runtime executes it
```

## 2. What is ASP.NET Core?

ASP.NET Core is the web framework in the .NET platform. It is used to build web applications, HTTP services, and Web APIs.

```text
.NET
 └── ASP.NET Core
      ├── Web APIs
      ├── MVC applications
      ├── Razor Pages
      └── Real-time applications
```

ASP.NET Core is cross-platform, so applications can run on macOS, Windows, Linux, containers, and cloud platforms.

## 3. SDK versus Runtime

### .NET SDK

The SDK is used to create, build, test, and publish applications.

Commands such as these are provided by the SDK:

```bash
dotnet new
dotnet build
dotnet run
dotnet test
dotnet publish
```

### .NET Runtime

The runtime executes an already-built .NET application.

A developer generally installs the SDK because the SDK includes the tools needed for development.

## 4. What is a Web API?

A Web API allows applications to communicate using HTTP.

For example:

```text
React application
       ↓ HTTP request
ASP.NET Core API
       ↓
Business logic
       ↓
Database
```

The React application should not connect directly to SQL Server. It sends requests to the API, and the API controls validation, security, business rules, and database access.

## 5. What is REST?

REST is an architectural style commonly used when designing HTTP APIs.

Typical REST operations are:

| HTTP method | Purpose | Example |
|---|---|---|
| GET | Read data | Get all employees |
| POST | Create data | Add an employee |
| PUT | Replace or update data | Update an employee |
| PATCH | Partially update data | Change an employee's email |
| DELETE | Delete data | Delete an employee |

Day 1 used only `GET`.

## 6. What is an endpoint?

An endpoint is an HTTP method combined with a route.

```text
GET /employees
```

- `GET` is the HTTP method.
- `/employees` is the route.
- Together, they identify an API operation.

## 7. What is `localhost`?

`localhost` refers to the computer on which the application is currently running.

```text
http://localhost:5144
```

This means:

- Protocol: `http`
- Host: `localhost`
- Port: `5144`

The application is available only on your machine unless it is deployed or configured for network access.

## 8. What is a port?

A port helps the operating system direct network traffic to the correct application.

```text
MacBook
├── Port 5144 → EmployeeAPI
├── Port 5173 → React/Vite application
└── Port 1433 → Possible SQL Server connection
```

Two applications generally cannot listen on the same IP address and port combination at the same time.

## 9. What happens when `dotnet run` is executed?

```text
dotnet run
    ↓
Restore required packages
    ↓
Compile the C# project
    ↓
Create the application
    ↓
Start the web server
    ↓
Listen for HTTP requests
```

`dotnet run` starts the application but normally requires a manual restart after source-code changes.

`dotnet watch run` watches project files and rebuilds or restarts the application when changes are saved.

## 10. What is `Program.cs`?

`Program.cs` is the starting point of the ASP.NET Core application.

A generated Minimal API may contain:

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddOpenApi();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
}

app.UseHttpsRedirection();

app.Run();
```

### `WebApplication.CreateBuilder(args)`

Creates a builder that prepares application configuration, logging, and dependency injection.

### `builder.Services`

Represents the dependency-injection service collection. Features and application services are registered here.

```csharp
builder.Services.AddOpenApi();
```

This registers services required to generate an OpenAPI document.

### `builder.Build()`

Builds the configured web application.

### `app.MapOpenApi()`

Adds an endpoint that exposes the generated OpenAPI document.

For this project, it was available at:

```text
/openapi/v1.json
```

### `app.Run()`

Starts the application and waits for incoming requests. Endpoint mappings must normally appear before `app.Run()`.

## 11. What is a Minimal API?

A Minimal API defines HTTP endpoints with a small amount of code, usually in `Program.cs`.

Example:

```csharp
app.MapGet("/employees", () =>
{
    return new[] { "Arundhathi", "Alice" };
});
```

`MapGet` means:

> When a GET request is sent to `/employees`, execute this handler and return its result.

Minimal APIs are useful for learning, small services, prototypes, and focused HTTP APIs. ASP.NET Core also supports controller-based APIs, which will be introduced later.

## 12. What does `.WithName()` do?

```csharp
app.MapGet("/weatherforecast", () => ...)
   .WithName("GetWeatherForecast");
```

`.WithName()` assigns a unique name to an endpoint.

The route is still `/weatherforecast`. The endpoint name is metadata that can be used for:

- URL generation
- OpenAPI operation identification
- Testing
- Referring to an endpoint without hardcoding its route

It is optional for a simple endpoint.

The employee endpoint can also be named:

```csharp
app.MapGet("/employees", () => ...)
   .WithName("GetEmployees");
```

## 13. What is OpenAPI?

OpenAPI is a standard, language-independent description of an HTTP API.

The generated JSON can describe:

- Routes
- HTTP methods
- Parameters
- Request bodies
- Response types
- Status codes
- Data schemas

`/openapi/v1.json` describes the API; it does not call the employee endpoint itself.

A browser-based interface such as Swagger UI or Scalar can render the OpenAPI document, but the .NET 10 template does not necessarily include such a UI by default.

## 14. What is JSON?

JSON is a text format used to exchange structured data.

Example:

```json
{
  "id": 1,
  "name": "Arundhathi",
  "department": "Engineering"
}
```

ASP.NET Core automatically serializes returned C# objects into JSON for HTTP responses.

```text
C# Employee object
        ↓ serialization
JSON employee object
```

## 15. What is a class?

A class defines the structure and behavior of a type.

```csharp
public class Employee
{
    public int Id { get; set; }

    public string Name { get; set; } = string.Empty;

    public string Department { get; set; } = string.Empty;

    public string Email { get; set; } = string.Empty;

    public decimal Salary { get; set; }
}
```

The class is a blueprint. It defines which properties an employee has.

## 16. What is an object?

An object is an instance created from a class.

```csharp
var employee = new Employee
{
    Id = 1,
    Name = "Arundhathi",
    Department = "Engineering",
    Email = "arundhathi@example.com",
    Salary = 50000
};
```

- `Employee` is the class.
- `employee` is the variable.
- `new Employee { ... }` creates an object.
- The object is an instance of `Employee`.

## 17. Properties and `get; set;`

```csharp
public string Name { get; set; } = string.Empty;
```

- `public` allows other parts of the application to access the property.
- `string` is the property's type.
- `Name` is the property name.
- `get` reads the value.
- `set` changes the value.
- `string.Empty` supplies a safe initial value.

## 18. Why use `decimal` for salary?

`decimal` is commonly preferred for money because it represents decimal values with high precision.

```csharp
public decimal Salary { get; set; }
```

An `int` cannot represent paise or cents:

```text
50000       → possible with int
50000.75    → not possible with int
```

Floating-point types such as `double` can introduce binary rounding behavior, so `decimal` is normally safer for financial values.

## 19. What is `List<Employee>`?

```csharp
var employees = new List<Employee>();
```

`List<Employee>` is a strongly typed collection that can store multiple `Employee` objects.

```text
List<Employee>
├── Employee object 1
├── Employee object 2
└── Employee object 3
```

The generic type argument `<Employee>` restricts the list to employee objects.

```csharp
employees.Add(new Employee());
```

Trying to add an unrelated type causes a compile-time error.

## 20. Explicit type versus `var`

These declarations produce variables with the same compile-time type:

```csharp
Employee employee = new Employee();
```

```csharp
var employee = new Employee();
```

With `var`, the compiler infers the variable type from the initializer. `var` does not mean `any`, and the variable does not become dynamically typed.

This is invalid:

```csharp
var employee = new Employee();
employee = "Hello"; // Compile-time error
```

The compiler inferred that `employee` is an `Employee`.

## 21. Anonymous object versus model object

### Anonymous object

```csharp
var employee = new
{
    Id = 1,
    Name = "Arundhathi"
};
```

The compiler creates an unnamed type. This can be convenient for small, temporary data shapes.

### Model object

```csharp
var employee = new Employee
{
    Id = 1,
    Name = "Arundhathi"
};
```

This uses a named, reusable type.

A model is preferable for application data because it provides:

- Reuse
- Strong typing
- Better readability
- Compiler checking
- Easier database mapping
- Better API documentation

## 22. What is `appsettings.json`?

`appsettings.json` stores application configuration.

Later it can contain:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "..."
  },
  "Jwt": {
    "Issuer": "...",
    "Audience": "..."
  }
}
```

Do not commit passwords, production secrets, or private API keys to Git. Development secrets should be stored using an appropriate secret-management mechanism.

## 23. What is the `.csproj` file?

`EmployeeAPI.csproj` is the project file. It defines project-level information such as:

- Target framework
- Nullable reference behavior
- Implicit `using` directives
- Package references

Example:

```xml
<TargetFramework>net10.0</TargetFramework>
```

This project targets .NET 10.

## 24. What are `bin` and `obj`?

These folders contain generated build output and intermediate files.

They should normally not be committed to Git:

```gitignore
bin/
obj/
```

The folders are recreated when the application is restored or built.

## 25. What is `.DS_Store`?

`.DS_Store` is a hidden macOS Finder metadata file. It is unrelated to the application and should not be committed.

```gitignore
.DS_Store
**/.DS_Store
```

## 26. Git repository root

Your repository root is:

```text
~/Development/DotNet-React
```

Git commands can be executed from subfolders, but paths in `git status` may then appear relative to the current folder.

For clearer output, run Git commands from the repository root:

```bash
cd ~/Development/DotNet-React
git status
```

A useful working convention is:

```text
DotNet-React repository root
    → git status, git add, git commit, git push

EmployeeAPI project folder
    → dotnet run, dotnet watch run, dotnet build
```

## Official References

- ASP.NET Core documentation: https://learn.microsoft.com/aspnet/core/
- Minimal API tutorial: https://learn.microsoft.com/aspnet/core/tutorials/min-web-api
- Minimal API reference: https://learn.microsoft.com/aspnet/core/fundamentals/minimal-apis
- OpenAPI support: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/overview
- C# classes: https://learn.microsoft.com/dotnet/csharp/fundamentals/types/classes
- Generic types: https://learn.microsoft.com/dotnet/csharp/fundamentals/types/generics
- Variable declarations and `var`: https://learn.microsoft.com/dotnet/csharp/language-reference/statements/declarations
- .NET configuration: https://learn.microsoft.com/dotnet/core/extensions/configuration
