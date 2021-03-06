# Project Report

## Get Report

* `GET /v1/:subdomain/reports/projects` returns a **Project Report**.

### Required Query String Parameters

Parameter | Description
--- | --- | ---
start_date | Start date in ISO 8601 (`YYYY-MM-DD`).
end_date | End date in ISO 8601 (`YYYY-MM-DD`).

**Example:**

```
https://api.resourceguruapp.com/v1/example-corp/reports/projects?start_date=2013-01-01&end_date=2013-01-07
```

### Project Report Response

```json
{
  "booked": 32640,
  "waiting_list": 0,
  "projects": [
    {
      "name": "Project A",
      "color": "#FFCC00",
      "booked": 0,
      "waiting_list": 0,
      "url": "https://api.resourceguruapp.com/v1/example-corp/projects/1",
      "client": {
        "name": "Client A",
        "url": "https://api.resourceguruapp.com/v1/example-corp/clients/1"
      }
    },
    {
      "name": "Project B",
      "color": "#CCFF00",
      "booked": 4800,
      "waiting_list": 0,
      "url": "https://api.resourceguruapp.com/v1/example-corp/projects/2",
      "client": {
        "name": "Client B",
        "url": "https://api.resourceguruapp.com/v1/example-corp/clients/2"
      }
    }
  ]
}
```

Key | Type | Description
--- | --- | ---
booked | integer | Total time booked in minutes.
waiting_list | integer | Total time on waiting list in minutes.
projects | array | Report breakdown per Project. [(Details)](#projects-key)

#### Projects Key

Key | Type | Description
--- | --- | ---
name | string | Name of this Project.
color | string | Color used to highlight this Project.
booked | integer | Time booked in minutes for this Project.
waiting_list | integer | Time on waiting list in minutes for this Project.
url | string | URL shortcut to view this Project.
client | hash | [Client] this Project belongs to. [(Details)](#client-key)

#### Client Key

*No `client` key will be returned if a Project has no Client.*

Key | Type | Description
--- | --- | ---
name | string | Name of this Client.
url | string | URL shortcut to view this Client.
