---
title:  SymboTalk API - Search free AAC Symbols

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - ruby
  - python
  - php

toc_footers:
  # - <a href=#>Sign Up for a Developer Key</a>
  - <a href=http://onelink.to/symbotalkapp>Download SymboTalk</a>
  - <a href=https://github.com/lord/slate>Documentation Powered by Slate</a>

includes:
- errors

search: true
---

# Introduction

Welcome to the SymboTalk API! You can use our API to search free AAC symbols at you app or website.

SymboTalk API has a database of more the 28,000 professional symbols sets, translated to 23 languages. 
The symbols are from: <a href="http://www.arasaac.org/" target="_blank">ARASAAC</a>, <a href="http://www.sclera.be/en/vzw/home" target="_blank">Sclera</a>, <a href="http://straight-street.com/gallery.php" target="_blank">Straight Street</a> and <a href="http://tawasolsymbols.org/en/home/" target="_blank">Tawasol</a>



You can see a live exapmle of the API <a href="https://elelad.github.io/SymboTalkAPIExample/" target="_blank">here</a>. 

SymboTalk API inspired by <a href="https://www.opensymbols.org/" target"_blank">OpenSymbols</a>






# Symbols

## Search symbols

```javascript
var request = require("request");

var options = { method: GET,
  url: https://symbotalkapiv1.azurewebsites.net/search/,
  qs: { name: school, lang: en, repo: all, limit: 10 },
  headers: 
   { Cache-Control: no-cache } 
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```ruby
require uri
require net/http

url = URI("https://symbotalkapiv1.azurewebsites.net/search/?name=school&lang=en&repo=all&limit=10")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Cache-Control"] = no-cache

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://symbotalkapiv1.azurewebsites.net/search/"

querystring = {"name":"school","lang":"en","repo":"all","limit":"10"}

headers = {
    Cache-Control: "no-cache"
    }

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```php
<?php

$request = new HttpRequest();
$request->setUrl(https://symbotalkapiv1.azurewebsites.net/search/);
$request->setMethod(HTTP_METH_GET);

$request->setQueryData(array(
  name => school,
  lang => en,
  repo => all,
  limit => 10
));

$request->setHeaders(array(
  Cache-Control => no-cache
));

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
```



> The above command returns an array of [Symbol Object](#symbol-object) 



This endpoint retrieves a symbols array based on the query parameters.

<!-- <aside class="warning"></aside> -->

### HTTP Request

`GET https://symbotalkapiv1.azurewebsites.net/search/?name=school&lang=en&repo=all&limit=10`

### URL Parameters

Parameter | Default | Allowed values | Description
--------- | ------- | ----------- | -----------
name | null | any | The symbol name you want to search.
lang | en | en, fi, el, ro, sk, iw, fr, de, es, pt, ru, ja, sv, nl, da, hu, pl, no, ko, th, tr, cs, ar | The language of the search. the retruned json will contain a translation to this laguage.
repo | all | all, arasaac, sclera, mulberry, tawasol | The symbols set you want to search at.
limit | 20 | any number smaller then 50 | The number of results to retrun.


<aside class="notice">
If you provide unapproved values or null for: lang, repo or limit - they will fall back to the defult value.
</aside>



## Get one Symbol

```javascript
var request = require("request");

var options = { method: GET,
  url: https://symbotalkapiv1.azurewebsites.net/symbols/20,
  headers: 
   { Cache-Control: no-cache } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```ruby
require uri
require net/http

url = URI("https://symbotalkapiv1.azurewebsites.net/symbols/20")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Cache-Control"] = no-cache

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://symbotalkapiv1.azurewebsites.net/symbols/20"

headers = {
    Cache-Control: "no-cache"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```php
<?php

$request = new HttpRequest();
$request->setUrl(https://symbotalkapiv1.azurewebsites.net/symbols/20);
$request->setMethod(HTTP_METH_GET);

$request->setHeaders(array(
  Postman-Token => c28f9b2b-c226-4257-8cc9-126bdc06646c,
  Cache-Control => no-cache
));

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
```



> The above command returns JSON of [Symbol Object](#symbol-object)


This endpoint retrieves one symbol by id.

### HTTP Request

`GET https://symbotalkapiv1.azurewebsites.net/symbols/:id`

### Request Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | null | The id of the symbol you want to retrun.


<!-- <aside class="success">
When  you use 
</aside> -->

# Symbol Object
> Symbol object structured like this:

```json
{
    "_id": "5adf6908795ba3078dc96444",
    "id": 20,
    "name": "5 euros",
    "license": "CC BY-NC-SA",
    "license_url": "http://creativecommons.org/licenses/by-nc-sa/3.0/",
    "author": "Sergio Palao",
    "author_url": "http://www.catedu.es/arasaac/condiciones_uso.php",
    "repo_key": "arasaac",
    "image_url": "https://storage.googleapis.com/symbols/arasaac/5 euros.png",
    "alt_url": "https://d18vdu4p71yql0.cloudfront.net/libraries/arasaac/5 euros.png",
    "translations": [{ "tLang": "en", "tName": "5 euros"},
        {"tLang": "iw","tName": "5 €"},
        {"tLang": "fr","tName": "5 euros"},
        {"tLang": "de","tName": "5 Euro"},
        {"tLang": "es","tName": "5 euros"},
        {"tLang": "pt","tName": "5 euros"},
        {"tLang": "ru","tName": "5 евро"},
        {"tLang": "ja","tName": "5ユーロ"},
        {"tLang": "sv","tName": "5 euro"},
        {"tLang": "nl","tName": "5 euro"},
        {"tLang": "da","tName": "5 euro"},
        {"tLang": "hu","tName": "5 euró"},
        {"tLang": "pl","tName": "5 euro"},
        {"tLang": "no","tName": "5 euro"},
        {"tLang": "ko","tName": "5 유로"},
        {"tLang": "th","tName": "5 ยูโร"},
        {"tLang": "tr","tName": "5 avro"},
        {"tLang": "cs","tName": "5 eur"},
        {"tLang": "ar","tName": "5 يورو"},
        {"tLang": "sk","tName": "5 EUR"},
        {"tLang": "fi","tName": "5 euroa"},
        {"tLang": "el","tName": "5 ευρώ"},
        {"tLang": "ro","tName": "5 euro"}]
}
```



All get requaest retrun Symbol object with this fields:

  - _id: The DB entry id. 
  - id: The Symbol id.
  - name: Symbol name.
  - license: The license of the symbol as defind by his auther.
  - license_url: More data about the license.
  - author: The creator of the symbol. 
  - author_url: The creator website.
  - repo_key: The name of the symbols set. 
  - image_url: The url of the symbol image. 
  - alt_url: Alternative image url. 
  - translations: The translations fo the symbol name. 

<aside class="notice">
When you requaest one symbol the symbol retruned will contain all translations. if you search, the symbol retruned will contain only the translation for the search language.
</aside>






# Authentication

<aside class="success">
SymboTalk API is open without authentication or cors restrictions.
</aside>