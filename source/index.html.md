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


## Get All or One Video(s)


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
Remember — a happy video is an authenticated video!
</aside>
<aside class="notice">
videoID looks something like this: "1cd58e507b3e3d8bb8a9b2a3a5baa9988f741b8df83fa2e9e6b661d339fba904"
</aside>


## Delete a Video


```shell
curl "https://app.aymatic.com/api/v1/videos/{videoID}"
  -X DELETE
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.videos.delete('1cd58e507b3e3d8bb8a9b2a3a5...');
```

> The above command returns JSON structured like this:

```json
{
  "id": '1cd58e507b3e3d8bb8a9b2a3a5...',
  "deleted" : "true"
}
```

This endpoint deletes a specific video.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/videos/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to delete


## Update a Video

```shell
curl -X PUT -H "Content-Type: application/json" \
--data '{
"videoColor": "#3493B1",
"music": "premium/Kaleidoscope by Ethan Rank - Awaken.mp3",
"theme": "template2",
"logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
"thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
}' \
"https://app.aymatic.com/api/v1/videos/1cd58e507b3e3d8bb8a9b2a3a5..."
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
"videoColor": "#3493B1",
"music": "premium/Kaleidoscope by Ethan Rank - Awaken.mp3",
"theme": "template2",
"logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
"thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
}
let max = api.videos.update('1cd58e507b3e3d8bb8a9b2a3a5...', body);
```

> The above command returns JSON structured like this:

```json
{
  "id": "1cd58e507b3e3d8bb8a9b2a3a5...",
  "updated" : "true"
}
```

This endpoint updates a specific video.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/videos/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to delete

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the video.


## Create a New Video

This endpoint creates a new video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{projectID}`

### Path parameters

Parameter | Description
--------- | -----------
projectID | The ID of the project to add the video to.

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the video.


## Render a Video

This endpoint renders a video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/render`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to render


## Publish a Video

This endpoint publishes a video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/publish`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to render

### Query parameters

Parameter | Description
--------- | -----------
provider | What platform you want to publish your video to. e.g. 'facebook', 'instagram', etc...


#Campaigns

## Get All or One Campaign(s)


```shell
curl "https://app.aymatic.com/api/v1/campaigns?campaignID"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let campaigns = api.campaigns.get(campaignID);
```

> The above command returns JSON structured like this:

```json
[
  
]
```

This endpoint retrieves all or one campaign(s).

### HTTP Request

`GET https://app.aymatic.com/v1/campaigns/{campaignID}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignID | If defined, the result will be the data from that specific campaign. Otherwise, the result will be all campaigns you own.

<aside class="notice">
campaignID looks something like this: "c5b4d78dc7f768afacbd288a621d9aab78d7b56f00dba2faaf3169857f782f69"
</aside>


## Delete a Campaign


```shell
curl "https://app.aymatic.com/api/v1/campaigns/{campaignID}"
  -X DELETE
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.campaigns.delete(campaignID);
```

> The above command returns JSON structured like this:

```json
{
  "id": campaignID,
  "deleted" : ":("
}
```

This endpoint deletes a specific campaign.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/campaigns/{campaignID}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignID | The ID of the campaign to delete


## Update a Campaign

This endpoint updates a specific campaign.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/campaigns/{campaignID}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignID | The ID of the Campaign to delete

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the campaign.


## Create a New Campaign

This endpoint creates a new campaign.

### HTTP Request

`POST https://app.aymatic.com/api/v1/campaigns`

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the campaign.


#Projects

## Get All or One Project(s)


```shell
curl "https://app.aymatic.com/api/v1/projects?projectID"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let projects = api.projects.get(projectID);
```

> The above command returns JSON structured like this:

```json
[
  
]
```

This endpoint retrieves all or one project(s).

### HTTP Request

`GET https://app.aymatic.com/v1/projects/{projectID}`

### Path Parameters

Parameter | Description
--------- | -----------
projectID | If defined, the result will be the data from that specific project. Otherwise, the result will be all projects you own.

<aside class="notice">
projectID looks something like this: "1f4ec1ba91f1bdca16e39409c7849dbe25fae905247d46829a84151ca4f20d6e"
</aside>


## Delete a Project


```shell
curl "https://app.aymatic.com/api/v1/projects/{projectID}"
  -X DELETE
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.projects.delete(projectID);
```

> The above command returns JSON structured like this:

```json
{
  "id": projectID,
  "deleted" : ":("
}
```

This endpoint deletes a specific project.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/projects/{projectID}`

### Path Parameters

Parameter | Description
--------- | -----------
projectID | The ID of the project to delete


## Update a Project

This endpoint updates a specific project.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/projects/{projectID}`

### Path Parameters

Parameter | Description
--------- | -----------
projectID | The ID of the project to delete

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the project.


## Create a New Project

This endpoint creates a new project.

### HTTP Request

`POST https://app.aymatic.com/api/v1/projects`

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the project.




