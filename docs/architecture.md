---
sidebar_position: 6
---

# Architecture

## How Time Zone Conversion Works

OpenTimezone relies on the .NET `TimeZoneInfo` API to perform all time zone calculations.

When a conversion request is received:

1. The API receives a source date/time, source time zone, and destination time zone.
2. OpenTimezone resolves the supplied IANA time zone identifiers using `TimeZoneInfo`.
3. `TimeZoneInfo` applies the correct UTC offset and daylight saving time (DST) rules for the specified date.
4. The converted date/time is returned to the caller.

### Time Zone Data Source

OpenTimezone runs on Linux containers in Azure Container Apps.

On Linux, `.NET`'s `TimeZoneInfo` uses the system time zone database provided by the **IANA Time Zone Database (tzdata)**. This database contains historical and future daylight saving time rules for supported regions around the world.

Typical examples of IANA time zone identifiers include:

- `Europe/London`
- `America/New_York`
- `Australia/Sydney`
- `Asia/Tokyo`

Because OpenTimezone uses the operating system's time zone data, updates to global daylight saving time rules and regional time zone changes can be incorporated by updating the underlying container image and its `tzdata` package.

### Architecture Overview

```
Client Request
      |
      v
+----------------------+
|   OpenTimezone API   |
+----------+-----------+
           |
           v
+----------------------+
| .NET TimeZoneInfo    |
+----------+-----------+
           |
           v
+----------------------+
| Linux tzdata (IANA)  |
+----------------------+
```

This approach ensures that OpenTimezone uses the same authoritative time zone data relied upon by many Linux-based systems and cloud services.

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

