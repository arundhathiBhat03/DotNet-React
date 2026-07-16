# Day 1 Interview Questions and Answers

Practice answering each question aloud before reading the suggested answer.

## .NET and ASP.NET Core

### 1. What is .NET?

.NET is a cross-platform development platform that provides a runtime, libraries, compilers, and tools for building and running applications.

### 2. Is .NET a programming language?

No. .NET is a development platform. C#, F#, and Visual Basic are languages that can run on .NET.

### 3. What is ASP.NET Core?

ASP.NET Core is the cross-platform web framework in .NET used to build web applications, APIs, and services.

### 4. What is the difference between the .NET SDK and runtime?

The SDK is used to create, build, test, and publish applications. The runtime is used to execute built applications.

### 5. What does `dotnet new webapi` do?

It creates a new ASP.NET Core Web API project from an installed project template.

### 6. What does `dotnet run` do?

It restores dependencies when needed, builds the project, and starts the application.

### 7. What is the difference between `dotnet run` and `dotnet watch run`?

`dotnet run` starts the application normally and usually requires a manual restart after code changes. `dotnet watch run` monitors project files and rebuilds or restarts the application after changes.

## Web API Fundamentals

### 8. What is an API?

An API is an interface that allows software applications or components to communicate through defined operations and data formats.

### 9. What is a Web API?

A Web API exposes operations over HTTP, allowing clients such as browsers, mobile apps, or React applications to exchange data with a server.

### 10. What is REST?

REST is an architectural style for designing networked applications, commonly using HTTP methods and resource-oriented routes.

### 11. What is an endpoint?

An endpoint is an HTTP method combined with a route, such as `GET /employees`.

### 12. What is the difference between a route and an endpoint?

A route is the URL pattern, such as `/employees`. An endpoint includes the route, HTTP method, handler, and associated metadata.

### 13. What are the main HTTP methods?

- `GET` reads data.
- `POST` creates data.
- `PUT` replaces or updates data.
- `PATCH` partially updates data.
- `DELETE` removes data.

### 14. What is JSON?

JSON is a text-based data-interchange format that represents objects, arrays, strings, numbers, booleans, and null values.

### 15. What is serialization?

Serialization is the conversion of an in-memory object into a transferable format such as JSON.

### 16. Why should a frontend not connect directly to a database?

An API provides a controlled layer for security, authentication, validation, business rules, logging, and database access. Direct database access from a browser would expose credentials and bypass server-side controls.

## ASP.NET Core Minimal APIs

### 17. What is a Minimal API?

A Minimal API is an ASP.NET Core approach for creating HTTP endpoints with minimal setup, commonly using methods such as `MapGet`, `MapPost`, and `MapDelete`.

### 18. What does `app.MapGet()` do?

It maps an HTTP GET request for a route to a handler.

### 19. What does `app.Run()` do?

It starts the web application and blocks while the application listens for requests.

### 20. Why must endpoint mappings appear before `app.Run()`?

The application must configure its routes before it starts processing requests. Code placed after the terminal `app.Run()` call is generally not used for normal startup configuration.

### 21. What does `.WithName()` do?

It assigns a unique name to an endpoint. The name can be used for URL generation, metadata, documentation, and testing.

### 22. Is `.WithName()` required?

No. A basic endpoint works without it, but names become useful as an API grows.

### 23. What is OpenAPI?

OpenAPI is a language-independent specification used to describe HTTP APIs, including paths, operations, parameters, requests, responses, and schemas.

### 24. What do `AddOpenApi()` and `MapOpenApi()` do?

`AddOpenApi()` registers services needed to generate the OpenAPI document. `MapOpenApi()` exposes the generated document through an HTTP endpoint.

### 25. Why was `/swagger` blank or unavailable while `/openapi/v1.json` worked?

The project generated an OpenAPI document but did not include an interactive Swagger UI by default. Document generation and a visual documentation interface are separate features.

## C# Fundamentals

### 26. What is a class?

A class is a named type that defines the data and behavior of objects created from it.

### 27. What is an object?

An object is an instance of a class created at runtime.

### 28. What is the purpose of the `Employee` class?

It defines the structure of employee data, including properties such as ID, name, department, email, and salary.

### 29. What is a model?

A model is a class used to represent application or domain data.

### 30. What does `new Employee()` do?

It creates a new instance of the `Employee` class.

### 31. What does `List<Employee>` mean?

It is a generic collection designed to store multiple `Employee` objects with compile-time type safety.

### 32. What is a generic type?

A generic type accepts one or more type parameters. In `List<Employee>`, `Employee` is the type argument that tells the list which kind of value it stores.

### 33. What is the difference between a class and an object?

A class is the definition or blueprint. An object is a concrete instance created from that class.

### 34. What is the difference between `Employee employee` and `var employee`?

With `Employee employee`, the type is written explicitly. With `var employee`, the compiler infers `Employee` from the initializer. Both variables are statically typed as `Employee`.

### 35. Does `var` mean the variable can hold any type?

No. `var` performs compile-time type inference. After the type is inferred, the variable remains strongly and statically typed.

### 36. What is an anonymous object?

An anonymous object is an object whose type is generated by the compiler and has no explicit class name in source code.

```csharp
var employee = new { Id = 1, Name = "Arundhathi" };
```

### 37. Why use an `Employee` model instead of anonymous objects?

A named model is reusable, maintainable, strongly typed, easier to document, and suitable for database mapping and API contracts.

### 38. What do `get` and `set` mean in a property?

`get` returns the property's value, and `set` assigns a new value.

### 39. Why initialize strings with `string.Empty`?

It supplies a non-null initial value and helps satisfy nullable reference-type analysis for required text properties in this beginner model.

### 40. Why use `decimal` for salary?

`decimal` is designed for high-precision decimal arithmetic and is generally preferred for monetary values.

## Application Files and Git

### 41. What is the purpose of `Program.cs`?

It is the application entry point where services, middleware, and Minimal API routes are configured.

### 42. What is `appsettings.json` used for?

It stores application configuration such as logging settings, connection strings, and application options. Secrets should not be committed there.

### 43. What is a `.csproj` file?

It is the .NET project file that defines the target framework, build settings, and package references.

### 44. What are the `bin` and `obj` folders?

They contain generated build output and intermediate files. They are normally excluded from Git.

### 45. What is `.gitignore`?

It tells Git which untracked files or patterns should not be included in commits.

### 46. What is `.DS_Store`?

It is a hidden macOS Finder metadata file. It is unrelated to source code and should normally be ignored by Git.

### 47. What does `git add .` do?

It stages current changes under the working directory for the next commit, subject to `.gitignore`.

### 48. What does `git commit` do?

It records the staged snapshot in the local Git repository with a message.

### 49. What does `git push` do?

It uploads local commits to the configured remote repository.

### 50. Why run Git commands from the repository root?

Git commands work from subfolders, but running them at the root makes paths and repository-wide changes easier to understand.

# Self-Test

Answer these without referring to the notes:

1. Explain `.NET` versus ASP.NET Core.
2. Explain SDK versus runtime.
3. Explain class versus object.
4. Explain `Employee` versus `List<Employee>`.
5. Explain `var` versus an explicit type.
6. Explain `/openapi/v1.json` versus `/employees`.
7. Explain `dotnet run` versus `dotnet watch run`.
8. Explain why `.DS_Store`, `bin`, and `obj` should be ignored.
