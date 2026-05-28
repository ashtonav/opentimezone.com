---
sidebar_position: 3
---

# Self-Hosting

Before you begin, clone or download the [OpenTimezone repository](https://github.com/ashtonav/opentimezone). Afterwards, choose one of the options below to host OpenTimezone.

---
## Option 1: Using Docker (recommended for self-hosting)

### Requirements
- Docker.

### How to Run
1. From the root folder of the project, run the following commands:
   ```bash
   docker build -t opentimezone -f ./src/Timezone.WebApi/Dockerfile .
   docker run -it -p 5280:8080 opentimezone
   ```
2. The API can be accessed at [http://localhost:5280](http://localhost:5280).

## Option 2: Using Visual Studio (recommended for development purposes)

### Requirements
- Visual Studio 2026.
    - With ASP.NET and web development installed from the Visual Studio Installer.
- Docker.
- .NET 10 SDK.

### How to Run
1. Open the solution in Visual Studio 2026.
2. Run it using Docker.
3. The API can be accessed at [https://localhost:5281](https://localhost:5281).

---