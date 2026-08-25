# CI/CD with GitHub Actions - Complete Interview Preparation Guide (2 Years Experience)

## 1. What is CI/CD?

CI/CD means:

-   Continuous Integration
-   Continuous Delivery
-   Continuous Deployment

CI/CD automates:

-   Code build
-   Testing
-   Validation
-   Deployment

------------------------------------------------------------------------

# 2. Continuous Integration (CI)

Continuous Integration automatically integrates developer code changes
into a shared repository.

Flow:

    Developer
        |
        v
    GitHub Repository
        |
        v
    GitHub Actions
        |
        v
    Build + Test

CI performs:

-   Dependency installation
-   Unit testing
-   Code validation
-   Application build

------------------------------------------------------------------------

# 3. Continuous Delivery

Continuous Delivery prepares code for release.

Flow:

    Code
     |
    Build
     |
    Test
     |
    Package
     |
    Ready for Deployment

Production deployment may require manual approval.

------------------------------------------------------------------------

# 4. Continuous Deployment

Continuous Deployment automatically releases successful changes.

Flow:

    Developer
     |
    Git Push
     |
    GitHub Actions
     |
    Tests Passed
     |
    Production Deployment

------------------------------------------------------------------------

# 5. What is GitHub Actions?

GitHub Actions is a CI/CD automation platform provided by GitHub.

It automates:

-   Build processes
-   Testing
-   Deployment
-   Docker image creation
-   Server deployment

Workflow files are stored in:

    .github/workflows/

------------------------------------------------------------------------

# 6. GitHub Actions Architecture

    GitHub Repository

            |
            |

    Workflow YAML File

            |
            |

    Runner Machine

            |
            |

    Jobs

            |
            |

    Steps

            |
            |

    Commands

------------------------------------------------------------------------

# 7. GitHub Actions Concepts

## Workflow

A workflow is an automated process written in YAML.

Example:

    build.yml
    deploy.yml
    test.yml

## Event

Triggers a workflow.

Examples:

``` yaml
on:
  push:
    branches:
      - main
```

Other triggers:

-   pull_request
-   workflow_dispatch

------------------------------------------------------------------------

## Job

A group of steps executed together.

Example:

    Build Application

    Steps:
    - Checkout code
    - Install dependencies
    - Run tests

------------------------------------------------------------------------

## Step

A single task inside a job.

Example:

``` yaml
steps:
- Checkout Code
- Install Packages
- Run Build
```

------------------------------------------------------------------------

## Runner

Machine where workflows execute.

Examples:

    ubuntu-latest
    windows-latest
    macos-latest

------------------------------------------------------------------------

# 8. Basic GitHub Actions Workflow

Example:

``` yaml
name: Node CI

on:
  push:
    branches:
      - main

jobs:

  build:

    runs-on: ubuntu-latest

    steps:

    - uses: actions/checkout@v4

    - uses: actions/setup-node@v4
      with:
        node-version: 18

    - run: npm install

    - run: npm test

    - run: npm run build
```

------------------------------------------------------------------------

# 9. GitHub Actions for React Application

Flow:

    Developer

     |

    Git Push

     |

    GitHub Actions

     |

    npm install

     |

    npm run build

     |

    Deploy

------------------------------------------------------------------------

# 10. GitHub Actions for Node.js Backend

Steps:

1.  Checkout code
2.  Setup Node.js
3.  Install dependencies
4.  Run tests
5.  Build application

------------------------------------------------------------------------

# 11. GitHub Actions with Docker

Real project flow:

    Developer

     |

    GitHub

     |

    GitHub Actions

     |

    Docker Build

     |

    Docker Image

     |

    Docker Registry

     |

    Server

     |

    Container

------------------------------------------------------------------------

# 12. GitHub Secrets

Never store sensitive information in code.

Examples:

-   Database passwords
-   JWT secrets
-   AWS keys
-   Docker credentials

Store in:

    Repository
     -> Settings
     -> Secrets and Variables
     -> Actions

Access:

``` yaml
${{ secrets.SECRET_NAME }}
```

------------------------------------------------------------------------

# 13. Environment Variables

Example:

``` yaml
env:
  NODE_ENV: production
```

Node.js:

``` javascript
process.env.NODE_ENV
```

------------------------------------------------------------------------

# 14. Deployment Flow

## React Deployment

    GitHub

     |

    GitHub Actions

     |

    npm build

     |

    Upload Files

     |

    Nginx Server

## Node.js Deployment

    GitHub

     |

    Actions

     |

    Build

     |

    SSH Server

     |

    Restart Application

     |

    PM2

------------------------------------------------------------------------

# 15. GitHub Actions with AWS

Architecture:

    Developer

     |

    GitHub

     |

    GitHub Actions

     |

    Docker Image

     |

    AWS ECR

     |

    AWS ECS / EC2

     |

    Application

Common AWS services:

-   EC2
-   ECS
-   ECR
-   S3
-   RDS

------------------------------------------------------------------------

# 16. GitHub Actions Matrix Strategy

Used for testing multiple versions.

Example:

``` yaml
strategy:
 matrix:
  node-version:
    - 16
    - 18
    - 20
```

------------------------------------------------------------------------

# 17. Artifacts

Artifacts store workflow output.

Examples:

-   React build folder
-   Test reports
-   Logs

Actions:

``` yaml
actions/upload-artifact
actions/download-artifact
```

------------------------------------------------------------------------

# 18. Caching

Caching improves workflow speed.

Used for:

-   npm packages
-   Dependencies
-   Docker layers

------------------------------------------------------------------------

# 19. Deployment Strategies

## Blue-Green Deployment

Two environments:

    Blue
    Current Version

    Green
    New Version

------------------------------------------------------------------------

## Rolling Deployment

Updates servers gradually.

------------------------------------------------------------------------

## Canary Deployment

Releases changes to a small user group first.

------------------------------------------------------------------------

# 20. Complete CI/CD Pipeline

    Developer

     |

    Git Push

     |

    GitHub Repository

     |

    GitHub Actions

     |

    Install Dependencies

     |

    Run Tests

     |

    Build Application

     |

    Create Docker Image

     |

    Push Image

     |

    Deploy Server

     |

    Application Live

------------------------------------------------------------------------

# GitHub Actions Interview Questions

## Q1. What is GitHub Actions?

Answer:

GitHub Actions is a CI/CD automation platform used to automate build,
testing, and deployment workflows.

------------------------------------------------------------------------

## Q2. Difference between CI and CD?

CI: - Automatically builds and tests code.

CD: - Automatically delivers or deploys code.

------------------------------------------------------------------------

## Q3. Where are GitHub Actions workflow files stored?

    .github/workflows/

------------------------------------------------------------------------

## Q4. What is a runner?

A runner is the machine where GitHub Actions jobs execute.

------------------------------------------------------------------------

## Q5. How do you store secrets?

Using GitHub Secrets.

------------------------------------------------------------------------

## Q6. How do you deploy Docker using GitHub Actions?

Steps:

1.  Build Docker image.
2.  Push image to registry.
3.  Connect to server.
4.  Pull image.
5.  Restart container.

------------------------------------------------------------------------

## Q7. How do you debug failed workflows?

Check:

-   Workflow logs
-   Secrets
-   Environment variables
-   Dependencies
-   Build errors

------------------------------------------------------------------------

## Q8. GitHub Actions vs Jenkins?

GitHub Actions:

-   Integrated with GitHub
-   YAML based
-   Easy setup

Jenkins:

-   Separate server
-   Plugin based
-   Highly customizable

------------------------------------------------------------------------

# 2 Years Experience Expected Knowledge

You should know:

-   CI/CD concepts
-   GitHub Actions YAML
-   Workflow triggers
-   Jobs and steps
-   Secrets management
-   Docker integration
-   React deployment
-   Node.js deployment
-   AWS basics
-   Debugging pipelines
