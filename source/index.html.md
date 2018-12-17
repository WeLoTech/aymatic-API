---
title: Aymatic Api Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  - javascript

toc_footers:
  - <a href='https://www.aymatic.com'>Contact us for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the aymatic API! You can use our API to access aymatic API endpoints, which can mainly create and update videos.

We have language bindings in Shell (cURL)! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentiion

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
```

> Make sure to replace `YOUR_KEY` with your API key.

aymatic uses API keys to allow access to the API. You can get a new aymatic API key in your [profile settings](https://app.aymatic.com/#/user-settings).

aymatic expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YOUR_KEY`

<aside class="notice">
You must replace <code>YOUR_KEY</code> with your personal API key.
</aside>
<aside class="notice">
videoID looks something like this: "1cd58e507b3e3d8bb8a9b2a3a5baa9988f741b8df83fa2e9e6b661d339fba904"
</aside>

# videos

## Get All videos


```shell
curl "https://app.aymatic.com/api/v1/videos?videoID"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let videos = api.videos.get(videoID);
```

> The above command returns JSON structured like this:

```json
[
  {"url":"https://www.aymatic.com/",
"keywords":["create emotional advertising videos from your content","easily explained","Supported on all platforms","Video marketing as easy and personal as a conversation.","Video Automation is not for everyon","you want to expand your existing online presence and stand out with video marketing, we offer the right solution.","Grow companies with videos"],
"images":["PROJECT_icon-G_S.4.png","PROJECT_icon-G_S.4.png","PROJECT_Aymatic-Logo-new.svg","PROJECT_avatar_user_3_1531505021-300x300.jpg",
"PROJECT_avatar_user_4_1532249024.png","PROJECT_Illustration-aymatic-erklaert.svg","PROJECT_facebook-1.svg"],
"music":"premium/Kaleidoscope by Ethan Rank - Awaken.mp3",
"imagelinks":["https://www.aymatic.com/wp-content/uploads/2018/09/icon-G_S.4.png","https://www.aymatic.com/wp-content/uploads/2018/09/icon-G_S.4.png","https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg","https://www.aymatic.com/wp-content/uploads/2018/07/avatar_user_3_1531505021-300x300.jpg","https://www.aymatic.com/wp-content/uploads/2018/07/avatar_user_4_1532249024.png","https://www.aymatic.com/wp-content/uploads/2018/09/Illustration-aymatic-erklaert.svg","https://www.aymatic.com/wp-content/uploads/2018/09/facebook-1.svg"],
"logo":"http://localhost:8080/src/uploadedImages/",
"colors":[[[0,0,0,1],[1,1,1,1]],[[0,0,0,1],[1,1,1,1]],[[0,0,0,1],[1,1,1,1]]]}
]
```

This endpoint retrieves all or one video(s).

### HTTP Request

`GET https://app.aymatic.com/v1/videos/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | If defined, the result will be the data from that specific video. Otherwise, the result will be all videos you own.

<aside class="success">
Remember — a happy Video is an authenticated Video!
</aside>
<aside class="notice">
videoID looks something like this: "1cd58e507b3e3d8bb8a9b2a3a5baa9988f741b8df83fa2e9e6b661d339fba904"
</aside>

## Delete a Specific Video


```shell
curl "https://app.aymatic.com/api/v1/videos/{videoID}"
  -X DELETE
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.videos.delete(videoID);
```

> The above command returns JSON structured like this:

```json
{
  "id": videoID,
  "deleted" : ":("
}
```

This endpoint deletes a specific Video.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/videos/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to delete

## Update a Specific Video

This endpoint updates a specific video.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/videos/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the Video to delete
data | The json that holds the information needed to update the video.

## Create a New Video

This endpoint creates a new video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos`

### Query Parameters

Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the video.




