## Funds

Get all fund transactions between specified dates

[Try it online](http://api.ubinary.com/nunit/page/online.html)


#### Request

GET http://api.ucapital.com/online/integration/cellxpert/funds?data=JSON_DATA

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
    FundTransaction[] Users;    // an array of retrieved transactions
    int PagingIndex;            // should be used in a consequent request
    int HasMoreData;            //     if there is more data
}

FundTransaction
{
    int TransactionId;
    int UserId;
    string UserName;
    string UserEmail;
    string UserPhone;
    int AffiliateId;
    int UserGroupId;
    int BusinessUnitId;
    decimal DepositAmount;
    string CompletionTimestamp;
    TransactionType TransactionType;
    string Comment;
}

enum TransactionType
{
    Order, Refund, Bonus
}
```

##### Successful response example

```json
{
  "HasMoreData": 0,
  "PagingIndex": 10,
  "Transactions": [
    {
      "TransactionId": 661344,
      "UserId": 308237,
      "UserName": "talal forayh",
      "UserEmail": "tal_138@hotmail.com",
      "UserPhone": "+966-550-091177",
      "AffiliateId": 0,
      "UserGroupId": 10894,
      "BusinessUnitId": 10454,
      "DepositAmount": 2000,
      "CompletionTimestamp": "2014-04-21 10:05:09",
      "TransactionType": "Order",
      "Comment": "hassan"
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
  "Transactions": [
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
