# CI/CD Pipeline Documentation

## Overview

This repository uses GitHub Actions for continuous integration and deployment. The pipeline automatically builds, tests, and creates releases for the BlazorTailwind application.

## Workflow: CI/CD Pipeline

**File**: `.github/workflows/ci-cd.yml`

### Triggers

The workflow runs on:
- **Push to main/master**: Builds the project and creates a release
- **Pull requests to main/master**: Builds the project (no release creation)
- **Manual dispatch**: Can be triggered manually from the Actions tab

### Jobs

#### 1. Build Job
- Checks out the code
- Sets up .NET 10.0 SDK
- Restores dependencies
- Builds the project in Release configuration
- Runs tests (continues even if tests fail)
- Publishes the application
- Uploads build artifacts (retained for 7 days)

#### 2. Create Release Job
- Only runs on push to main/master (not on PRs)
- Checks if v1.0.0 tag already exists
- Creates a GitHub release with tag v1.0.0 if it doesn't exist
- Includes release notes with feature descriptions

### Release Information

- **Version**: v1.0.0 (initial release)
- **Automatic Creation**: The release is created automatically when changes are pushed to the main/master branch
- **Idempotent**: The workflow checks if the tag exists before creating it, preventing duplicate releases

### Build Artifacts

Build artifacts are uploaded and available for download for 7 days. These include the compiled and published application ready for deployment.

## How to Use

### For Developers

1. Create a feature branch
2. Make your changes
3. Push your branch and create a PR
4. The build job will run automatically to validate your changes
5. Once approved and merged to main, the release job will create a new release (for v1.0.0 only, on first merge)

### Manual Workflow Trigger

You can manually trigger the workflow:
1. Go to the Actions tab in GitHub
2. Select "CI/CD Pipeline"
3. Click "Run workflow"
4. Select the branch and click "Run workflow"

## Future Enhancements

For future releases beyond v1.0.0, consider:
- Dynamic versioning based on commits or version files
- Semantic versioning automation
- Deployment to hosting platforms
- Integration with package registries
