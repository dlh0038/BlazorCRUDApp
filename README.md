# BlazorCRUDApp
Blazor WebAssembly App with .Net 6 and EF Core modified to use SQLite for local DB

---
![ExampleScreenshot](/screenshot.PNG)
## steps to setup:

1. Cloned the project from [BlazorCRUDApp](https://github.com/Nabaraj222/BlazorCRUDApp).
2. Removed "ConnectionStrings" from Server/appsettings.json.
3. Modified Server/Program.cs
    ```c#
    // For entity Framework
    builder.Services.AddDbContext<ApplicationDbContext>(options => 
    { 
        //options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection"));
        options.UseSqlite("Data Source = Products.db");
    });
    ```
4. Using Terminal to update Server/BlazorCRUDApp.Server.csproj with:
    - `dotnet add package Microsoft.EntityFrameworkCore`
    - `dotnet add package Microsoft.EntityFrameworkCore.Sqlite`
5. Using Terminal to update Client/BlazorCRUDApp.Client.csproj with:
    - `dotnet add package Microsoft.AspNetCore`
6. Could not use `dotnet ef migrations add init`, so I created a SQLite database with Person table using DB Browser for SQLite
5. Run the Project: `dotnet watch run --project .\Server\`

