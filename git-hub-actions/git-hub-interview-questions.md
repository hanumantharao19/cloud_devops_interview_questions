## 1. What is GitHub Actions?
## Answer:
- GitHub Actions is a CI/CD tool that automates workflows like build, test, and deployment directly from GitHub repositories.

## 2. What is a GitHub Actions workflow?
##Answer:
- A workflow is a YAML file that defines automated steps triggered by events like push, pull request, or schedule.

## 3. Where are GitHub Actions workflows stored?
## Answer:
- Workflows are stored in the .github/workflows/ directory of a repository.

## 4. What are events in GitHub Actions?
## Answer:
- Events are actions that trigger workflows, such as push, pull_request, or workflow_dispatch.

## 5. What is a job in GitHub Actions?
## Answer:
- A job is a set of steps that run on the same runner.

## 6. What is a step in GitHub Actions?
## Answer:
- A step is an individual task inside a job, such as running a command or using an action.

## 7. What is a runner in GitHub Actions?
## Answer:
- A runner is a server that executes the workflow jobs. It can be GitHub-hosted or self-hosted.

## 8. What is the difference between GitHub-hosted and self-hosted runners?
## Answer:
- GitHub-hosted runners are managed by GitHub.
- Self-hosted runners are managed by the user for custom environments.

## 9. What are GitHub Actions actions?
## Answer:
- Actions are reusable automation units that perform specific tasks in a workflow.

## 10. How do you define environment variables in GitHub Actions?
## Answer:
- Environment variables can be defined using the env keyword at workflow, job, or step level.

## 11. How are secrets managed in GitHub Actions?
## Answer:
- Secrets are stored securely in GitHub repository or organization secrets and accessed using ${{ secrets.NAME }}.

## 12. What is workflow_dispatch?
## Answer:
- It allows manual triggering of a workflow from the GitHub UI.

## 13. What is matrix strategy in GitHub Actions?
## Answer:
- Matrix strategy allows running the same job with multiple configurations, such as different OS or language versions.

## 14. How can you cache dependencies in GitHub Actions?
## Answer:
- Use the actions/cache action to speed up builds by caching dependencies.

## 15. How do you deploy applications using GitHub Actions?
## Answer:
- By adding deployment steps in the workflow, such as pushing images to registries or deploying to cloud services.

## 16. How can GitHub Actions integrate with Kubernetes?
## Answer:
- It can build Docker images, push them to a registry, and deploy to Kubernetes using kubectl or Helm.

## 17. What is the difference between GitHub Actions and Jenkins?
## Answer:
- GitHub Actions is GitHub-native and event-driven, while Jenkins is self-managed and plugin-based.

## 18. What is concurrency in GitHub Actions?
## Answer:
- Concurrency controls how many workflow runs can execute at the same time and prevents duplicate runs.

## 19. How do you restrict workflow access to environments?
## Answer:
- Use GitHub Environments with required reviewers and environment-specific secrets.

## 20. What are best practices for GitHub Actions?
## Answer:

- Use secrets securely
- Cache dependencies
- Use reusable workflows
- Limit permissions using permissions keyword