## Update affiliate's details

Update affiliate details

#### Request

GET http://api.ucapital.com/online/integration/cellxpert/update/affiliate


where `JSON_DATA` is like

```C#
{
    int AffProgramId;
    int AffiliateId;
    string UserName;
    string Email;
    string FirstName;
    string LastName;
    string CountryCode;
    string WebSite;
    AffiliateStatusId StatusId;
}

enum AffiliateStatusId
{
    Active = 1
}
```

##### A valid request example

```json
{
    ...
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    int CreatedCount;
    int UpdatedCount;
    int FailedCount;
}
```

##### Response example

```json
{
    ...
}
```


#### Access restrictions

- White IP list


#### Expectations

None
