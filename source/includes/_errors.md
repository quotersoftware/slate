# Errors

In case of errors (`4XX` or `5XX` HTTP status codes), the API returns an error response body with a `key` , `title` , and `detail` .
For example, this is the JSON you will get with a 401 error:

```
{
    "errors": [
        {
            "key": "ERR_AUTHORIZATION_TOKEN_INVALID",
            "title": "Unauthorized",
            "detail": "Authorization token is invalid"
        }
    ]
}
```
