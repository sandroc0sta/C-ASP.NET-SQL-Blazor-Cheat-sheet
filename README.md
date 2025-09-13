Cheat Sheet (C#, ASP.NET, SQL, Blazor)

---

## 🔹 C# Essentials

* **LINQ**

  ```csharp
  var nums = new List<int>{1,2,3,4,5};
  var evens = nums.Where(n => n % 2 == 0).ToList();
  ```

  * `.Where()`, `.Select()`, `.OrderBy()`, `.FirstOrDefault()`

* **Classes & Objects**

  ```csharp
  class Student { public string Name {get;set;} }
  var s = new Student { Name="Ana" };
  ```

---

## 🔹 ASP.NET Core Basics

* **Minimal API**

  ```csharp
  var app = WebApplication.Create(args);

  app.MapGet("/hello", () => "Hello World");
  app.MapPost("/todo", (Todo t) => { /* add todo */ });

  app.Run();
  ```

* **Controller Example**

  ```csharp
  [ApiController]
  [Route("api/[controller]")]
  public class ProductsController : ControllerBase {
      [HttpGet] public IEnumerable<string> Get() => new[] { "P1", "P2" };
  }
  ```

* **Dependency Injection (DI)**

  * Instead of creating objects inside a class, inject them via constructor.

  ```csharp
  builder.Services.AddScoped<IRepo, Repo>();
  ```

---

## 🔹 SQL Refresher

* **Basic Queries**

  ```sql
  SELECT * FROM Customers;
  INSERT INTO Customers(Name) VALUES ('Ana');
  UPDATE Customers SET Name='Maria' WHERE Id=1;
  DELETE FROM Customers WHERE Id=1;
  ```

* **Foreign Key Example**

  ```sql
  CREATE TABLE Customers(
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(50)
  );

  CREATE TABLE Orders(
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
  );
  ```

---

## 🔹 Blazor Basics

* **Component Example (`.razor`)**

  ```razor
  <h3>Counter</h3>
  <p>Count: @count</p>
  <button @onclick="Increment">Click</button>

  @code {
      int count = 0;
      void Increment() => count++;
  }
  ```

* **Hosting Models**

  * **Blazor Server**: Runs on server, UI updates via SignalR (fast start).
  * **Blazor WebAssembly (WASM)**: Runs in browser via WebAssembly (offline capable).

---

## 🔹 General Concepts

* **HTTP verbs**: GET (read), POST (create), PUT (update), DELETE (remove).
* **REST API**: Resources exposed via URLs, stateless, JSON data exchange.
* **MVC Pattern**:

  * Model = data,
  * View = UI,
  * Controller = logic/request handling.
