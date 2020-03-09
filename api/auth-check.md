# BBO Authentication Check API

BridgeBaseOnline exposes an API to check whether or not a user is currently logged in. 

## Usage

```
POST https://webutil.bridgebase.com/v2/auth_check.php
```

### Authorization

Client needs a valid API key to use this endpoint. API key can be obtained by contacting BBO technical staff.
API key must be submitted as _Bearer_  format through the _Authorization_ HTTP header, i.e.:

```
POST https://webutil.bridgebase.com/v2/auth_check.php
Authorization: Bearer client_api_key
```

### Required input parameters:

| Parameter | Description |
| --------- | ----------- |
| username  | BBO username.|
| token | Hashed session token. |
  
### Accepted content-types

####  • application/x-www-form-urlencoded
Example:

```
POST https://webutil.bridgebase.com/v2/auth_check.php  
Authorization: Bearer client_api_key
Content-Type: application/x-www-form-urlencoded  
Accept: application/json
  
username=some_username&token=b507e2c594b0ddf11a15d6696b1190149311daab
```


####  • application/json
Example:

```
POST https://webutil.bridgebase.com/v2/auth_check.php  
Authorization: Bearer client_api_key
Content-Type: application/json 
Accept: application/json
    
{"username": "some_username", "token": "b507e2c594b0ddf11a15d6696b1190149311daab"}
```

### Response

#### Codes

| Response code | Description |
| ------------- | ----------- |
| 200 | Submitted credentials are or aren't valid (see response body). |
| 400 | Invalid request (check response body for further details). |
| 401 | Invalid API key. |
| 405 | Invalid method (only POST is allowed). |

#### Content

Returned content type depends on your `Accept` HTTP header, which can be:

- `application/json`  if you want a JSON output
- `text/xml` for XML (by default)

#### Returned values:

| Key | Type | Description |
| --- | ---- | ----------- |
| success | boolean | **TRUE**: Submitted credentials are valid / **FALSE**: They aren't *(HTTP 200)*, or an error occured *(HTTP 40x)*. See `message`.  |
| message | string | Verbose description of what happened. |


## Last revision

March 2020.

## Contact

benoit@bridgebase.com
