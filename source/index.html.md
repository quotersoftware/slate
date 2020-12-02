---
title: Quoter API Reference v1.0.0
language_tabs:
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - go: Go
language_clients:
  - javascript: ""
  - ruby: ""
  - python: ""
  - go: ""
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="quoter-api-reference">Quoter API Reference v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

TODO: Introduction

Base URLs:

* <a href="https://api.quoter.com/v1">https://api.quoter.com/v1</a>

# Authentication

- HTTP Authentication, scheme: bearer An access token acquired from the /auth/oauth/authorize endpoint.

<h1 id="quoter-api-reference-authorization">Authorization</h1>

## Get an access/refresh token

> Code samples

```javascript
const inputBody = '{
  "grant_type": "client_credentials",
  "client_id": "cid_asdf1234",
  "client_secret": "topsecret"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://api.quoter.com/v1/auth/oauth/authorize',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.quoter.com/v1/auth/oauth/authorize',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.quoter.com/v1/auth/oauth/authorize', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/auth/oauth/authorize", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/oauth/authorize`

> Body parameter

```json
{
  "grant_type": "client_credentials",
  "client_id": "cid_asdf1234",
  "client_secret": "topsecret"
}
```

<h3 id="get-an-access/refresh-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» grant_type|body|string|false|none|
|» client_id|body|string|false|none|
|» client_secret|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkphbmUgRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.cMErWtEf7DxCXJl8C9q0L7ttkm-Ex54UWHsOCMGbtUc"
}
```

<h3 id="get-an-access/refresh-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[tokens](#schematokens)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authorization invalid|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error|None|

<aside class="success">
This operation does not require authentication
</aside>

## Get a new access/refresh token from a refresh token

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/auth/refresh',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/auth/refresh',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/auth/refresh', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/auth/refresh", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/refresh`

> Example responses

> 200 Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkphbmUgRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.cMErWtEf7DxCXJl8C9q0L7ttkm-Ex54UWHsOCMGbtUc"
}
```

<h3 id="get-a-new-access/refresh-token-from-a-refresh-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[tokens](#schematokens)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authorization invalid|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-categories">Categories</h1>

## List categories

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/categories',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/categories',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/categories', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/categories", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /categories`

<h3 id="list-categories-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer|false|The number of records to return|
|page|query|integer|false|The page number|
|fields|query|array|false|One or more of id, name, parent_category, parent_category_id, created_at, and modified_at, separated by commas|
|parent_category_id|query|string|false|The category parent's id|
|sort_by|query|string|false|One of name, -name, created_at, -created_at, modified_at, or -modified_at|
|filter|query|string|false|One of name or name[cont]. name[cont] searches for all names that contains the specified string|

> Example responses

> 200 Response

```json
{
  "has_more": false,
  "total_count": 1,
  "data": [
    {
      "id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
      "name": "Test Category",
      "parent_category": "Test Parent Category",
      "parent_category_id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
      "created_at": "2019-08-24T14:15:22Z",
      "modified_at": "2019-08-24T14:15:22Z"
    }
  ]
}
```

<h3 id="list-categories-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<h3 id="list-categories-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» has_more|boolean|false|none|none|
|» total_count|integer|false|none|none|
|» data|[[category](#schemacategory)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» parent_category|string|false|none|none|
|»» parent_category_id|string|false|none|none|
|»» created_at|string(date-time)|false|none|none|
|»» modified_at|string(date-time)|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Create a category

> Code samples

```javascript
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/categories',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/categories',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/categories', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/categories", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /categories`

> Body parameter

```json
"string"
```

<h3 id="create-a-category-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|The name of the category|

> Example responses

> 200 Response

```json
{
  "id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Category",
  "parent_category": "Test Parent Category",
  "parent_category_id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="create-a-category-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[category](#schemacategory)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Delete a category

> Code samples

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/categories/{publicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.quoter.com/v1/categories/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.quoter.com/v1/categories/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.quoter.com/v1/categories/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /categories/{publicId}`

<h3 id="delete-a-category-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Category not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error (category is being used or contains child)|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch a category

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/categories/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/categories/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/categories/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/categories/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /categories/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Category",
  "parent_category": "Test Parent Category",
  "parent_category_id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="fetch-a-category-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[category](#schemacategory)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Category not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Update a category

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/categories/{publicId}',
{
  method: 'PATCH',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://api.quoter.com/v1/categories/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://api.quoter.com/v1/categories/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.quoter.com/v1/categories/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /categories/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Category",
  "parent_category": "Test Parent Category",
  "parent_category_id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="update-a-category-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[category](#schemacategory)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Category not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-itemoptions">ItemOptions</h1>

## Create an item option

> Code samples

```javascript
const inputBody = '{
  "allow_multiple_values": false,
  "description": "<p>Standard description</p>",
  "extended_description": "<p>Longer description.</p>",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Size",
  "required": false,
  "sort_order": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/item_options',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/item_options',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/item_options', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/item_options", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /item_options`

> Body parameter

```json
{
  "allow_multiple_values": false,
  "description": "<p>Standard description</p>",
  "extended_description": "<p>Longer description.</p>",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Size",
  "required": false,
  "sort_order": 0
}
```

<h3 id="create-an-item-option-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|Request body for an item option|
|» allow_multiple_values|body|boolean|false|none|
|» description|body|string|false|none|
|» extended_description|body|string|false|none|
|» item_id|body|string|true|none|
|» name|body|string|true|none|
|» required|body|boolean|false|none|
|» sort_order|body|integer|false|none|

> Example responses

> 200 Response

```json
{
  "allow_multiple_values": false,
  "created_at": "2019-08-24T14:15:22Z",
  "description": "<p>Standard description</p>",
  "extended_description": "<p>Longer description.</p>",
  "id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Size",
  "required": false,
  "sort_order": 0
}
```

<h3 id="create-an-item-option-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[itemoption](#schemaitemoption)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch an item option

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/item_options/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/item_options/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/item_options/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/item_options/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /item_options/{publicId}`

> Example responses

> 200 Response

```json
{
  "allow_multiple_values": false,
  "created_at": "2019-08-24T14:15:22Z",
  "description": "<p>Standard description</p>",
  "extended_description": "<p>Longer description.</p>",
  "id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Size",
  "required": false,
  "sort_order": 0
}
```

<h3 id="fetch-an-item-option-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[itemoption](#schemaitemoption)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|ItemOption not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-itemoptionvalues">ItemOptionValues</h1>

## Create an item option value

> Code samples

```javascript
const inputBody = '{
  "code": "sku",
  "cost_decimal": "50.50",
  "cost_type": "amount",
  "item_option_id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "item option value",
  "price_decimal": "50.50",
  "price_type": "amount",
  "sort_order": 1
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/item_option_values',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/item_option_values',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/item_option_values', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/item_option_values", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /item_option_values`

> Body parameter

```json
{
  "code": "sku",
  "cost_decimal": "50.50",
  "cost_type": "amount",
  "item_option_id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "item option value",
  "price_decimal": "50.50",
  "price_type": "amount",
  "sort_order": 1
}
```

<h3 id="create-an-item-option-value-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|Request body for an item option value|
|» code|body|string|false|none|
|» cost_decimal|body|string|false|none|
|» cost_type|body|string|false|none|
|» item_option_id|body|string|true|none|
|» name|body|string|true|none|
|» price_decimal|body|string|false|none|
|» price_type|body|string|false|none|
|» sort_order|body|integer|false|none|

> Example responses

> 200 Response

```json
{
  "code": "sku",
  "cost_decimal": "50.50",
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_option_id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Item Option Value",
  "price_decimal": "50.50",
  "price_type": "amount",
  "id": "iov_1jAEZdbtkbLFBAU1Tt0ouKpiBUe"
}
```

<h3 id="create-an-item-option-value-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[itemoptionvalue](#schemaitemoptionvalue)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Delete an item option value

> Code samples

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/item_option_values/{publicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.quoter.com/v1/item_option_values/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.quoter.com/v1/item_option_values/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.quoter.com/v1/item_option_values/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /item_option_values/{publicId}`

<h3 id="delete-an-item-option-value-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|ItemOptionValue not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch an item option value

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/item_option_values/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/item_option_values/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/item_option_values/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/item_option_values/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /item_option_values/{publicId}`

> Example responses

> 200 Response

```json
{
  "code": "sku",
  "cost_decimal": "50.50",
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_option_id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Item Option Value",
  "price_decimal": "50.50",
  "price_type": "amount",
  "id": "iov_1jAEZdbtkbLFBAU1Tt0ouKpiBUe"
}
```

<h3 id="fetch-an-item-option-value-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[itemoptionvalue](#schemaitemoptionvalue)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|ItemOptionValue not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-items">Items</h1>

## List Items

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/items',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/items',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/items', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/items", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /items`

<h3 id="list-items-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer|false|The number of records to return.|
|page|query|integer|false|The page number.|
|fields|query|string|false|none|
|sort_by|query|string|false|One or more of ( -created_at, -id, -modified_at, -name, created_at, id, modified_at, name, ), separated by commas|
|filter|query|string|false|One or more of (category_id, code, created_at[gt], created_at[lt], manufacturer_id, modified_at[gt], modified_at[lt], name, name[cont], sku, or supplier_id), separated by commas.|

#### Detailed descriptions

**filter**: One or more of (category_id, code, created_at[gt], created_at[lt], manufacturer_id, modified_at[gt], modified_at[lt], name, name[cont], sku, or supplier_id), separated by commas.

category_id searches for all objects that are associated with category_id.
code searches for all objects whose code value is equal to code.
created_at[gt] searches for all objects created after time period.
created_at[lt] searches for all objects created before time period.
manufacturer_id searches for all objects that are associated with manufacturer_id.
modified_at[gt] searches for all objects modified after time period.
modified_at[lt] searches for all objects modified before time period.
name searches for all objects whose name value is equal to name.
name[cont] searches for all objects whose name value contains name.
sku searches for all objects whose sku value is equal to sku.
supplier_id searches for all objects that are associated with supplier_id.

#### Enumerated Values

|Parameter|Value|
|---|---|
|fields|allow_decimal_quantities|
|fields|category_id|
|fields|category|
|fields|code|
|fields|cost_decimal|
|fields|cost_type|
|fields|created_at|
|fields|description|
|fields|id|
|fields|internal_note|
|fields|manufacturer_id|
|fields|manufacturer|
|fields|modified_at|
|fields|name|
|fields|percentage_price_category_ids|
|fields|percentage_price_decimal|
|fields|price_decimal|
|fields|pricing_scheme|
|fields|quantity_help_tip|
|fields|recurring_interval|
|fields|recurring|
|fields|restrict_discounting|
|fields|show_option_prices|
|fields|sku|
|fields|supplier_id|
|fields|supplier|
|fields|taxable|
|fields|weight_decimal|
|sort_by|-created_at|
|sort_by|-id|
|sort_by|-modified_at|
|sort_by|-name|
|sort_by|created_at|
|sort_by|id|
|sort_by|modified_at|
|sort_by|name|

> Example responses

> 200 Response

```json
{
  "has_more": false,
  "total_count": 1,
  "data": []
}
```

<h3 id="list-items-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<h3 id="list-items-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» has_more|boolean|false|none|none|
|» total_count|integer|false|none|none|
|» data|array|false|none|none|
|»» *anonymous*|any|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Create an item

> Code samples

```javascript
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/items',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/items',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/items', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/items", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /items`

> Body parameter

```json
"string"
```

<h3 id="create-an-item-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|The name of the item|

> Example responses

> 200 Response

```json
{
  "id": "item_OcThl0eqYyTVQzll6qFrMDMBYyu",
  "allow_decimal_quantities": true,
  "category": "Test Category",
  "category_id": "cat_OcThl8SOeE8w6JYUznfrnQGdp94",
  "code": "Test Code",
  "cost_decimal": 50.5,
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "description": "Test Description",
  "internal_note": "Test Internal Note",
  "manufacturer": "Test Manufacturer",
  "manufacturer_id": "manu_OcThlEWcbhAG52u3vLJodwnV88k",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Name",
  "percentage_price_category_ids": "[\n\n\n  cat_OcThlTV6Tama8RH5Zh4Jfw1fhJC,\n  cat_OcThlfcZ0OdBgF5EFb7qI1h1GDe,\n  cat_OcThlnsT1KxdEBMaqSVmYKpG6Ck\n]",
  "percentage_price_decimal": 50.5,
  "price_decimal": 50.5,
  "pricing_scheme": "per_unit",
  "quantity_help_tip": "Test Quantity Help Tip",
  "recurring": true,
  "recurring_interval": "annually",
  "restrict_discounting": true,
  "show_option_prices": true,
  "sku": "Test SKU",
  "supplier": "Test Supplier",
  "supplier_id": "sup_OcThlLwzLAM7m5eK1WEKkXUQZtm",
  "taxable": true,
  "weight_decimal": 50.5
}
```

<h3 id="create-an-item-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[item](#schemaitem)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Delete an item

> Code samples

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/items/{publicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.quoter.com/v1/items/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.quoter.com/v1/items/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.quoter.com/v1/items/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /items/{publicId}`

<h3 id="delete-an-item-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Item not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error (item is being used or contains child)|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch an item

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/items/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/items/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/items/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/items/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /items/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "item_OcThl0eqYyTVQzll6qFrMDMBYyu",
  "allow_decimal_quantities": true,
  "category": "Test Category",
  "category_id": "cat_OcThl8SOeE8w6JYUznfrnQGdp94",
  "code": "Test Code",
  "cost_decimal": 50.5,
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "description": "Test Description",
  "internal_note": "Test Internal Note",
  "manufacturer": "Test Manufacturer",
  "manufacturer_id": "manu_OcThlEWcbhAG52u3vLJodwnV88k",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Name",
  "percentage_price_category_ids": "[\n\n\n  cat_OcThlTV6Tama8RH5Zh4Jfw1fhJC,\n  cat_OcThlfcZ0OdBgF5EFb7qI1h1GDe,\n  cat_OcThlnsT1KxdEBMaqSVmYKpG6Ck\n]",
  "percentage_price_decimal": 50.5,
  "price_decimal": 50.5,
  "pricing_scheme": "per_unit",
  "quantity_help_tip": "Test Quantity Help Tip",
  "recurring": true,
  "recurring_interval": "annually",
  "restrict_discounting": true,
  "show_option_prices": true,
  "sku": "Test SKU",
  "supplier": "Test Supplier",
  "supplier_id": "sup_OcThlLwzLAM7m5eK1WEKkXUQZtm",
  "taxable": true,
  "weight_decimal": 50.5
}
```

<h3 id="fetch-an-item-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[item](#schemaitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Item not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Update an item

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/items/{publicId}',
{
  method: 'PATCH',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://api.quoter.com/v1/items/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://api.quoter.com/v1/items/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.quoter.com/v1/items/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /items/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "item_OcThl0eqYyTVQzll6qFrMDMBYyu",
  "allow_decimal_quantities": true,
  "category": "Test Category",
  "category_id": "cat_OcThl8SOeE8w6JYUznfrnQGdp94",
  "code": "Test Code",
  "cost_decimal": 50.5,
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "description": "Test Description",
  "internal_note": "Test Internal Note",
  "manufacturer": "Test Manufacturer",
  "manufacturer_id": "manu_OcThlEWcbhAG52u3vLJodwnV88k",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Name",
  "percentage_price_category_ids": "[\n\n\n  cat_OcThlTV6Tama8RH5Zh4Jfw1fhJC,\n  cat_OcThlfcZ0OdBgF5EFb7qI1h1GDe,\n  cat_OcThlnsT1KxdEBMaqSVmYKpG6Ck\n]",
  "percentage_price_decimal": 50.5,
  "price_decimal": 50.5,
  "pricing_scheme": "per_unit",
  "quantity_help_tip": "Test Quantity Help Tip",
  "recurring": true,
  "recurring_interval": "annually",
  "restrict_discounting": true,
  "show_option_prices": true,
  "sku": "Test SKU",
  "supplier": "Test Supplier",
  "supplier_id": "sup_OcThlLwzLAM7m5eK1WEKkXUQZtm",
  "taxable": true,
  "weight_decimal": 50.5
}
```

<h3 id="update-an-item-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[item](#schemaitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Item not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-manufacturers">Manufacturers</h1>

## List manufacturers

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/manufacturers',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/manufacturers',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/manufacturers', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/manufacturers", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /manufacturers`

<h3 id="list-manufacturers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer|false|The number of records to return|
|page|query|integer|false|The page number|
|fields|query|array|false|One or more of id, name, created_at, and modified_at, separated by commas|
|sort_by|query|string|false|One of name, -name, created_at, -created_at, modified_at, or -modified_at|
|filter|query|string|false|One of name or name[cont]. name[cont] searches for all names that contains the specified string|

> Example responses

> 200 Response

```json
{
  "has_more": false,
  "total_count": 1,
  "data": [
    {
      "id": "manu_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
      "name": "Test Manufacturer",
      "created_at": "2019-08-24T14:15:22Z",
      "modified_at": "2019-08-24T14:15:22Z"
    }
  ]
}
```

<h3 id="list-manufacturers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<h3 id="list-manufacturers-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» has_more|boolean|false|none|none|
|» total_count|integer|false|none|none|
|» data|[[manufacturer](#schemamanufacturer)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» created_at|string(date-time)|false|none|none|
|»» modified_at|string(date-time)|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Create a manufacturer

> Code samples

```javascript
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/manufacturers',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/manufacturers',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/manufacturers', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/manufacturers", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /manufacturers`

> Body parameter

```json
"string"
```

<h3 id="create-a-manufacturer-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|The name of the manufacturer|

> Example responses

> 200 Response

```json
{
  "id": "manu_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Manufacturer",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="create-a-manufacturer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[manufacturer](#schemamanufacturer)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Delete a manufacturer

> Code samples

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/manufacturers/{publicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.quoter.com/v1/manufacturers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.quoter.com/v1/manufacturers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.quoter.com/v1/manufacturers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /manufacturers/{publicId}`

<h3 id="delete-a-manufacturer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Manufacturer not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error (manufacturer is being used)|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch a manufacturer

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/manufacturers/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/manufacturers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/manufacturers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/manufacturers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /manufacturers/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "manu_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Manufacturer",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="fetch-a-manufacturer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[manufacturer](#schemamanufacturer)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Manufacturer not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Update a manufacturer

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/manufacturers/{publicId}',
{
  method: 'PATCH',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://api.quoter.com/v1/manufacturers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://api.quoter.com/v1/manufacturers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.quoter.com/v1/manufacturers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /manufacturers/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "manu_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Manufacturer",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="update-a-manufacturer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[manufacturer](#schemamanufacturer)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Manufacturer not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

<h1 id="quoter-api-reference-suppliers">Suppliers</h1>

## List suppliers

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/suppliers',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/suppliers',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/suppliers', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/suppliers", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /suppliers`

<h3 id="list-suppliers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer|false|The number of records to return|
|page|query|integer|false|The page number|
|fields|query|array|false|One or more of id, name, created_at, and modified_at, separated by commas|
|sort_by|query|string|false|One of name, -name, created_at, -created_at, modified_at, or -modified_at|
|filter|query|string|false|One of name or name[cont]. name[cont] searches for all names that contains the specified string|

> Example responses

> 200 Response

```json
{
  "has_more": false,
  "total_count": 1,
  "data": [
    {
      "id": "sup_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
      "name": "Test Supplier",
      "created_at": "2019-08-24T14:15:22Z",
      "modified_at": "2019-08-24T14:15:22Z"
    }
  ]
}
```

<h3 id="list-suppliers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<h3 id="list-suppliers-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» has_more|boolean|false|none|none|
|» total_count|integer|false|none|none|
|» data|[[supplier](#schemasupplier)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» created_at|string(date-time)|false|none|none|
|»» modified_at|string(date-time)|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Create a supplier

> Code samples

```javascript
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/suppliers',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://api.quoter.com/v1/suppliers',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://api.quoter.com/v1/suppliers', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.quoter.com/v1/suppliers", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /suppliers`

> Body parameter

```json
"string"
```

<h3 id="create-a-supplier-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|string|true|The name of the supplier|

> Example responses

> 200 Response

```json
{
  "id": "sup_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Supplier",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="create-a-supplier-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[supplier](#schemasupplier)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Delete a supplier

> Code samples

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/suppliers/{publicId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://api.quoter.com/v1/suppliers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://api.quoter.com/v1/suppliers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.quoter.com/v1/suppliers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /suppliers/{publicId}`

<h3 id="delete-a-supplier-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Supplier not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error (supplier is being used)|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Fetch a supplier

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/suppliers/{publicId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.quoter.com/v1/suppliers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.quoter.com/v1/suppliers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.quoter.com/v1/suppliers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /suppliers/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "sup_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Supplier",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="fetch-a-supplier-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[supplier](#schemasupplier)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Supplier not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

## Update a supplier

> Code samples

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://api.quoter.com/v1/suppliers/{publicId}',
{
  method: 'PATCH',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://api.quoter.com/v1/suppliers/{publicId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://api.quoter.com/v1/suppliers/{publicId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.quoter.com/v1/suppliers/{publicId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /suppliers/{publicId}`

> Example responses

> 200 Response

```json
{
  "id": "sup_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Supplier",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}
```

<h3 id="update-a-supplier-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[supplier](#schemasupplier)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Supplier not found|None|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation error in request|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2
</aside>

# Schemas

<h2 id="tocS_tokens">tokens</h2>
<!-- backwards compatibility -->
<a id="schematokens"></a>
<a id="schema_tokens"></a>
<a id="tocStokens"></a>
<a id="tocstokens"></a>

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkphbmUgRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.cMErWtEf7DxCXJl8C9q0L7ttkm-Ex54UWHsOCMGbtUc"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|access_token|string|false|none|none|
|refresh_token|string|false|none|none|

<h2 id="tocS_category">category</h2>
<!-- backwards compatibility -->
<a id="schemacategory"></a>
<a id="schema_category"></a>
<a id="tocScategory"></a>
<a id="tocscategory"></a>

```json
{
  "id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Category",
  "parent_category": "Test Parent Category",
  "parent_category_id": "cat_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|parent_category|string|false|none|none|
|parent_category_id|string|false|none|none|
|created_at|string(date-time)|false|none|none|
|modified_at|string(date-time)|false|none|none|

<h2 id="tocS_itemoption">itemoption</h2>
<!-- backwards compatibility -->
<a id="schemaitemoption"></a>
<a id="schema_itemoption"></a>
<a id="tocSitemoption"></a>
<a id="tocsitemoption"></a>

```json
{
  "allow_multiple_values": false,
  "created_at": "2019-08-24T14:15:22Z",
  "description": "<p>Standard description</p>",
  "extended_description": "<p>Longer description.</p>",
  "id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Size",
  "required": false,
  "sort_order": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|allow_multiple_values|boolean|false|none|none|
|created_at|string(date-time)|false|none|none|
|description|string|false|none|none|
|extended_description|string|false|none|none|
|id|string|false|none|none|
|item_id|string|false|none|none|
|modified_at|string(date-time)|false|none|none|
|name|string|false|none|none|
|required|boolean|false|none|none|
|sort_order|integer|false|none|none|

<h2 id="tocS_itemoptionvalue">itemoptionvalue</h2>
<!-- backwards compatibility -->
<a id="schemaitemoptionvalue"></a>
<a id="schema_itemoptionvalue"></a>
<a id="tocSitemoptionvalue"></a>
<a id="tocsitemoptionvalue"></a>

```json
{
  "code": "sku",
  "cost_decimal": "50.50",
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "item_id": "item_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "item_option_id": "iopt_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Item Option Value",
  "price_decimal": "50.50",
  "price_type": "amount",
  "id": "iov_1jAEZdbtkbLFBAU1Tt0ouKpiBUe"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|string|false|none|none|
|cost_decimal|string|false|none|none|
|cost_type|string|false|none|none|
|created_at|string(date-time)|false|none|none|
|item_id|string|false|none|none|
|item_option_id|string|false|none|none|
|modified_at|string(date-time)|false|none|none|
|name|string|false|none|none|
|price_decimal|string|false|none|none|
|price_type|string|false|none|none|
|id|string|false|none|none|

<h2 id="tocS_item">item</h2>
<!-- backwards compatibility -->
<a id="schemaitem"></a>
<a id="schema_item"></a>
<a id="tocSitem"></a>
<a id="tocsitem"></a>

```json
{
  "id": "item_OcThl0eqYyTVQzll6qFrMDMBYyu",
  "allow_decimal_quantities": true,
  "category": "Test Category",
  "category_id": "cat_OcThl8SOeE8w6JYUznfrnQGdp94",
  "code": "Test Code",
  "cost_decimal": 50.5,
  "cost_type": "amount",
  "created_at": "2019-08-24T14:15:22Z",
  "description": "Test Description",
  "internal_note": "Test Internal Note",
  "manufacturer": "Test Manufacturer",
  "manufacturer_id": "manu_OcThlEWcbhAG52u3vLJodwnV88k",
  "modified_at": "2019-08-24T14:15:22Z",
  "name": "Test Name",
  "percentage_price_category_ids": "[\n\n\n  cat_OcThlTV6Tama8RH5Zh4Jfw1fhJC,\n  cat_OcThlfcZ0OdBgF5EFb7qI1h1GDe,\n  cat_OcThlnsT1KxdEBMaqSVmYKpG6Ck\n]",
  "percentage_price_decimal": 50.5,
  "price_decimal": 50.5,
  "pricing_scheme": "per_unit",
  "quantity_help_tip": "Test Quantity Help Tip",
  "recurring": true,
  "recurring_interval": "annually",
  "restrict_discounting": true,
  "show_option_prices": true,
  "sku": "Test SKU",
  "supplier": "Test Supplier",
  "supplier_id": "sup_OcThlLwzLAM7m5eK1WEKkXUQZtm",
  "taxable": true,
  "weight_decimal": 50.5
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|allow_decimal_quantities|boolean|false|none|none|
|category|string|false|none|none|
|category_id|string|false|none|none|
|code|string|false|none|none|
|cost_decimal|string|false|none|none|
|cost_type|string|false|none|none|
|created_at|string(date-time)|false|none|none|
|description|string|false|none|none|
|internal_note|string|false|none|none|
|manufacturer|string|false|none|none|
|manufacturer_id|string|false|none|none|
|modified_at|string(date-time)|false|none|none|
|name|string|false|none|none|
|percentage_price_category_ids|[string]|false|none|none|
|percentage_price_decimal|string|false|none|none|
|price_decimal|string|false|none|none|
|pricing_scheme|string|false|none|none|
|quantity_help_tip|string|false|none|none|
|recurring|boolean|false|none|none|
|recurring_interval|string|false|none|none|
|restrict_discounting|boolean|false|none|none|
|show_option_prices|boolean|false|none|none|
|sku|string|false|none|none|
|supplier|string|false|none|none|
|supplier_id|string|false|none|none|
|taxable|boolean|false|none|none|
|weight_decimal|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|cost_type|amount|
|cost_type|percentage|
|pricing_scheme|per_unit|
|pricing_scheme|flat|
|pricing_scheme|tiered_volume|
|pricing_scheme|tiered_stepped|
|pricing_scheme|percentage|
|recurring_interval|monthly|
|recurring_interval|quarterly|
|recurring_interval|semi_annually|
|recurring_interval|annually|

<h2 id="tocS_manufacturer">manufacturer</h2>
<!-- backwards compatibility -->
<a id="schemamanufacturer"></a>
<a id="schema_manufacturer"></a>
<a id="tocSmanufacturer"></a>
<a id="tocsmanufacturer"></a>

```json
{
  "id": "manu_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Manufacturer",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|created_at|string(date-time)|false|none|none|
|modified_at|string(date-time)|false|none|none|

<h2 id="tocS_supplier">supplier</h2>
<!-- backwards compatibility -->
<a id="schemasupplier"></a>
<a id="schema_supplier"></a>
<a id="tocSsupplier"></a>
<a id="tocssupplier"></a>

```json
{
  "id": "sup_1jAEZdbtkbLFBAU1Tt0ouKpiBUe",
  "name": "Test Supplier",
  "created_at": "2019-08-24T14:15:22Z",
  "modified_at": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|created_at|string(date-time)|false|none|none|
|modified_at|string(date-time)|false|none|none|

