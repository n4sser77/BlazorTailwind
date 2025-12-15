# BlazorTailwind

Blazor server webapp template preconfigured with Tailwind V4 and Identity for authentication.

## CI/CD Pipeline

This project uses GitHub Actions for continuous integration and deployment. The pipeline:

- Automatically builds the project on push to main/master branch
- Runs tests (if available)
- Creates release artifacts
- Generates version tags for releases

### Build Status

The CI/CD pipeline is configured in `.github/workflows/ci-cd.yml`

## Getting Started

### Prerequisites

- .NET 10.0 SDK or later

### Build

```bash
dotnet build
```

### Run

```bash
dotnet run
```

## Version

Current version: **v1.0.0** 
