## 1. What is Jenkins, and why is it widely used in CI/CD?

- Jenkins is an open-source automation server for building, testing, and deploying software.
It allows teams to automate pipelines, integrate with various tools, and deliver software reliably.

---
## 2. What is a Jenkins controller (master) and agent (slave)?

- Controller manages jobs, scheduling, and orchestration.
- Agents execute jobs on different environments or OS, enabling scalable and distributed CI/CD.
---
## 3-. How does Jenkins handle scalability?

- Using multiple agents, node labels, and cloud integrations (Kubernetes, AWS).
- This ensures parallel builds and avoids overloading a single controller.
---
## 4. What is Pipeline as Code, and why is it important?

- Pipeline as Code stores the CI/CD workflow in a Jenkinsfile, under version control.
It improves traceability, collaboration, and repeatable pipelines.
---
## 5. Difference between Freestyle and Pipeline jobs?

- Freestyle jobs are simple but hard to maintain, lack version control.
- Pipeline jobs are code-driven, reusable, and support complex workflows.
---
## 6. Why prefer Declarative pipelines over Scripted pipelines?

- Declarative pipelines are structured, readable, and enforce standards, making them maintainable.
- Scripted pipelines offer flexibility but can lead to complex and unmaintainable code.
---
## 7. What are stages and steps in a pipeline?

- Stages group logical tasks (Build, Test, Deploy), while steps are individual commands executed inside a stage.
---
## 8. What is the purpose of post blocks in Declarative pipelines?

- post blocks allow actions after pipeline execution such as notifications, cleanup, or error handling.
---
##  9. How do you run stages conditionally?

- Conditional stages are used to control pipeline flow so that specific steps run only for certain branches, environments, or conditions.

```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to Production'
            }
        }
    }
}
```
---
## 10. How do you run stages in parallel?

- Using the parallel block.
- Parallel stages reduce total pipeline execution time.
- Jenkins parallel jobs are used when multiple independent tasks like test suites, deployments, or scans can run simultaneously to reduce pipeline execution time.

```
stage('Deploy to Environments') {
    parallel {
        stage('Deploy to Dev') {
            steps {
                echo 'Deploying to Dev'
            }
        }

        stage('Deploy to QA') {
            steps {
                echo 'Deploying to QA'
            }
        }
    }
}
```
---
## 11. How do you handle failures in Jenkins Declarative pipelines, and what is the difference between catchError and try-catch? Give an example.

- catchError should be used only for selected stages, not for all stages.
- You use it only when a failure is acceptable and the pipeline must continue.

- try-catch – Use inside script {} for custom failure handling, such as rollback or notifications, usually for critical stages.

- Post blocks (post { failure } / always) – Run cleanup, notifications, or logging after stages complete.
```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'exit 0' // Simulate success
            }
        }

        stage('Unit Tests') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    echo 'Running unit tests...'
                    sh 'exit 1' // Simulate failure
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    try {
                        echo 'Deploying to dev environment...'
                        sh 'kubectl apply -f deployment.yaml'
                        sh 'exit 1' // Simulate deployment failure
                    } catch (err) {
                        echo "Deployment failed: ${err}"
                        sh 'kubectl rollback deployment my-app'
                    }
                }
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Cleaning resources...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
        failure {
            echo 'Pipeline marked as FAILED'
        }
    }
}

```
---


## 12. What is the agent in Declarative pipelines?

- Defines where the pipeline or stage will run: node, Docker container, or Kubernetes pod.
---
## 13. How to timeout a pipeline stage?

- Using timeout { time: 10, unit: 'MINUTES' }.
- Prevents long-running or stuck builds from consuming resources.
---

## 14. What are Jenkins Shared Libraries?

- Shared Libraries store reusable pipeline code (Groovy functions or classes) in Git.
- They standardize and centralize logic across multiple pipelines.
- By moving common steps, validations, and deployments into reusable methods.
- This reduces duplication and improves team-wide consistency.
---
## 15. Structure of a shared library?

- vars/ → reusable simple steps

- src/ → Groovy classes with complex logic

- resources/ → static files (YAML, scripts)
---
## 16. Difference between vars and src in shared libraries?

- vars contains simple reusable scripts callable directly in Jenkinsfile.
- src contains complex Groovy classes for structured business logic.
---
## 17. How to include a shared library in a Jenkinsfile?
- @Library('my-shared-lib') _

- Then call library functions:

- deployApp('dev')
---
## 18. How do you version shared libraries?

- Using Git branches or tags, referenced in Jenkinsfile:

- @Library('my-shared-lib@v1.2') _
---

## 19. How do you trigger pipelines automatically from Git?

- A Jenkins pipeline can be triggered automatically from Git by connecting Jenkins with the Git repository. The two common ways are:

## Using Webhooks (Recommended)
- GitHub, GitLab, or Bitbucket sends a webhook notification to Jenkins whenever code is pushed or a pull request is created. Jenkins immediately starts the pipeline.

## Using SCM Polling
- Jenkins checks the Git repository at regular intervals (for example, every 5 minutes). If it detects code changes, it triggers the pipeline.
---
## 20. How to implement multi-branch pipelines?

- Using Multibranch Pipeline jobs, which automatically create jobs for each branch.
---
## 21. How do you deploy the same pipeline to multiple environments?

- Use different values files or environment parameters, e.g., dev, QA, prod.
---
## 22. How can you reduce Jenkins pipeline execution time?

- You can reduce Jenkins pipeline execution time by:
  - Running independent stages in parallel
  - Using caching for dependencies like Maven, npm, or Docker layers
  - Using lightweight agents (for example, Kubernetes pods instead of heavy static nodes)
---
## 23. How do you debug pipeline failures?

- Check the console logs to see error messages and failed commands
- Use echo (Declarative) or println (Scripted) to print variable values and understand flow
- Isolate the failing stage by running or fixing one stage at a time
- Use Replay to re-run the pipeline with small changes or dry-run options (when supported) to test without full execution
---
## 24. How do you manage long-running pipelines safely?

- Using timeout blocks so the pipeline automatically stops if it runs too long

- Writing restart-safe pipelines, so the job can continue from the last successful stage after a Jenkins restart

- Breaking the pipeline into clear stages and using checkpoints or stage-level retries

- Avoiding long work on the controller and running heavy tasks on agents
---
## 25. How do you handle dynamic agents in Kubernetes?

- Use Kubernetes plugin to dynamically spin pods per job.
- Ensures clean and scalable execution environments.
---
## 26. How to implement approval gates in pipelines?

- Use input step:

- input "Approve deployment to prod?"

- Pauses pipeline until manual approval.
---






























