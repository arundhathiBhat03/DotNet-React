# Day 1 Exercises

Complete these without copying the existing solution first.

## Exercise 1 – Add an Employee

Add a third employee with:

- A unique ID
- Name
- Department
- Email
- Salary

Run the application and verify that the employee appears in the JSON response.

## Exercise 2 – Add a Property

Add this property to `Employee.cs`:

```csharp
public int ExperienceYears { get; set; }
```

Give every employee a value and verify the JSON response.

## Exercise 3 – Create a Department Endpoint

Create:

```text
GET /departments
```

Return:

```json
[
  "Engineering",
  "Human Resources",
  "Finance"
]
```

Give the endpoint the name `GetDepartments`.

## Exercise 4 – Create One Employee Object

Create one variable:

```csharp
Employee employee = new Employee
{
    Id = 10,
    Name = "Test Employee"
};
```

Then rewrite it using `var`.

Explain why both variables have the same type.

## Exercise 5 – Understand Compile-Time Safety

Try adding a string to a `List<Employee>`:

```csharp
employees.Add("Hello");
```

Observe the compiler error, then remove the invalid line.

Write one sentence explaining why the compiler rejected it.

## Exercise 6 – Change the Route

Temporarily change:

```text
/employees
```

to:

```text
/api/employees
```

Run the API and call the new URL. Restore the original route afterward.

## Exercise 7 – Watch Mode

1. Start the API with `dotnet watch run`.
2. Change an employee name.
3. Save the file.
4. Refresh the browser.
5. Compare this workflow with `dotnet run`.

## Exercise 8 – Explain the OpenAPI Document

Open:

```text
/openapi/v1.json
```

Locate:

- The `/employees` path
- The `get` operation
- The successful response
- The employee schema, if generated

Write two sentences describing what the document represents.

## Exercise 9 – Git Practice

From the repository root:

```bash
git status
```

Change one employee value, then run:

```bash
git diff
```

Restore the original value and run:

```bash
git status
```

## Exercise 10 – Explain the Request Flow

Without looking at the notes, draw this flow:

```text
Browser → Route → Endpoint handler → Employee objects → JSON response
```

Explain each arrow in your own words.

# Optional Challenge

Create:

```text
GET /employees/featured
```

Return one `Employee` object rather than a list.

Questions:

1. How does the JSON shape differ?
2. Which endpoint returns an array?
3. Which endpoint returns a single object?
