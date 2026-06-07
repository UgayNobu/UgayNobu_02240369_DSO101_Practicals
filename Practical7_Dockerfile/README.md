# Practical 8: GitHub Actions and Render - Self Study

**Name:** UgayNobu  
**Student ID:** 02240369  
**Course:** DSO101  

---

## Objective

The objective of this self-study practical was to understand how GitHub Actions can be used for CI/CD and how Render can be used to deploy an application automatically.

---

## Step 1: Create the GitHub Actions Workflow

A workflow file was created inside `.github/workflows/` in the repository. The workflow is triggered automatically on every push to the `main` branch.

```bash
mkdir -p .github/workflows
```

```yaml
name: Deploy to Render

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Run Build Step
        run: echo "Build step completed successfully"
```

The workflow file was committed and pushed to GitHub:

```bash
git add .
git commit -m "Add GitHub Actions workflow"
git push
```

![GitHub Actions workflow pushed to repository](images/Screenshot_2026-06-08_at_1_17_54_AM.png)

---

## Step 2: Verify GitHub Actions Workflow Ran Successfully

After pushing, GitHub Actions automatically triggered the workflow. The Actions tab showed the workflow completed with **Status: Success** in 10 seconds.

![GitHub Actions workflow completed successfully](images/Screenshot_2026-06-08_at_1_18_36_AM.png)

---

## Step 3: Connect Project to Render

The GitHub repository was connected to Render. Render was configured to automatically redeploy the service whenever a new commit is pushed to the `main` branch via Auto-Deploy.

Common Render settings used:

```text
Service Type: Web Service
Branch: main
Runtime: Docker / Image
Auto-Deploy: Enabled
```

The Render service events page shows a full history of automatic deployments triggered by GitHub commits.

![Render service showing automatic deployment history](images/Screenshot_2026-06-08_at_1_23_10_AM.png)

---

## Step 4: Verify Deployment on Render Dashboard

The Render dashboard shows all active services with their deployment status. All services show **Deployed** confirming successful automatic deployments connected to GitHub.

![Render dashboard showing all active deployed services](images/Screenshot_2026-06-08_at_1_24_48_AM.png)

---

## Results

| Step | Description | Status |
|------|-------------|--------|
| Step 1 | Created `.github/workflows/deploy.yml` and pushed to GitHub | ✅ |
| Step 2 | GitHub Actions workflow ran and completed successfully | ✅ |
| Step 3 | Connected GitHub repository to Render with Auto-Deploy | ✅ |
| Step 4 | Render dashboard shows all services actively deployed | ✅ |

---

## Reflection

This self-study practical helped me understand how CI/CD pipelines work in practice. GitHub Actions automates build and test steps whenever code is pushed to the repository, while Render listens for those changes and automatically redeploys the latest version of the application. This eliminates the need for manual deployment and reduces the chance of human error. I also learned that the workflow file in `.github/workflows/` is the key configuration that defines what happens on each push — from checking out the code to running build commands. Together, GitHub Actions and Render create a seamless and automated software delivery pipeline.

---

## Overall Conclusion

Through these DSO101 practicals, I learned the foundations of Linux, Docker, Jenkins, data persistence, Dockerfiles, Docker Hub, GitHub Actions, and Render deployment. These tools are important in DevOps and CI/CD because they help developers build, test, package, and deploy applications in a consistent and automated way. The practicals also helped me understand how containers work, how applications can be deployed using cloud platforms, and how automation improves the software development workflow.

---

## References

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Render Documentation](https://render.com/docs)
- [GitHub Actions Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)