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


# Authentication

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

# Videos


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

> The above command returns JSON structured like this if a video is specified:

```json
[
  {
  "url":"https://www.aymatic.com/",
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
<code>videoID</code> looks something like this: "1cd58e507b3e3d8bb8a9b2a3a5baa9988f741b8df83fa2e9e6b661d339fba904"
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
let max = api.videos.delete("videoID");
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
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
curl -X PUT -H "Authorization: YOUR_KEY", "Content-Type: application/json" \
--data '{
  "videoColor": "#3493B1",
  "music": "premium/Kaleidoscope by Ethan Rank - Awaken.mp3",
  "theme": "template2",
  "logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
  "thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
}' \
"https://app.aymatic.com/api/v1/videos/{videoID}"
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
let max = api.videos.update("videoID", body);
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
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

```shell
curl -X POST -H "Authorization: YOUR_KEY", "Content-Type: application/json" \
--data '{
  "theme": "blog",
  "template": "template0",
  "videoColor": "#4054B2",
  "imageSteps": ["https://kittenrescue.org/wp-content/uploads/2017/03/KittenRescue_KittenCareHandbook.jpg","https://www.thesprucepets.com/thmb/810a_HYIb2E8DxkedI6V-3gtkys=/450x0/filters:no_upscale():max_bytes(150000):strip_icc()/kitten-looking-at-camera-521981437-57d840213df78c583374be3b.jpg","http://images6.fanpop.com/image/photos/41500000/Kitten-cats-and-kittens-club-41536653-1280-853.jpg","https://www1.cbn.com/sites/default/files/styles/video_ratio_16_9/public/kittenas_hdv.jpg?itok=4nxmYAVy","https://www.scholastic.com/content/dam/teachers/Book%20List/2016-2017/kittens-book-list-4-3.jpg"],
  "textSteps" : ["The world is a dark place.", "My book is sitting next to me.", "Calculators are nifty.", "Shades are open.","Comes enjoy fresh soup.", "Welcome to our website!", "World's funniest joke."]
}' \
"https://app.aymatic.com/api/v1/videos/{projectKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "theme": "blog",
  "template": "template0",
  "videoColor": "#4054B2",
  "imageSteps": ["https://kittenrescue.org/wp-content/uploads/2017/03/KittenRescue_KittenCareHandbook.jpg","https://www.thesprucepets.com/thmb/810a_HYIb2E8DxkedI6V-3gtkys=/450x0/filters:no_upscale():max_bytes(150000):strip_icc()/kitten-looking-at-camera-521981437-57d840213df78c583374be3b.jpg","http://images6.fanpop.com/image/photos/41500000/Kitten-cats-and-kittens-club-41536653-1280-853.jpg","https://www1.cbn.com/sites/default/files/styles/video_ratio_16_9/public/kittenas_hdv.jpg?itok=4nxmYAVy","https://www.scholastic.com/content/dam/teachers/Book%20List/2016-2017/kittens-book-list-4-3.jpg"],
  "textSteps" : ["The world is a dark place.", "My book is sitting next to me.", "Calculators are nifty.", "Shades are open.","Comes enjoy fresh soup.", "Welcome to our website!", "World's funniest joke."]
}
let max = api.videos.create("projectKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "newVideoID",
  "projectKey": "projectKey"
}
```

This endpoint creates a new video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{projectKey}`

### Path parameters

Parameter | Description
--------- | -----------
projectKey | The ID of the project to add the video to.

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the video.


## Render a Video

```shell
curl -X POST -H "https://app.aymatic.com/api/v1/videos/{videoID}/render"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');

let max = api.videos.render("videoID");
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
  "wasAlreadyRendered": false,
  "isRendered": true,
  "videoDir": "app.aymatic.com/{videoID}.mp4"
}
```

This endpoint renders a video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/render`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to render

#Publishing

## Publish a Video to Facebook Page

curl -X POST -H "Authorization: YOUR_KEY", "Content-Type: application/json" \
--data '{
  "fbPageID": "YOUR_FACEBOOK_PAGE_ID",
  "fbUserId": "YOUR_FACEBOOK_USER_ID",
  "pageToken": "YOUR_FACEBOOK_PAGE_TOKEN"
}' \
"https://app.aymatic.com/api/v1/videos/{videoID}/publishFB"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "fbPageID": "YOUR_FACEBOOK_PAGE_ID",
  "fbUserId": "YOUR_FACEBOOK_USER_ID",
  "pageToken": "YOUR_FACEBOOK_PAGE_TOKEN"
};
let max = api.videos.publishFB("videoID", body);
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
  "postID": "postID"
}
```

This endpoint publishes a video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/publishFB`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to publish

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the video.

#Campaigns

## Get All or One Campaign(s)


```shell
curl "https://app.aymatic.com/api/v1/campaigns?campaignKey"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let campaigns = api.campaigns.get("campaignKey");
```

> The above command returns JSON structured like this if the campaignKey was defined as "61239a2b7877197e107b4a0ceb053288d77b9a243e57a46d66478d6bedd4b366":

```json
{
  "hasPushed" : false,
  "key" : "61239a2b7877197e107b4a0ceb053288d77b9a243e57a46d66478d6bedd4b366",
  "playerControls" : [ false, false, false, false, false, false ],
  "projects" : {
    "40496491030915177d818cb154b3e445faa77ac3989b94e1d6527591f92be846" : {
      "FBdata" : {
        "pageID" : "",
        "pageName" : "",
        "postID" : ""
      },
      "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
      "key" : "40496491030915177d818cb154b3e445faa77ac3989b94e1d6527591f92be846",
      "templateName" : "Cardealer-1-1",
      "title" : "Project 1",
      "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5",
      "views" : 0
    }
  },
  "title" : "Campaign 9",
  "type" : "blog",
  "videoColor" : "#ffffff",
  "videoIcon" : "",
  "videoPlayend" : "0",
  "videoPlaystart" : "0"
}
```

<notice>If campaignKey is not defined, the result will be all your campaigns.</notice>

This endpoint retrieves all or one campaign(s).

### HTTP Request

`GET https://app.aymatic.com/v1/campaigns/{campaignKey}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignKey | If defined, the result will be the data from that specific campaign. Otherwise, the result will be all campaigns you own.

<aside class="notice">
campaignKey looks something like this: "c5b4d78dc7f768afacbd288a621d9aab78d7b56f00dba2faaf3169857f782f69"
</aside>


## Delete a Campaign


```shell
curl "https://app.aymatic.com/api/v1/campaigns/{campaignKey}"
  -X DELETE
  -H "Authorization: "YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.campaigns.delete(campaignKey);
```

> The above command returns JSON structured like this:

```json
{
  "campaignKey": campaignKey,
  "deleted" : "true"
}
```

This endpoint deletes a specific campaign.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/campaigns/{campaignKey}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignKey | The ID of the campaign to delete


## Update a Campaign

```shell
curl -X PUT -H "Authorization: "YOUR_KEY", "Content-Type: application/json" \
--data '{
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoIcon": "",
  "videoPlayend": "3000",
  "videoPlaystart": "1000"
}' \
"https://app.aymatic.com/api/v1/campaigns/{campaignKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoIcon": "",
  "videoPlayend": "3000",
  "videoPlaystart": "1000"
}
let max = api.campaigns.update("campaignKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "campaignKey": "campaignKey",
  "updated" : "true"
}
```

This endpoint updates a specific campaign.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/campaigns/{campaignKey}`

### Path Parameters

Parameter | Description
--------- | -----------
campaignKey | The ID of the Campaign to delete

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the campaign.


## Create a New Campaign

```shell
curl -X POST -H "Authorization: "YOUR_KEY", "Content-Type: application/json" \
--data '{
{
  "type": "blog"
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoIcon": "",
  "videoPlayend": "3000",
  "videoPlaystart": "1000"
}
}' \
"https://app.aymatic.com/api/v1/campaigns"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "type": "blog"
  "title": "This is a wacky title!",
  "playerControls": [false,true,false,false,false,true],
  "videoColor": "#ffe25E",
  "videoIcon": "",
  "videoPlayend": "5000",
  "videoPlaystart": "2000"
}
let max = api.campains.create(body);
```

> The above command returns JSON structured like this:

```json
{
  "campaignKey": "newCampaignKey"
}
```

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
curl "https://app.aymatic.com/api/v1/projects/{projectKey}"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let projects = api.projects.get("projectKey");
```

> The above command returns JSON structured like this if a project is specified:

```json
[
  {
  "FBdata" : {
    "pageID" : "",
    "pageName" : "",
    "postID" : ""
  },
  "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
  "key" : "40496491030915177d818cb154b3e445faa77ac3989b94e1d6527591f92be846",
  "templateName" : "Cardealer-1-1",
  "title" : "Project 1",
  "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5",
  "views" : 0
  }

]
```

This endpoint retrieves all or one project(s).

### HTTP Request

`GET https://app.aymatic.com/v1/projects/{projectKey}`

### Path Parameters

Parameter | Description
--------- | -----------
projectKey | If defined, the result will be the data from that specific project. Otherwise, the result will be all projects you own.

<aside class="notice">
projectKey looks something like this: "1f4ec1ba91f1bdca16e39409c7849dbe25fae905247d46829a84151ca4f20d6e"
</aside>


## Delete a Project


```shell
curl "https://app.aymatic.com/api/v1/projects/{projectKey}"
  -X DELETE
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.projects.delete(projectKey);
```

> The above command returns JSON structured like this:

```json
{
  "projectKey": projectKey,
  "deleted" : "true"
}
```

This endpoint deletes a specific project.

### HTTP Request

`DELETE https://app.aymatic.com/api/v1/projects/{projectKey}`

### Path Parameters

Parameter | Description
--------- | -----------
projectKey | The ID of the project to delete


## Update a Project

```shell
curl -X PUT -H "Authorization: "YOUR_KEY", "Content-Type: application/json" \
--data '{
  "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
  "templateName" : "Cardealer-1-1",
  "title" : "Project 1",
  "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5"
}' \
"https://app.aymatic.com/api/v1/projects/{projectKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
  "templateName" : "Cardealer-1-1",
  "title" : "Project 1",
  "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5"
}
let max = api.projects.update("projectKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "projectKey": "projectKey",
  "updated" : "true"
}
```

This endpoint updates a specific project.

### HTTP Request

`PUT https://app.aymatic.com/api/v1/projects/{projectKey}`

### Path Parameters

Parameter | Description
--------- | -----------
projectKey | The ID of the project to delete

### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to update the project.


## Create a New Project

```shell
curl -X POST -H "Authorization: "YOUR_KEY", "Content-Type: application/json" \
--data '{
  "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
  "templateName" : "Cardealer-1-1",
  "title" : "Project 1",
  "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5"
}' \
"https://app.aymatic.com/api/v1/projects/{campaignKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "image" : "https://s3.eu-central-1.amazonaws.com/private-content.aymatic.com/src/videos/d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5/0c6c9df068da71c9fb1e200ca2309db83ce1bd4117cfdd1fd24f9327335d446d.jpeg",
  "templateName" : "Cardealer-1-1",
  "title" : "Project 1",
  "videoUUID" : "d9779427515e143e44b594cb7335b3f4e324bedeabe85c1fe31bea94cdc7c5d5"
}
let max = api.projects.create("campaignKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "projectKey": "newProjectKey",
}
```

This endpoint creates a new project.

### HTTP Request

`POST https://app.aymatic.com/api/v1/projects/{campaignKey}`

### Query parameters
Parameter | Description
--------- | -----------
campaignKey | The ID of the campaign at which the project should be created in.
### Request body parameters
Parameter | Description
--------- | -----------
data | The json that holds the information needed to create the project.


#Templates

## Get Templates

```shell
curl "https://app.aymatic.com/api/v1/templates/{theme}"
  -X GET
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.templates.get("theme");
```

> The above command returns JSON structured like this if theme is defined to be "blog":

```json
{
  
  "template2" : {
    "description" : "Aymatic's handgefertigte Fahrzeug Video-Vorlage",
    "id" : 2,
    "imageSteps" : [ "Auto vorne", "Auto hinten", "Auto Reifen", "Auto innen", "Auto detail 1", "Auto vorne", "Logo oder Mitarbeiter" ],
    "isCustom" : false,
    "isPremium" : false,
    "name" : "Vorlage Auto Günther",
    "textSteps" : [ "Auto Name", "Fahrzeugtyp", "Getriebe", "Motor", "Verbrauch", "Preis", "Kontakt" ],
    "type" : "Cardealer-1-1"
  },
  "template3" : {
    "description" : "Aymatics's \"Steinhart und Kraus\"-Vorlage",
    "id" : 3,
    "imageSteps" : [ "Auto vorne", "Auto hinten", "Auto innen", "Auto innen detail 1", "Auto innen detail 2", "Auto seitlich" ],
    "isCustom" : false,
    "isPremium" : false,
    "name" : "Vorlage S&K Autohaus",
    "textSteps" : [ "Auto Name", "Fahrzeugtyp", "Getriebe", "Motor", "Verbrauch (ohne L/100)", "Preis", "Kontakt" ],
    "type" : "Cardealer-2-3"
  }
  
  
}

```

This endpoint returns the templates that you can use.

<notice>Notice how only the templates that are not premium get returned.
This user does not have premium status and therefore is not allowed to view the premium templates.</notice>

### HTTP Request

`GET https://app.aymatic.com/api/v1/templates/{theme}`

### Path Parameters

Parameter | Description
--------- | -----------
theme | The type of templates you want. Blog, Email, or Product. If not defined, the result will be all of them.


#Insights

## Get Video Insights


```shell
curl "https://app.aymatic.com/api/v1/insights/{videoID}"
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let insights = api.insights.get("videoID");
```

> The above command returns JSON structured like this:

```json
{
   "views" : 0,
   "likes" : 0
}
```

This endpoint retrieves insights about a specific video.

### HTTP Request

`GET https://app.aymatic.com/v1/insights/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to gain insights from.






