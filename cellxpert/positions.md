## Positions

Get all positions opened between specified dates

[Try it online](http://api.ucapital.com/nunit/page/online.html)


#### Request

GET http://api.ucapital.com/online/integration/cellxpert/positions?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    DateTime From;              // starting from this date
    DateTime To;                // until this date
    int PagingIndex;            // user index to start with in case there are more results
    string Token;               // a validation token
}
```

##### A valid request example

```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 0,
  "Token": ""
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string TrackingId;          // tracking id of this request (for troubleshooting...)
    PositionInfo[] Positions;   // an array of retrieved positions
    int PagingIndex;            // should be used in a consequent request
    int HasMoreData;            //     if there is more data
}

PositionInfo
{
    int UserId;
    string Email;
    int PositionId;
    string Asset;
    string Dir;
    decimal Volume;
    string Result;
    decimal Pnl;
    string CreatedAt;
    string ClosedAt;
}
```

##### Successful response example

```json
{
  "HasMoreData": 1,
  "PagingIndex": 101,
  "Positions": [
    {
      "UserId": 131252,
      "Email": "cdibley@hotmail.com",
      "PositionId": 700383,
      "Asset": "Gold",
      "Dir": "Below",
      "Volume": 70,
      "Result": "Loss",
      "Pnl": -66.5,
      "OpenedAt": "2014-04-21 12:59:25",
      "ClosedAt": "2014-04-21 13:09:26"
    },
    ...
  ]
}
```

##### Successful response example with consequent request for remaining data

```json
{
  "PagingIndex": 101,
  "HasMoreData": 1
  "Positions": [
    ...
}
```


```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 101,
  "Token": ""
}
```


#### Access restrictions

- Each request may retrieve up to one hundred items
- White IP list


#### Expectations

None
