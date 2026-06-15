---
sidebar_position: 1
---

# Getting Started

This page will guide you through making your first time zone conversion with OpenTimezone.

OpenTimezone uses a simple conversion endpoint:

```text
https://api.opentimezone.com/convert
```

By sending a `POST` request with a date/time, a source time zone, and a target time zone, you can convert times between supported time zones.

OpenTimezone also provides helper endpoints for listing supported time zones, looking up a specific time zone, and searching time zone abbreviations.

<details>
<summary>Available endpoints</summary>

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/convert` | Convert a date/time from one time zone to another. |
| `GET` | `/timezones` | List all supported time zones. |
| `GET` | `/timezone/{timezoneId}` | Get details for a specific time zone. |
| `GET` | `/timezones/abbreviations` | List known time zone abbreviations. |
| `GET` | `/timezones/abbreviations/search` | Search for time zones by abbreviation. |

</details>

---

## Step 1: Convert UTC to New York time

Below is a minimal example of how to convert a UTC date/time to New York time.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222026-06-15T03%3A02%3A22.1771394%22%2C%22fromTimezone%22%3A%22UTC%22%2C%22toTimezone%22%3A%22America%2FNew_York%22%7D)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'POST' \
  'https://api.opentimezone.com/convert' \
  -H 'Content-Type: application/json' \
  -d '{
    "dateTime": "2026-06-15T03:02:22.1771394",
    "fromTimezone": "UTC",
    "toTimezone": "America/New_York"
  }'
```

</details>

<details>
<summary>Example response</summary>

```json
{
  "dateTime": "2026-06-14T23:02:22.1771394"
}
```

</details>

---

## Step 2: Convert New York time to UTC

You can also convert local time back to UTC.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222026-06-14T23%3A02%3A22.1771971%22%2C%22fromTimezone%22%3A%22America%2FNew_York%22%2C%22toTimezone%22%3A%22UTC%22%7D)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'POST' \
  'https://api.opentimezone.com/convert' \
  -H 'Content-Type: application/json' \
  -d '{
    "dateTime": "2026-06-14T23:02:22.1771971",
    "fromTimezone": "America/New_York",
    "toTimezone": "UTC"
  }'
```

</details>

<details>
<summary>Example response</summary>

```json
{
  "dateTime": "2026-06-15T03:02:22.1771971"
}
```

</details>

---

## Step 3: Convert between two local time zones

OpenTimezone can convert directly between two local time zones.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222026-06-14T23%3A02%3A22.1772092%22%2C%22fromTimezone%22%3A%22America%2FNew_York%22%2C%22toTimezone%22%3A%22Europe%2FLondon%22%7D)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'POST' \
  'https://api.opentimezone.com/convert' \
  -H 'Content-Type: application/json' \
  -d '{
    "dateTime": "2026-06-14T23:02:22.1772092",
    "fromTimezone": "America/New_York",
    "toTimezone": "Europe/London"
  }'
```

</details>

<details>
<summary>Example response</summary>

```json
{
  "dateTime": "2026-06-15T04:02:22.1772092"
}
```

</details>

---

## Step 4: List all supported time zones

Use the `/timezones` endpoint to retrieve the list of supported time zones.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=GET&url=https%3A%2F%2Fapi.opentimezone.com%2Ftimezones)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'GET' \
  'https://api.opentimezone.com/timezones'
```

</details>

<details>
<summary>Example response</summary>

The response contains all supported time zones. This excerpt shows one item from the live API response.

```json
[
  {
    "id": "Europe/London",
    "displayName": "(UTC+00:00) Europe/London",
    "baseOffset": "00:00:00"
  }
]
```

</details>

---

## Step 5: Look up a specific time zone

Use `/timezone/{timezoneId}` to retrieve information about a single time zone.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=GET&url=https%3A%2F%2Fapi.opentimezone.com%2Ftimezone%2FEurope%252FLondon)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'GET' \
  'https://api.opentimezone.com/timezone/Europe%2FLondon'
```

</details>

<details>
<summary>Example response</summary>

```json
{
  "id": "Europe/London",
  "displayName": "(UTC+00:00) Europe/London",
  "baseOffset": "00:00:00"
}
```

</details>

---

## Step 6: Explore time zone abbreviations

OpenTimezone can also return known time zone abbreviations.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=GET&url=https%3A%2F%2Fapi.opentimezone.com%2Ftimezones%2Fabbreviations)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'GET' \
  'https://api.opentimezone.com/timezones/abbreviations'
```

</details>

<details>
<summary>Example response</summary>

The response contains all known abbreviation groups. This excerpt shows the first few entries from the live API response.

```json
{
  "abbreviations": [
    {
      "abbreviation": "SST",
      "utcOffset": "-11:00:00",
      "timezoneIds": [
        "Pacific/Midway",
        "Pacific/Pago_Pago"
      ]
    },
    {
      "abbreviation": "-11",
      "utcOffset": "-11:00:00",
      "timezoneIds": [
        "Pacific/Niue"
      ]
    },
    {
      "abbreviation": "HST",
      "utcOffset": "-10:00:00",
      "timezoneIds": [
        "America/Adak",
        "Pacific/Honolulu"
      ]
    }
  ]
}
```

</details>

---

## Step 7: Search by abbreviation

Use `/timezones/abbreviations/search` to search for time zones by abbreviation.

The `includeNumeric` query parameter controls whether numeric-style abbreviations, such as `-05:00:00`, are included in the result.

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=GET&url=https%3A%2F%2Fapi.opentimezone.com%2Ftimezones%2Fabbreviations%2Fsearch%3Fabbreviation%3DEST%26includeNumeric%3Dtrue)

<details>
<summary>View cURL request</summary>

```bash
curl -X 'GET' \
  'https://api.opentimezone.com/timezones/abbreviations/search?abbreviation=EST&includeNumeric=true'
```

</details>

<details>
<summary>Example response</summary>

```json
{
  "abbreviations": [
    {
      "abbreviation": "EST",
      "utcOffset": "-05:00:00",
      "timezoneIds": [
        "America/Atikokan",
        "America/Cancun",
        "America/Cayman",
        "America/Detroit",
        "America/Grand_Turk",
        "America/Indiana/Indianapolis",
        "America/Indiana/Marengo",
        "America/Indiana/Petersburg",
        "America/Indiana/Vevay",
        "America/Indiana/Vincennes",
        "America/Indiana/Winamac",
        "America/Iqaluit",
        "America/Jamaica",
        "America/Kentucky/Louisville",
        "America/Kentucky/Monticello",
        "America/Nassau",
        "America/New_York",
        "America/Panama",
        "America/Port-au-Prince",
        "America/Toronto"
      ]
    }
  ]
}
```

</details>

---