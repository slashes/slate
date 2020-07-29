---
title: Harqen API v2.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="harqen-api">Harqen API v2.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The HarQen API provides a client with the ability to:
- Query for available campaigns.
- Create an interview for a candidate.
- Get the interview for a candidate including media.
- Be notified when an interview has been completed.
- Create a presentation URL in order to access the completed interview link.

Access the API via https://va.harqen.com domain.

The relative path /v2/ indicates the version of the API.

Please contact us for a [developer key](mailto:support@harqen.com?subject=Developer%20Key). 

Base URLs:

* <a href="https://va.harqen.com/{basePath}">https://va.harqen.com/{basePath}</a>

    * **basePath** -  Default: v2

Email: <a href="mailto:support@harqen.com">Support</a> 

# Authentication

- HTTP Authentication, scheme: basic 

<h1 id="harqen-api-campaigns">Campaigns</h1>

Used to create new Campaigns from scratch, from a template, or copied from an existing Campaign.

## Get Campaign by id

> Code samples

```shell
# You can also use wget
curl -X GET https://va.harqen.com/{basePath}/campaign/{campaignId} \
  -H 'Accept: application/json'

```

```http
GET https://va.harqen.com/{basePath}/campaign/{campaignId} HTTP/1.1
Host: va.harqen.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/{campaignId}',
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
  'Accept' => 'application/json'
}

result = RestClient.get 'https://va.harqen.com/{basePath}/campaign/{campaignId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://va.harqen.com/{basePath}/campaign/{campaignId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://va.harqen.com/{basePath}/campaign/{campaignId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/{campaignId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://va.harqen.com/{basePath}/campaign/{campaignId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /campaign/{campaignId}`

Returns a campaign id and name.

<h3 id="get-campaign-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|campaignId|path|integer(int64)|true|ID of campaign to return. Must belong to the company and exist.|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "campaignName": "string",
  "ownerId": 1,
  "typeInd": 0
}
```

<h3 id="get-campaign-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Campaign](#schemacampaign)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## New Campaign

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/create \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/create HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignName": "string",
  "clientBrandingId": 0,
  "customFieldValues": [],
  "departmentId": 0,
  "description": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/create',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/create',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/create', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/create', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/create");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/create", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/create`

Create a new Campaign with the given object.

> Body parameter

```json
{
  "campaignName": "string",
  "clientBrandingId": 0,
  "customFieldValues": [],
  "departmentId": 0,
  "description": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0
}
```

<h3 id="new-campaign-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Campaign](#schemacampaign)|true|Details for the new Campaign.|
|» id|body|integer(int64)|true|none|
|» campaignName|body|string|true|Less than 512 characters.|
|» clientBrandingId|body|integer(int64)|true|none|
|» customFieldValues|body|any|false|none|
|»» *anonymous*|body|[object]|false|none|
|»»» id|body|integer(int64)|false|none|
|»»» value|body|string|false|none|
|»» *anonymous*|body|any|false|none|
|» departmentId|body|integer(int64)|true|none|
|» description|body|string|false|Less than 512 characters.|
|» jobId|body|string|false|Less than 64 characters.|
|» numBatchReviewHoldDays|body|integer(int64)|true|Valid range is 0 to 20.|
|» ownerId|body|integer(int64)|true|none|
|» privateInd|body|any|true|none|
|»» *anonymous*|body|[PrivateInd](#schemaprivateind)(int64)|false|none|
|»» *anonymous*|body|any|false|none|
|» typeInd|body|[TypeInd](#schematypeind)(int64)|true|Valid values: 0 (audio), 1 (text), 2 (video)|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»» *anonymous*|0|
|»» *anonymous*|1|
|» typeInd|0|
|» typeInd|1|
|» typeInd|2|

> Example responses

> 200 Response

```json
{
  "campaignId": 0
}
```

<h3 id="new-campaign-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="new-campaign-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» campaignId|integer(int64)|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## New Campaign from copy

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/copyfromcampaign \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/copyfromcampaign HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignOrTemplateId": 0,
  "campaignName": "string",
  "ownerId": 1,
  "emailGreetingReplyTo": "string",
  "description": "string",
  "jobId": "string",
  "customFieldValues": [
    {
      "id": 0,
      "value": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/copyfromcampaign',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/copyfromcampaign',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/copyfromcampaign', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/copyfromcampaign', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/copyfromcampaign");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/copyfromcampaign", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/copyfromcampaign`

Create a new Campaign using the same data copied over from another existing Campaign.

> Body parameter

```json
{
  "campaignOrTemplateId": 0,
  "campaignName": "string",
  "ownerId": 1,
  "emailGreetingReplyTo": "string",
  "description": "string",
  "jobId": "string",
  "customFieldValues": [
    {
      "id": 0,
      "value": "string"
    }
  ]
}
```

<h3 id="new-campaign-from-copy-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CampaignCopy](#schemacampaigncopy)|true|Details needed to create a new Campaign copy.|
|» campaignOrTemplateId|body|integer(int64)|true|none|
|» campaignName|body|string|true|Less than 512 characters.|
|» ownerId|body|integer(int64)|true|none|
|» emailGreetingReplyTo|body|string|true|none|
|» description|body|string|false|Less than 512 characters.|
|» jobId|body|string|false|Less than 64 characters.|
|» customFieldValues|body|[object]|false|none|
|»» id|body|integer(int64)|false|none|
|»» value|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "campaignId": 0
}
```

<h3 id="new-campaign-from-copy-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="new-campaign-from-copy-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» campaignId|integer(int64)|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## New Campaign from Template

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/copyfromtemplate \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/copyfromtemplate HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignOrTemplateId": 0,
  "campaignName": "string",
  "ownerId": 1,
  "emailGreetingReplyTo": "string",
  "description": "string",
  "jobId": "string",
  "customFieldValues": [
    {
      "id": 0,
      "value": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/copyfromtemplate',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/copyfromtemplate',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/copyfromtemplate', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/copyfromtemplate', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/copyfromtemplate");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/copyfromtemplate", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/copyfromtemplate`

Create a new Campaign using the data copied over from an existing template.

> Body parameter

```json
{
  "campaignOrTemplateId": 0,
  "campaignName": "string",
  "ownerId": 1,
  "emailGreetingReplyTo": "string",
  "description": "string",
  "jobId": "string",
  "customFieldValues": [
    {
      "id": 0,
      "value": "string"
    }
  ]
}
```

<h3 id="new-campaign-from-template-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CampaignCopy](#schemacampaigncopy)|true|Details needed to create a new Campaign from a template.|
|» campaignOrTemplateId|body|integer(int64)|true|none|
|» campaignName|body|string|true|Less than 512 characters.|
|» ownerId|body|integer(int64)|true|none|
|» emailGreetingReplyTo|body|string|true|none|
|» description|body|string|false|Less than 512 characters.|
|» jobId|body|string|false|Less than 64 characters.|
|» customFieldValues|body|[object]|false|none|
|»» id|body|integer(int64)|false|none|
|»» value|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "campaignId": 0
}
```

<h3 id="new-campaign-from-template-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="new-campaign-from-template-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» campaignId|integer(int64)|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-qualifying-questions">Qualifying Questions</h1>

To add or update Qualifying Questions in a Campaign.

## Update Qualifying Questions

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "qualifyingQuestionsToAdd": {
    "questionType": "yesOrNo",
    "questionText": "string",
    "requiredInd": 0,
    "expectedAnswerBoolean": true
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/qualifyingquestion", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/qualifyingquestion`

Change the Qualifying Questions for an existing interview.

> Body parameter

```json
{
  "campaignId": 1,
  "qualifyingQuestionsToAdd": {
    "questionType": "yesOrNo",
    "questionText": "string",
    "requiredInd": 0,
    "expectedAnswerBoolean": true
  }
}
```

<h3 id="update-qualifying-questions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[QualifyingQuestions](#schemaqualifyingquestions)|true|Details needed to change the Qualifying Questions. There are three types of operations that can be executed with this endpoint. To add a question, please populate the ONE relevant property for the operation: `qualifyingQuestionsToAdd`, `qualifyingQuestionsToUpdate`, `qualifyingQuestionsToCopy` or `qualifyingQuestionsToDelete`.|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="update-qualifying-questions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="update-qualifying-questions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-interviews">Interviews</h1>

To add or update Interview Questions in a Campaign.

## Change Interview Settings

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/interview \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/interview HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "emailGreetingSubject": "string",
  "emailGreeting": "string",
  "emailGreetingSignature": "string",
  "inviteSms": "string",
  "emailGreetingReplyTo": "string",
  "interviewNowText": "string",
  "interviewNowSms": "string",
  "callInfoText": "string",
  "interviewCompleteText": "string",
  "redirectUrl": "string",
  "interviewCompleteSms": "string",
  "emailNextstepSubject": "string",
  "emailNextstepSignature": "string",
  "emailNextstep": "string",
  "prequalFailedText": "string",
  "failedRedirectUrl": "string",
  "prequalFailedSms": "string",
  "haltInterviewSms": "string",
  "haltInterviewText": "string",
  "sendRejectEmailInd": 0,
  "emailReject": "string",
  "emailRejectSignature": "string",
  "emailRejectSubject": "string",
  "sendAcceptEmailInd": 0,
  "emailAccept": "string",
  "emailAcceptSignature": "string",
  "emailAcceptSubject": "string",
  "reminder1Ind": 0,
  "reminder1Hours": 0,
  "reminder1EmailText": "string",
  "reminder2Ind": 0,
  "reminder2EmailText": "string",
  "reminder2Hours": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/interview',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/interview',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/interview', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/interview', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/interview");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/interview", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/interview`

Change or edit Settings for an Interview.

> Body parameter

```json
{
  "campaignId": 1,
  "emailGreetingSubject": "string",
  "emailGreeting": "string",
  "emailGreetingSignature": "string",
  "inviteSms": "string",
  "emailGreetingReplyTo": "string",
  "interviewNowText": "string",
  "interviewNowSms": "string",
  "callInfoText": "string",
  "interviewCompleteText": "string",
  "redirectUrl": "string",
  "interviewCompleteSms": "string",
  "emailNextstepSubject": "string",
  "emailNextstepSignature": "string",
  "emailNextstep": "string",
  "prequalFailedText": "string",
  "failedRedirectUrl": "string",
  "prequalFailedSms": "string",
  "haltInterviewSms": "string",
  "haltInterviewText": "string",
  "sendRejectEmailInd": 0,
  "emailReject": "string",
  "emailRejectSignature": "string",
  "emailRejectSubject": "string",
  "sendAcceptEmailInd": 0,
  "emailAccept": "string",
  "emailAcceptSignature": "string",
  "emailAcceptSubject": "string",
  "reminder1Ind": 0,
  "reminder1Hours": 0,
  "reminder1EmailText": "string",
  "reminder2Ind": 0,
  "reminder2EmailText": "string",
  "reminder2Hours": 0
}
```

<h3 id="change-interview-settings-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[InterviewSettings](#schemainterviewsettings)|true|Details needed to change Settings for an Interview.|
|» campaignId|body|integer(int64)|true|none|
|» emailGreetingSubject|body|string|false|none|
|» emailGreeting|body|string|false|none|
|» emailGreetingSignature|body|string|false|none|
|» inviteSms|body|string|false|none|
|» emailGreetingReplyTo|body|string|false|none|
|» interviewNowText|body|string|false|none|
|» interviewNowSms|body|string|false|none|
|» callInfoText|body|string|false|none|
|» interviewCompleteText|body|string|false|NOTE: If `redirectUrl` has a non-blank value, this field will be ignored.|
|» redirectUrl|body|string|false|none|
|» interviewCompleteSms|body|string|false|none|
|» emailNextstepSubject|body|string|false|none|
|» emailNextstepSignature|body|string|false|none|
|» emailNextstep|body|string|false|none|
|» prequalFailedText|body|string|false|NOTE: If `failedRedirectUrl` has a non-blank value, this field will be ignored.|
|» failedRedirectUrl|body|string|false|none|
|» prequalFailedSms|body|string|false|none|
|» haltInterviewSms|body|string|false|none|
|» haltInterviewText|body|string|false|none|
|» sendRejectEmailInd|body|integer|false|Valid values: 0 (do not send), 1 (send)|
|» emailReject|body|string|false|NOTE: If `sendRejectEmailInd` is set to 1, this field is required.|
|» emailRejectSignature|body|string|false|none|
|» emailRejectSubject|body|string|false|none|
|» sendAcceptEmailInd|body|integer|false|Valid values: 0 (do not send), 1 (send)|
|» emailAccept|body|string|false|NOTE: If `sendAcceptEmailInd` is set to 1, this field is required.|
|» emailAcceptSignature|body|string|false|none|
|» emailAcceptSubject|body|string|false|none|
|» reminder1Ind|body|integer|false|Valid values: 0 (do not remind), 1 (remind)|
|» reminder1Hours|body|integer(int64)|false|NOTE: If `reminder1Ind` is set to 1, this field is required.|
|» reminder1EmailText|body|string|false|NOTE: If `reminder1Ind` is set to 1, this field is required.|
|» reminder2Ind|body|integer|false|Valid values: 0 (do not remind), 1 (remind)|
|» reminder2EmailText|body|string|false|NOTE: If `reminder2Ind` is set to 1, this field is required.|
|» reminder2Hours|body|integer(int64)|false|NOTE: If `reminder2Ind` is set to 1, this field is required.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» sendRejectEmailInd|0|
|» sendRejectEmailInd|1|
|» sendAcceptEmailInd|0|
|» sendAcceptEmailInd|1|
|» reminder1Ind|0|
|» reminder1Ind|1|
|» reminder2Ind|0|
|» reminder2Ind|1|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="change-interview-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="change-interview-settings-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## Setup an Interview Now

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/interviewnow \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/interviewnow HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "requirePhoneNumberInd": 0,
  "requestPermissionToSmsInd": 0,
  "intNowResumeRequiredInd": -1
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/interviewnow',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/interviewnow',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/interviewnow', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/interviewnow', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/interviewnow");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/interviewnow", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/interviewnow`

Setup an Interview now.

> Body parameter

```json
{
  "campaignId": 1,
  "requirePhoneNumberInd": 0,
  "requestPermissionToSmsInd": 0,
  "intNowResumeRequiredInd": -1
}
```

<h3 id="setup-an-interview-now-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[InterviewNow](#schemainterviewnow)|true|Details needed to setup an Interview now.|
|» campaignId|body|integer(int64)|true|none|
|» requirePhoneNumberInd|body|integer|false|Valid values: 0 (do not require), 1 (require)|
|» requestPermissionToSmsInd|body|integer|false|Valid values: 0 (do not request), 1 (request). NOTE: If `requirePhoneNumberInd` is set to 1, this field is required.|
|» intNowResumeRequiredInd|body|integer|false|Valid values: -1 (dont ask), 0 (optional), 1 (required)|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» requirePhoneNumberInd|0|
|» requirePhoneNumberInd|1|
|» requestPermissionToSmsInd|0|
|» requestPermissionToSmsInd|1|
|» intNowResumeRequiredInd|-1|
|» intNowResumeRequiredInd|0|
|» intNowResumeRequiredInd|1|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="setup-an-interview-now-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="setup-an-interview-now-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## Email Notification for Interviews

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/emailnotification \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/emailnotification HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "userId": [
    1
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/emailnotification',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/emailnotification',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/emailnotification', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/emailnotification', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/emailnotification");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/emailnotification", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/emailnotification`

Send an email notification to potential candidates to apply for Campaigns.

> Body parameter

```json
{
  "campaignId": 1,
  "userId": [
    1
  ]
}
```

<h3 id="email-notification-for-interviews-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[EmailNotification](#schemaemailnotification)|true|Details needed to send an email notification.|
|» campaignId|body|integer(int64)|true|none|
|» userId|body|[integer]|false|none|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="email-notification-for-interviews-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="email-notification-for-interviews-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-interview-questions">Interview Questions</h1>

To add or update Questions in a Campaign.

## Update Campaign Interview Questions

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/interviewquestion \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/interviewquestion HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 48372,
  "questionsToAdd": [
    483,
    484,
    494
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/interviewquestion',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/interviewquestion',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/interviewquestion', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/interviewquestion', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/interviewquestion");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/interviewquestion", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/interviewquestion`

Change or edit Interview Questions used in a Campaign.

> Body parameter

```json
{
  "campaignId": 48372,
  "questionsToAdd": [
    483,
    484,
    494
  ]
}
```

<h3 id="update-campaign-interview-questions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[InterviewQuestion](#schemainterviewquestion)|true|Details needed to change Interview Questions for a Campaign. There are three types of operations that can be executed with this endpoint. To add a question, please populate the ONE relevant property for the operation: `questionsToAdd`, `questionsToUpdate`, or `questionsToDelete`.|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="update-campaign-interview-questions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="update-campaign-interview-questions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## Update Candidate Call

> Code samples

```shell
# You can also use wget
curl -X GET https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId} \
  -H 'Accept: application/json'

```

```http
GET https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId} HTTP/1.1
Host: va.harqen.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}',
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
  'Accept' => 'application/json'
}

result = RestClient.get 'https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://va.harqen.com/{basePath}/campaign/update/question/candidatecall/{campaignId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /campaign/update/question/candidatecall/{campaignId}`

Returns the call-in information for an interview.

<h3 id="update-candidate-call-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|campaignId|path|integer(int64)|true|ID of campaign. Must belong to the company and exist.|

> Example responses

> 200 Response

```json
[
  {
    "pin": 293847,
    "dialInNumber": "412-555-2345"
  }
]
```

<h3 id="update-candidate-call-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[CandidateCall](#schemacandidatecall)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

## Update Harqen Call

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/question/harqencall \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/question/harqencall HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "countryCode": "string",
  "areaCode": "string",
  "localNumber": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/question/harqencall',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/question/harqencall',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/question/harqencall', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/question/harqencall', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/question/harqencall");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/question/harqencall", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/question/harqencall`

Change the call-in number for an existing interview.

> Body parameter

```json
{
  "campaignId": 1,
  "countryCode": "string",
  "areaCode": "string",
  "localNumber": "string"
}
```

<h3 id="update-harqen-call-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[HarqenCall](#schemaharqencall)|true|Details needed to change the call-in number.|
|» campaignId|body|integer(int64)|true|none|
|» countryCode|body|string|true|Less than 3 characters.|
|» areaCode|body|string|true|none|
|» localNumber|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="update-harqen-call-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="update-harqen-call-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-access">Access</h1>

To add or update Access to a Campaign.

## Change Campaign Access Permissions

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/access \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/access HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "userIdsToAdd": [
    1
  ],
  "userIdsToDelete": [
    1
  ],
  "groupIdsToAdd": [
    1
  ],
  "groupIdsToDelete": [
    1
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/access',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/access',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/access', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/access', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/access");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/access", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/access`

To change the access permissions for a Campaign.

> Body parameter

```json
{
  "campaignId": 1,
  "userIdsToAdd": [
    1
  ],
  "userIdsToDelete": [
    1
  ],
  "groupIdsToAdd": [
    1
  ],
  "groupIdsToDelete": [
    1
  ]
}
```

<h3 id="change-campaign-access-permissions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CampaignAccess](#schemacampaignaccess)|true|Details needed to change access permissions.|
|» campaignId|body|integer(int64)|true|none|
|» userIdsToAdd|body|[integer]|false|none|
|» userIdsToDelete|body|[integer]|false|none|
|» groupIdsToAdd|body|[integer]|false|none|
|» groupIdsToDelete|body|[integer]|false|none|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="change-campaign-access-permissions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="change-campaign-access-permissions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-status">Status</h1>

To add or update Status of a Campaign.

## Change status of Campaign.

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/status \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/status HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "campaignId": 1,
  "activeInd": -1,
  "haltInterviewInd": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/status',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/status',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/status', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/status', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/status");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/status", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/status`

To change the status of a Campaign.

> Body parameter

```json
{
  "campaignId": 1,
  "activeInd": -1,
  "haltInterviewInd": 0
}
```

<h3 id="change-status-of-campaign.-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CampaignStatus](#schemacampaignstatus)|true|Details needed to change Campaign status.|
|» campaignId|body|integer(int64)|true|none|
|» activeInd|body|integer|false|Valid values: -1 (removed), 0 (archived), 1 (active).|
|» haltInterviewInd|body|integer|false|Valid values: 0 (do not halt), 1 (halt).|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» activeInd|-1|
|» activeInd|0|
|» activeInd|1|
|» haltInterviewInd|0|
|» haltInterviewInd|1|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="change-status-of-campaign.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="change-status-of-campaign.-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

<h1 id="harqen-api-settings">Settings</h1>

To add or update Campaign Settings.

## Change Campaigns Settings

> Code samples

```shell
# You can also use wget
curl -X POST https://va.harqen.com/{basePath}/campaign/update/settings \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://va.harqen.com/{basePath}/campaign/update/settings HTTP/1.1
Host: va.harqen.com
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "allowAnswerAssessment": true,
  "allowAudioFallback": true,
  "campaignId": 1,
  "campaignName": "string",
  "clientBrandingId": 0,
  "departmentId": 0,
  "description": "string",
  "enableAutoCandidateWithdrawal": true,
  "enableMediaTranscription": true,
  "interviewColor": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0,
  "requestPermissionToSms": true,
  "supportedLocaleId": 1,
  "withdrawCandidatesDays": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://va.harqen.com/{basePath}/campaign/update/settings',
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

result = RestClient.post 'https://va.harqen.com/{basePath}/campaign/update/settings',
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

r = requests.post('https://va.harqen.com/{basePath}/campaign/update/settings', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://va.harqen.com/{basePath}/campaign/update/settings', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://va.harqen.com/{basePath}/campaign/update/settings");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

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
    req, err := http.NewRequest("POST", "https://va.harqen.com/{basePath}/campaign/update/settings", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /campaign/update/settings`

Change or edit Settings for a Campaign.

> Body parameter

```json
{
  "allowAnswerAssessment": true,
  "allowAudioFallback": true,
  "campaignId": 1,
  "campaignName": "string",
  "clientBrandingId": 0,
  "departmentId": 0,
  "description": "string",
  "enableAutoCandidateWithdrawal": true,
  "enableMediaTranscription": true,
  "interviewColor": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0,
  "requestPermissionToSms": true,
  "supportedLocaleId": 1,
  "withdrawCandidatesDays": 0
}
```

<h3 id="change-campaigns-settings-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CampaignSettings](#schemacampaignsettings)|true|Details needed to change Settings for a Campaign.|
|» allowAnswerAssessment|body|boolean|false|none|
|» allowAudioFallback|body|boolean|false|none|
|» campaignId|body|integer(int64)|true|none|
|» campaignName|body|string|false|Less than 512 characters.|
|» clientBrandingId|body|integer(int64)|false|none|
|» departmentId|body|integer(int64)|false|none|
|» description|body|string|false|Less than 512 characters.|
|» enableAutoCandidateWithdrawal|body|boolean|false|none|
|» enableMediaTranscription|body|boolean|false|none|
|» interviewColor|body|string|false|Color in hex codes.|
|» jobId|body|string|false|Less than 64 characters.|
|» numBatchReviewHoldDays|body|integer(int64)|false|Valid range is 0 to 20.|
|» ownerId|body|integer(int64)|false|none|
|» privateInd|body|[PrivateInd](#schemaprivateind)(int64)|false|none|
|» typeInd|body|[TypeInd](#schematypeind)(int64)|false|Valid values: 0 (audio), 1 (text), 2 (video)|
|» requestPermissionToSms|body|boolean|false|none|
|» supportedLocaleId|body|[SupportedLocaleId](#schemasupportedlocaleid)(int64)|false|Valid values: 1 (en-US), 2 (es-ES), 3 (fr-CA)|
|» withdrawCandidatesDays|body|integer(int64)|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» privateInd|0|
|» privateInd|1|
|» typeInd|0|
|» typeInd|1|
|» typeInd|2|
|» supportedLocaleId|1|
|» supportedLocaleId|2|
|» supportedLocaleId|3|

> Example responses

> 200 Response

```json
{
  "result": "string"
}
```

<h3 id="change-campaigns-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication information is missing or invalid.|None|
|default|Default|Unexpected error has occurred. Please contact support.|None|

<h3 id="change-campaigns-settings-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|string|false|none|none|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|401|WWW_Authenticate|string||Authentication method used to gain access.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth
</aside>

# Schemas

<h2 id="tocS_Campaign">Campaign</h2>
<!-- backwards compatibility -->
<a id="schemacampaign"></a>
<a id="schema_Campaign"></a>
<a id="tocScampaign"></a>
<a id="tocscampaign"></a>

```json
{
  "id": 0,
  "campaignName": "string",
  "clientBrandingId": 0,
  "customFieldValues": [],
  "departmentId": 0,
  "description": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0
}

```

An object with Campaign details.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|read-only|none|
|campaignName|string|true|none|Less than 512 characters.|
|clientBrandingId|integer(int64)|true|write-only|none|
|customFieldValues|any|false|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[CustomFieldValues](#schemacustomfieldvalues)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|write-only|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|departmentId|integer(int64)|true|write-only|none|
|description|string|false|write-only|Less than 512 characters.|
|jobId|string|false|write-only|Less than 64 characters.|
|numBatchReviewHoldDays|integer(int64)|true|write-only|Valid range is 0 to 20.|
|ownerId|integer(int64)|true|none|none|
|privateInd|any|true|none|none|

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[PrivateInd](#schemaprivateind)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|write-only|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|typeInd|[TypeInd](#schematypeind)|true|none|Valid values: 0 (audio), 1 (text), 2 (video)|

<h2 id="tocS_CampaignCopy">CampaignCopy</h2>
<!-- backwards compatibility -->
<a id="schemacampaigncopy"></a>
<a id="schema_CampaignCopy"></a>
<a id="tocScampaigncopy"></a>
<a id="tocscampaigncopy"></a>

```json
{
  "campaignOrTemplateId": 0,
  "campaignName": "string",
  "ownerId": 1,
  "emailGreetingReplyTo": "string",
  "description": "string",
  "jobId": "string",
  "customFieldValues": [
    {
      "id": 0,
      "value": "string"
    }
  ]
}

```

An object with Campaign details.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignOrTemplateId|integer(int64)|true|none|none|
|campaignName|string|true|none|Less than 512 characters.|
|ownerId|integer(int64)|true|none|none|
|emailGreetingReplyTo|string|true|none|none|
|description|string|false|none|Less than 512 characters.|
|jobId|string|false|none|Less than 64 characters.|
|customFieldValues|[CustomFieldValues](#schemacustomfieldvalues)|false|none|none|

<h2 id="tocS_CustomFieldValues">CustomFieldValues</h2>
<!-- backwards compatibility -->
<a id="schemacustomfieldvalues"></a>
<a id="schema_CustomFieldValues"></a>
<a id="tocScustomfieldvalues"></a>
<a id="tocscustomfieldvalues"></a>

```json
[
  {
    "id": 0,
    "value": "string"
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|none|
|value|string|false|none|none|

<h2 id="tocS_PrivateInd">PrivateInd</h2>
<!-- backwards compatibility -->
<a id="schemaprivateind"></a>
<a id="schema_PrivateInd"></a>
<a id="tocSprivateind"></a>
<a id="tocsprivateind"></a>

```json
0

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int64)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|0|
|*anonymous*|1|

<h2 id="tocS_TypeInd">TypeInd</h2>
<!-- backwards compatibility -->
<a id="schematypeind"></a>
<a id="schema_TypeInd"></a>
<a id="tocStypeind"></a>
<a id="tocstypeind"></a>

```json
0

```

Valid values: 0 (audio), 1 (text), 2 (video)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int64)|false|none|Valid values: 0 (audio), 1 (text), 2 (video)|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|0|
|*anonymous*|1|
|*anonymous*|2|

<h2 id="tocS_SupportedLocaleId">SupportedLocaleId</h2>
<!-- backwards compatibility -->
<a id="schemasupportedlocaleid"></a>
<a id="schema_SupportedLocaleId"></a>
<a id="tocSsupportedlocaleid"></a>
<a id="tocssupportedlocaleid"></a>

```json
1

```

Valid values: 1 (en-US), 2 (es-ES), 3 (fr-CA)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int64)|false|none|Valid values: 1 (en-US), 2 (es-ES), 3 (fr-CA)|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|3|

<h2 id="tocS_InterviewQuestion">InterviewQuestion</h2>
<!-- backwards compatibility -->
<a id="schemainterviewquestion"></a>
<a id="schema_InterviewQuestion"></a>
<a id="tocSinterviewquestion"></a>
<a id="tocsinterviewquestion"></a>

```json
{
  "campaignId": 48372,
  "questionsToAdd": [
    483,
    484,
    494
  ]
}

```

An object with Interview Question details.

### Properties

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» questionsToAdd|[integer]|false|none|none|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» questionsToUpdate|[object]|false|none|none|
|»» id|integer(int64)|true|none|Id of question to update.|
|»» activeInd|integer(int64)|false|none|none|
|»» questionTextVisible|boolean|false|none|none|
|»» supportedLocale|integer(int64)|false|none|Id of locale.|
|»» orderNum|integer(int64)|false|none|Valid range is 1 up to number of total questions.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» questionsToDelete|[integer]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|activeInd|0|
|activeInd|1|

<h2 id="tocS_CandidateCall">CandidateCall</h2>
<!-- backwards compatibility -->
<a id="schemacandidatecall"></a>
<a id="schema_CandidateCall"></a>
<a id="tocScandidatecall"></a>
<a id="tocscandidatecall"></a>

```json
[
  {
    "pin": 293847,
    "dialInNumber": "412-555-2345"
  }
]

```

An object with candidate call in information.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pin|string|false|none|none|
|dialInNumber|string|false|none|none|

<h2 id="tocS_HarqenCall">HarqenCall</h2>
<!-- backwards compatibility -->
<a id="schemaharqencall"></a>
<a id="schema_HarqenCall"></a>
<a id="tocSharqencall"></a>
<a id="tocsharqencall"></a>

```json
{
  "campaignId": 1,
  "countryCode": "string",
  "areaCode": "string",
  "localNumber": "string"
}

```

An object with details to call candidate.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|countryCode|string|true|none|Less than 3 characters.|
|areaCode|string|true|none|none|
|localNumber|string|true|none|none|

<h2 id="tocS_InterviewSettings">InterviewSettings</h2>
<!-- backwards compatibility -->
<a id="schemainterviewsettings"></a>
<a id="schema_InterviewSettings"></a>
<a id="tocSinterviewsettings"></a>
<a id="tocsinterviewsettings"></a>

```json
{
  "campaignId": 1,
  "emailGreetingSubject": "string",
  "emailGreeting": "string",
  "emailGreetingSignature": "string",
  "inviteSms": "string",
  "emailGreetingReplyTo": "string",
  "interviewNowText": "string",
  "interviewNowSms": "string",
  "callInfoText": "string",
  "interviewCompleteText": "string",
  "redirectUrl": "string",
  "interviewCompleteSms": "string",
  "emailNextstepSubject": "string",
  "emailNextstepSignature": "string",
  "emailNextstep": "string",
  "prequalFailedText": "string",
  "failedRedirectUrl": "string",
  "prequalFailedSms": "string",
  "haltInterviewSms": "string",
  "haltInterviewText": "string",
  "sendRejectEmailInd": 0,
  "emailReject": "string",
  "emailRejectSignature": "string",
  "emailRejectSubject": "string",
  "sendAcceptEmailInd": 0,
  "emailAccept": "string",
  "emailAcceptSignature": "string",
  "emailAcceptSubject": "string",
  "reminder1Ind": 0,
  "reminder1Hours": 0,
  "reminder1EmailText": "string",
  "reminder2Ind": 0,
  "reminder2EmailText": "string",
  "reminder2Hours": 0
}

```

A JSON Object with Interview Settings.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|emailGreetingSubject|string|false|none|none|
|emailGreeting|string|false|none|none|
|emailGreetingSignature|string|false|none|none|
|inviteSms|string|false|none|none|
|emailGreetingReplyTo|string|false|none|none|
|interviewNowText|string|false|none|none|
|interviewNowSms|string|false|none|none|
|callInfoText|string|false|none|none|
|interviewCompleteText|string|false|none|NOTE: If `redirectUrl` has a non-blank value, this field will be ignored.|
|redirectUrl|string|false|none|none|
|interviewCompleteSms|string|false|none|none|
|emailNextstepSubject|string|false|none|none|
|emailNextstepSignature|string|false|none|none|
|emailNextstep|string|false|none|none|
|prequalFailedText|string|false|none|NOTE: If `failedRedirectUrl` has a non-blank value, this field will be ignored.|
|failedRedirectUrl|string|false|none|none|
|prequalFailedSms|string|false|none|none|
|haltInterviewSms|string|false|none|none|
|haltInterviewText|string|false|none|none|
|sendRejectEmailInd|integer|false|none|Valid values: 0 (do not send), 1 (send)|
|emailReject|string|false|none|NOTE: If `sendRejectEmailInd` is set to 1, this field is required.|
|emailRejectSignature|string|false|none|none|
|emailRejectSubject|string|false|none|none|
|sendAcceptEmailInd|integer|false|none|Valid values: 0 (do not send), 1 (send)|
|emailAccept|string|false|none|NOTE: If `sendAcceptEmailInd` is set to 1, this field is required.|
|emailAcceptSignature|string|false|none|none|
|emailAcceptSubject|string|false|none|none|
|reminder1Ind|integer|false|none|Valid values: 0 (do not remind), 1 (remind)|
|reminder1Hours|integer(int64)|false|none|NOTE: If `reminder1Ind` is set to 1, this field is required.|
|reminder1EmailText|string|false|none|NOTE: If `reminder1Ind` is set to 1, this field is required.|
|reminder2Ind|integer|false|none|Valid values: 0 (do not remind), 1 (remind)|
|reminder2EmailText|string|false|none|NOTE: If `reminder2Ind` is set to 1, this field is required.|
|reminder2Hours|integer(int64)|false|none|NOTE: If `reminder2Ind` is set to 1, this field is required.|

#### Enumerated Values

|Property|Value|
|---|---|
|sendRejectEmailInd|0|
|sendRejectEmailInd|1|
|sendAcceptEmailInd|0|
|sendAcceptEmailInd|1|
|reminder1Ind|0|
|reminder1Ind|1|
|reminder2Ind|0|
|reminder2Ind|1|

<h2 id="tocS_InterviewNow">InterviewNow</h2>
<!-- backwards compatibility -->
<a id="schemainterviewnow"></a>
<a id="schema_InterviewNow"></a>
<a id="tocSinterviewnow"></a>
<a id="tocsinterviewnow"></a>

```json
{
  "campaignId": 1,
  "requirePhoneNumberInd": 0,
  "requestPermissionToSmsInd": 0,
  "intNowResumeRequiredInd": -1
}

```

A JSON Object with Interview Settings.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|requirePhoneNumberInd|integer|false|none|Valid values: 0 (do not require), 1 (require)|
|requestPermissionToSmsInd|integer|false|none|Valid values: 0 (do not request), 1 (request). NOTE: If `requirePhoneNumberInd` is set to 1, this field is required.|
|intNowResumeRequiredInd|integer|false|none|Valid values: -1 (dont ask), 0 (optional), 1 (required)|

#### Enumerated Values

|Property|Value|
|---|---|
|requirePhoneNumberInd|0|
|requirePhoneNumberInd|1|
|requestPermissionToSmsInd|0|
|requestPermissionToSmsInd|1|
|intNowResumeRequiredInd|-1|
|intNowResumeRequiredInd|0|
|intNowResumeRequiredInd|1|

<h2 id="tocS_EmailNotification">EmailNotification</h2>
<!-- backwards compatibility -->
<a id="schemaemailnotification"></a>
<a id="schema_EmailNotification"></a>
<a id="tocSemailnotification"></a>
<a id="tocsemailnotification"></a>

```json
{
  "campaignId": 1,
  "userId": [
    1
  ]
}

```

A JSON Object with Email Notification data.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|userId|[integer]|false|none|none|

<h2 id="tocS_QualifyingQuestions">QualifyingQuestions</h2>
<!-- backwards compatibility -->
<a id="schemaqualifyingquestions"></a>
<a id="schema_QualifyingQuestions"></a>
<a id="tocSqualifyingquestions"></a>
<a id="tocsqualifyingquestions"></a>

```json
{
  "campaignId": 1,
  "qualifyingQuestionsToAdd": {
    "questionType": "yesOrNo",
    "questionText": "string",
    "requiredInd": 0,
    "expectedAnswerBoolean": true
  }
}

```

A JSON Object with Qualifying Questions details.

### Properties

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» qualifyingQuestionsToAdd|any|false|none|none|

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A yes or no Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» questionText|string|true|none|none|
|»»» requiredInd|integer|true|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerBoolean|boolean|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A number type Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» questionText|string|true|none|none|
|»»» requiredInd|integer|true|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerNum|integer(int64)|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» questionComparator|string|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A Qualifying Question with drop down list of answers.|
|»»» questionType|string|true|none|none|
|»»» questionText|string|true|none|none|
|»»» requiredInd|integer|true|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A multiple choice Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» questionText|string|true|none|none|
|»»» requiredInd|integer|true|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» allRequiredInd|integer|false|none|Whether all correct choices in `multiChoiceValues` will be required or not. Valid values: 0 (not required), 1 (required). Control of whether this field is required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|An open text answer Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» questionText|string|true|none|none|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» qualifyingQuestionsToUpdate|any|false|none|none|

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A yes or no Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» activeInd|integer|false|none|Whether this question is visible. Valid values: 0 (not active), 1 (active)|
|»»» questionText|string|false|none|none|
|»»» orderNum|integer|false|none|Valid values: 1 to total number of questions.|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerBoolean|boolean|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A number type Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» activeInd|integer|false|none|Whether this question is visible. Valid values: 0 (not active), 1 (active)|
|»»» questionText|string|false|none|none|
|»»» orderNum|integer|false|none|Valid values: 1 to total number of questions.|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerNum|integer(int64)|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» questionComparator|string|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A Qualifying Question with drop down list of answers.|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» activeInd|integer|false|none|Whether this question is visible. Valid values: 0 (not active), 1 (active)|
|»»» questionText|string|false|none|none|
|»»» orderNum|integer|false|none|Valid values: 1 to total number of questions.|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A multiple choice Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» activeInd|integer|false|none|Whether this question is visible. Valid values: 0 (not active), 1 (active)|
|»»» questionText|string|false|none|none|
|»»» orderNum|integer|false|none|Valid values: 1 to total number of questions.|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» allRequiredInd|integer|false|none|Whether all correct choices in `multiChoiceValues` will be required or not. Valid values: 0 (not required), 1 (required). Control of whether this field is required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|An open text answer Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» activeInd|integer|false|none|Whether this question is visible. Valid values: 0 (not active), 1 (active)|
|»»» questionText|string|false|none|none|
|»»» orderNum|integer|false|none|Valid values: 1 to total number of questions.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» qualifyingQuestionsToCopy|any|false|none|none|

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A yes or no Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» questionText|string|false|none|none|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerBoolean|boolean|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A number type Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» questionText|string|false|none|none|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» expectedAnswerNum|integer(int64)|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» questionComparator|string|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A Qualifying Question with drop down list of answers.|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» questionText|string|false|none|none|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|A multiple choice Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» questionText|string|false|none|none|
|»»» requiredInd|integer|false|none|Whether this question will be required or not. Valid values: 0 (not required), 1 (required)|
|»»» multiChoiceValues|[string]|false|none|Required or not is controlled by member field `requiredInd`.|
|»»» allRequiredInd|integer|false|none|Whether all correct choices in `multiChoiceValues` will be required or not. Valid values: 0 (not required), 1 (required). Control of whether this field is required or not is controlled by member field `requiredInd`.|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|An open text answer Qualifying Question|
|»»» questionType|string|true|none|none|
|»»» id|integer(int64)|true|none|none|
|»»» questionText|string|false|none|none|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» campaignId|integer(int64)|true|none|none|
|» qualifyingQuestionsToDelete|[integer]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|questionType|yesOrNo|
|requiredInd|0|
|requiredInd|1|
|questionType|number|
|requiredInd|0|
|requiredInd|1|
|questionComparator|equal|
|questionComparator|greaterThan|
|questionComparator|greaterThanOrEqual|
|questionComparator|lessThan|
|questionComparator|lessThanOrEqual|
|questionType|dropDownList|
|requiredInd|0|
|requiredInd|1|
|questionType|multipleChoiceCheckBoxes|
|requiredInd|0|
|requiredInd|1|
|allRequiredInd|0|
|allRequiredInd|1|
|questionType|openText|
|questionType|yesOrNo|
|activeInd|0|
|activeInd|1|
|requiredInd|0|
|requiredInd|1|
|questionType|number|
|activeInd|0|
|activeInd|1|
|requiredInd|0|
|requiredInd|1|
|questionComparator|equal|
|questionComparator|greaterThan|
|questionComparator|greaterThanOrEqual|
|questionComparator|lessThan|
|questionComparator|lessThanOrEqual|
|questionType|dropDownList|
|activeInd|0|
|activeInd|1|
|requiredInd|0|
|requiredInd|1|
|questionType|multipleChoiceCheckBoxes|
|activeInd|0|
|activeInd|1|
|requiredInd|0|
|requiredInd|1|
|allRequiredInd|0|
|allRequiredInd|1|
|questionType|openText|
|activeInd|0|
|activeInd|1|
|questionType|yesOrNo|
|requiredInd|0|
|requiredInd|1|
|questionType|number|
|requiredInd|0|
|requiredInd|1|
|questionComparator|equal|
|questionComparator|greaterThan|
|questionComparator|greaterThanOrEqual|
|questionComparator|lessThan|
|questionComparator|lessThanOrEqual|
|questionType|dropDownList|
|requiredInd|0|
|requiredInd|1|
|questionType|multipleChoiceCheckBoxes|
|requiredInd|0|
|requiredInd|1|
|allRequiredInd|0|
|allRequiredInd|1|
|questionType|openText|

<h2 id="tocS_CampaignAccess">CampaignAccess</h2>
<!-- backwards compatibility -->
<a id="schemacampaignaccess"></a>
<a id="schema_CampaignAccess"></a>
<a id="tocScampaignaccess"></a>
<a id="tocscampaignaccess"></a>

```json
{
  "campaignId": 1,
  "userIdsToAdd": [
    1
  ],
  "userIdsToDelete": [
    1
  ],
  "groupIdsToAdd": [
    1
  ],
  "groupIdsToDelete": [
    1
  ]
}

```

A JSON Object with access permissions data.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|userIdsToAdd|[integer]|false|none|none|
|userIdsToDelete|[integer]|false|none|none|
|groupIdsToAdd|[integer]|false|none|none|
|groupIdsToDelete|[integer]|false|none|none|

<h2 id="tocS_CampaignStatus">CampaignStatus</h2>
<!-- backwards compatibility -->
<a id="schemacampaignstatus"></a>
<a id="schema_CampaignStatus"></a>
<a id="tocScampaignstatus"></a>
<a id="tocscampaignstatus"></a>

```json
{
  "campaignId": 1,
  "activeInd": -1,
  "haltInterviewInd": 0
}

```

A JSON Object with status data.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|campaignId|integer(int64)|true|none|none|
|activeInd|integer|false|none|Valid values: -1 (removed), 0 (archived), 1 (active).|
|haltInterviewInd|integer|false|none|Valid values: 0 (do not halt), 1 (halt).|

#### Enumerated Values

|Property|Value|
|---|---|
|activeInd|-1|
|activeInd|0|
|activeInd|1|
|haltInterviewInd|0|
|haltInterviewInd|1|

<h2 id="tocS_CampaignSettings">CampaignSettings</h2>
<!-- backwards compatibility -->
<a id="schemacampaignsettings"></a>
<a id="schema_CampaignSettings"></a>
<a id="tocScampaignsettings"></a>
<a id="tocscampaignsettings"></a>

```json
{
  "allowAnswerAssessment": true,
  "allowAudioFallback": true,
  "campaignId": 1,
  "campaignName": "string",
  "clientBrandingId": 0,
  "departmentId": 0,
  "description": "string",
  "enableAutoCandidateWithdrawal": true,
  "enableMediaTranscription": true,
  "interviewColor": "string",
  "jobId": "string",
  "numBatchReviewHoldDays": 0,
  "ownerId": 1,
  "privateInd": 0,
  "typeInd": 0,
  "requestPermissionToSms": true,
  "supportedLocaleId": 1,
  "withdrawCandidatesDays": 0
}

```

A JSON Object with Campaign Settings.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|allowAnswerAssessment|boolean|false|none|none|
|allowAudioFallback|boolean|false|none|none|
|campaignId|integer(int64)|true|none|none|
|campaignName|string|false|none|Less than 512 characters.|
|clientBrandingId|integer(int64)|false|none|none|
|departmentId|integer(int64)|false|none|none|
|description|string|false|none|Less than 512 characters.|
|enableAutoCandidateWithdrawal|boolean|false|none|none|
|enableMediaTranscription|boolean|false|none|none|
|interviewColor|string|false|none|Color in hex codes.|
|jobId|string|false|none|Less than 64 characters.|
|numBatchReviewHoldDays|integer(int64)|false|none|Valid range is 0 to 20.|
|ownerId|integer(int64)|false|none|none|
|privateInd|[PrivateInd](#schemaprivateind)|false|none|none|
|typeInd|[TypeInd](#schematypeind)|false|none|Valid values: 0 (audio), 1 (text), 2 (video)|
|requestPermissionToSms|boolean|false|none|none|
|supportedLocaleId|[SupportedLocaleId](#schemasupportedlocaleid)|false|none|Valid values: 1 (en-US), 2 (es-ES), 3 (fr-CA)|
|withdrawCandidatesDays|integer(int64)|false|none|none|

