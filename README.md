# Construction Cost Estimator

A Blazor Server web application for organizing construction projects and estimating their material, labor, and equipment costs. Projects are associated with the signed-in user, and reports summarize project costs.

## Features

- Create an account, sign in, and manage your profile.
- Create and track construction projects.
- Add materials, labor, and equipment costs to projects.
- Review project estimates with tax, overhead, and profit calculations.
- View a dashboard and project cost reports.

The project includes a PDF report-generation service, but the report download action in the interface is not currently enabled.

## Requirements

- .NET SDK 10.0 or later
- No separate database installation is required; the application uses SQLite.

## Run locally

From the directory containing `ConstructionCostEstimator.csproj`, run:

```powershell
dotnet restore
dotnet run
```

The HTTPS launch profile uses `https://localhost:7081` (and `http://localhost:5080`). You can also start the app in Visual Studio or VS Code using the `https` launch profile.

On startup, the application attempts to apply Entity Framework Core migrations. The default SQLite connection string stores the database at `Data/app.db`.

## Account confirmation

Email confirmation is required for sign-in. The default email sender is a no-op, so it does not deliver messages. During local development, after registering, use the confirmation link displayed on the Register Confirmation page. For a deployed environment, configure a real email sender before allowing user registration.

## Technology

- ASP.NET Core 10 and Blazor Server
- Entity Framework Core 10 with SQLite
- ASP.NET Core Identity
- QuestPDF for PDF document generation

## Configuration

The default connection string and logging settings are in `appsettings.json`. Keep credentials and other environment-specific secrets out of source control; use .NET User Secrets for local development secrets and an appropriate secret store for deployment.

## Project layout

- `Components/Pages/` - Blazor pages and application workflows
- `Components/Account/` - Identity and account UI
- `Data/` - EF Core database context and migrations
- `Models/` - Project, estimate, and cost entities
- `Services/` - Project, cost, estimate, report, and PDF services
- `wwwroot/` - Static assets and styles