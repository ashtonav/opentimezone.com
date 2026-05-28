---
sidebar_position: 1
---

# Getting Started

## 1: Convert time from New York to London.

```bash
 curl -X 'POST' \
    'https://api.opentimezone.com/convert' \
    -H 'Content-Type: application/json' \
    -d '{
    "dateTime": "2024-10-14T00:00:00.000",
    "fromTimezone": "America/New_York",
    "toTimezone": "Europe/London"
    }' 
```

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222024-10-14T00%3A00%3A00.000%22%2C%22fromTimezone%22%3A%22America%2FNew_York%22%2C%22toTimezone%22%3A%22Europe%2FLondon%22%7D)

---

## 2: Convert UTC to New York time.

```bash
curl -X 'POST' \
  'https://api.opentimezone.com/convert' \
  -H 'Content-Type: application/json' \
  -d '{
    "dateTime": "2025-09-17T04:36:48.131338",
    "fromTimezone": "UTC",
    "toTimezone": "America/New_York"
  }'
````

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222025-09-17T04%3A36%3A48.131338%22%2C%22fromTimezone%22%3A%22UTC%22%2C%22toTimezone%22%3A%22America%2FNew_York%22%7D)

---

## 3: Convert New York to UTC time.

```bash
curl -X 'POST' \
  'https://api.opentimezone.com/convert' \
  -H 'Content-Type: application/json' \
  -d '{
    "dateTime": "2025-09-17T00:36:48.131394",
    "fromTimezone": "America/New_York",
    "toTimezone": "UTC"
  }'
```

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=POST&url=https%3A%2F%2Fapi.opentimezone.com%2Fconvert&bodyMode=raw&contentType=application%2Fjson&rawParams=%7B%22dateTime%22%3A%222025-09-17T00%3A36%3A48.131394%22%2C%22fromTimezone%22%3A%22America%2FNew_York%22%2C%22toTimezone%22%3A%22UTC%22%7D)

---

## 4: List all supported time zones.

```bash
curl -X 'GET' 'https://api.opentimezone.com/timezones'
```

[![Try it out](https://img.shields.io/badge/-Try%20it%20out-brightgreen?style=for-the-badge)](https://hoppscotch.io/?method=GET&url=https%3A%2F%2Fapi.opentimezone.com%2Ftimezones)


---