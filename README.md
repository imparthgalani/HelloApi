# Minimal ASP.NET Core API Example

This project demonstrates a **minimal ASP.NET Core API** with a simple `/hello` endpoint, Swagger/OpenAPI integration, and root redirection to Swagger UI.

---

## 🚀 Features

* ASP.NET Core **Minimal API** style configuration
* `/hello` endpoint returning a JSON message
* **Swagger/OpenAPI** for API documentation
* Root (`/`) redirects to **Swagger UI**
* Runs locally with **HTTPS** enabled

---

## 📂 Project Structure

```
.
├── Program.cs        # Application entry point
├── Controllers
│   └── HelloController.cs   # Hello endpoint controller
├── Properties
│   └── launchSettings.json  # Debug/run settings
└── README.md         # Project documentation
```

---

## 🛠️ Prerequisites

Make sure you have the following installed:

* [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
* An IDE such as [Visual Studio](https://visualstudio.microsoft.com/) or [Visual Studio Code](https://code.visualstudio.com/)

---

## 📦 Setup & Run

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/minimal-aspnetcore-api.git
   cd minimal-aspnetcore-api
   ```

2. **Restore dependencies**

   ```bash
   dotnet restore
   ```

3. **Run the application**

   ```bash
   dotnet run
   ```

4. **Access the API locally**

   * Swagger UI: [https://localhost:5001/swagger](https://localhost:5001/swagger)
   * Hello Endpoint: [https://localhost:5001/hello](https://localhost:5001/hello)

---

## 📜 Code Overview

### `Program.cs`

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllers();
builder.Services.AddOpenApi();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();
app.UseAuthorization();

// Map controllers
app.MapControllers();

// Redirect root to Swagger UI
app.MapGet("/", () => Results.Redirect("/swagger"));

app.Run();
```

### `HelloController.cs`

```csharp
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("[controller]")]
public class HelloController : ControllerBase
{
    [HttpGet]
    public IActionResult GetHello()
    {
        return Ok(new { message = "Hello, ASP.NET Core Minimal API!" });
    }
}
```

---

## 📖 Example Response

### Request:

```http
GET /hello
```

### Response:

```json
{
  "message": "Hello, ASP.NET Core Minimal API!"
}
```

---

## 🔧 Customization

* Modify `HelloController.cs` to add more endpoints
* Update Swagger configuration in `Program.cs` for custom docs
* Add authentication/authorization if required

---

## 📜 License

This project is licensed under the **MIT License**. You are free to use, modify, and distribute it.

---

## 👨‍💻 Author
**Parth Patel**  
🔗 [LinkedIn](https://linkedin.com/in/imparthgalani)  
🔗 [GitHub](https://github.com/imparthgalani)


