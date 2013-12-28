HyperLink-for-iOS
=================

HyperLink app for iOS.


API
----

All requests that require security token should return HTTP code `403` if token test failed.

### Login

`POST` to `/login`:

```JSON
{
  "email": "<email>",
  "password": "<password>"
}
```

#### Successfull login

Returns security token. HTTP code: `200`.
```JSON
{
  "token": "<security token>"
}
```

#### Login failed

Return HTTP code `403`.

### Layers list

`GET` from `/layers?token=:security_token`.

#### Response

Layers list. HTTP code: `200`.

```JSON
{
  "layers": [ "Layer1", "Layer2" ... ]
}
```

### Events retrieving

`POST` to `/events?token=:security_token`:

```JSON
{
  "layer": "<layer name>",
  "location": {
    "latitude": <latitude as float>,
    "longitude": <longitude as float>
  }
}
```

#### Response

Should return all related events in the area and all events joined by user. HTTP code: `200`.

```JSON
{
  "events": [
    {
      "_id": "<event ID>",
      "title": "<event title>",
      "description": "<event description>",
      "viewed": true/false,
      "joined": true/false,
      "location": {
        "latitude": <latitude as float>,
        "longitude": <longitude as float>
      }
    }
    ...
  ],
}
```

### Event edit

`POST` to `/events/:ivent_ID?token=:security_token`:

```JSON
{
  "joined": true/false,
  "viewed": true/false
}
```

#### Response

Should return changed event. HTTP code: `200`.

```JSON
{
  "event": {
    "_id": "<event ID>",
    "title": "<event title>",
    "description": "<event description>",
    "viewed": true/false,
    "joined": true/false,
    "location": {
      "latitude": <latitude as float>,
      "longitude": <longitude as float>
    }
  }
}
```
