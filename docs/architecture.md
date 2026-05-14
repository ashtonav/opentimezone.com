---
sidebar_position: 6
---

# Architecture

Below is a diagram illustrating how **OpenTimezone** is deployed via a CI/CD pipeline to Azure Container Apps.

---

## Deployment Diagram

```
     +---------------------+
     |  GitHub Repository  |
     +----------+----------+
                |
                | (Push code to main branch)
                v
     +--------------------------------------+
     |    CI/CD Pipeline (GitHub Actions)   |
     |  - .NET build & tests                |
     |  - Docker build                      |
     +-------------+------------------------+
                   | (Push image)
                   v
     +----------------------------------+
     |  Azure Container Registry (ACR)  |
     +----------------------------------+
                   | (Pull image)
                   v
+-----------------------------------------+
|  Azure Container Apps                   |
+-----------------------------------------+
                   |
                   v
        +---------------------------------------+
        |  Publicly Accessible                  |
        |  via api.opentimezone.com             |
        +---------------------------------------+
```

1. **Developers** push code changes or open pull requests on GitHub.
2. **GitHub Actions** (CI/CD service) automatically runs tests and builds a Docker image.
3. The image is **pushed** to **Azure Container Registry (ACR)**.
4. **Azure Container Apps** **pulls** the Docker image from ACR.
5. The container is **deployed** and made publicly available at `api.opentimezone.com`.

---
