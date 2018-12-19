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

The first thing you probably will want to do is create a video. Here is a brief overview of our structure and what you will need to do first.

Campaign -> Videos

1. Create a campaign
2. Create a video in that campaign.

<aside class="warning">You cannot create a video unless you have a campaign to put it in.</aside>

AUTO means that you can define the variable, but if you don't, we will choose it for you.

NECESSARY means that you do need to define the variable, otherwise, it will throw an error.

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
  "videoUUID":"1cd58e507b3e3d8bb8a9b2a3a5baa9988f741b8df83fa2e9e6b661d339fba904",
  "videoColor":"#ffffff",
  "title":"My first video",
  "template":"Cardealer-1-1",
  "facebook":{
    postID:""
  }
  "instagram"{
    ...
  }
  "youtube"{
    ...
  }
  "url":"https://www.aymatic.com/",
  "keywords":["create emotional advertising videos from your content","easily explained","Supported on all platforms","Video marketing as easy and personal as a conversation.","Video Automation is not for everyon","you want to expand your existing online presence and stand out with video marketing, we offer the right solution.","Grow companies with videos"],
  "images":["PROJECT_icon-G_S.4.png","PROJECT_icon-G_S.4.png","PROJECT_Aymatic-Logo-new.svg","PROJECT_avatar_user_3_1531505021-300x300.jpg",
  "PROJECT_avatar_user_4_1532249024.png","PROJECT_Illustration-aymatic-erklaert.svg","PROJECT_facebook-1.svg"],
  "music":"premium/Kaleidoscope by Ethan Rank - Awaken.mp3",
  "imagelinks":["https://www.aymatic.com/wp-content/uploads/2018/09/icon-G_S.4.png","https://www.aymatic.com/wp-content/uploads/2018/09/icon-G_S.4.png","https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg","https://www.aymatic.com/wp-content/uploads/2018/07/avatar_user_3_1531505021-300x300.jpg","https://www.aymatic.com/wp-content/uploads/2018/07/avatar_user_4_1532249024.png","https://www.aymatic.com/wp-content/uploads/2018/09/Illustration-aymatic-erklaert.svg","https://www.aymatic.com/wp-content/uploads/2018/09/facebook-1.svg"],
  "logo":"http://localhost:8080/src/uploadedImages/",
  }
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
  "successful" : "true"
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
  "music": "Kaleidoscope by Ethan Rank - Awaken.mp3",
  "title":"My second video",
  "template":"Cardealer-1-1",
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
  "title":"My second video",
  "template":"Cardealer-1-1",
  "music": "Kaleidoscope by Ethan Rank - Awaken.mp3",
  "logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
  "thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
}
let max = api.videos.update("videoID", body);
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
  "successful" : "true"
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
videoColor | The color that the video's UI should be.
title | The name of the video.
template | How the video uses the images. 
music | The song that plays when the video starts.
logo | The video's designated logo. Used for branding.
thumbnail | The image that appears when the video hasn't been played yet.

<notice>Anything not added to the body of the request will not be modified. You don't need to change everything.</notice>

## Create a New Video

```shell
curl -X POST -H "Authorization: YOUR_KEY", "Content-Type: application/json" \
--data '{
  "title": "My new video",
  "template": "template0",
  "videoColor": "#4054B2",
  "music": "Kaleidoscope by Ethan Rank - Awaken.mp3",
  "logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
  "thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
  "imageSteps": ["https://kittenrescue.org/wp-content/uploads/2017/03/KittenRescue_KittenCareHandbook.jpg","https://www.thesprucepets.com/thmb/810a_HYIb2E8DxkedI6V-3gtkys=/450x0/filters:no_upscale():max_bytes(150000):strip_icc()/kitten-looking-at-camera-521981437-57d840213df78c583374be3b.jpg","http://images6.fanpop.com/image/photos/41500000/Kitten-cats-and-kittens-club-41536653-1280-853.jpg","https://www1.cbn.com/sites/default/files/styles/video_ratio_16_9/public/kittenas_hdv.jpg?itok=4nxmYAVy","https://www.scholastic.com/content/dam/teachers/Book%20List/2016-2017/kittens-book-list-4-3.jpg"],
  "textSteps" : ["The world is a dark place.", "My book is sitting next to me.", "Calculators are nifty.", "Shades are open.","Comes enjoy fresh soup.", "Welcome to our website!", "World's funniest joke."]
}' \
"https://app.aymatic.com/api/v1/videos/{campaignKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "title": "My new video",
  "template": "template0",
  "videoColor": "#4054B2",
  "music": "Kaleidoscope by Ethan Rank - Awaken.mp3",
  "logo": "https://www.aymatic.com/wp-content/uploads/2018/05/Aymatic-Logo-new.svg",
  "thumbnail": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Kitten_in_Rizal_Park%2C_Manila.jpg/230px-Kitten_in_Rizal_Park%2C_Manila.jpg"
  "imageSteps": ["https://kittenrescue.org/wp-content/uploads/2017/03/KittenRescue_KittenCareHandbook.jpg","https://www.thesprucepets.com/thmb/810a_HYIb2E8DxkedI6V-3gtkys=/450x0/filters:no_upscale():max_bytes(150000):strip_icc()/kitten-looking-at-camera-521981437-57d840213df78c583374be3b.jpg","http://images6.fanpop.com/image/photos/41500000/Kitten-cats-and-kittens-club-41536653-1280-853.jpg","https://www1.cbn.com/sites/default/files/styles/video_ratio_16_9/public/kittenas_hdv.jpg?itok=4nxmYAVy","https://www.scholastic.com/content/dam/teachers/Book%20List/2016-2017/kittens-book-list-4-3.jpg"],
  "textSteps" : ["The world is a dark place.", "My book is sitting next to me.", "Calculators are nifty.", "Shades are open.","Comes enjoy fresh soup.", "Welcome to our website!", "World's funniest joke."]
}
let max = api.videos.create("campaignKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "newVideoID",
  "campaignKey": "campaignKey",
  "successful": true
}
```

This endpoint creates a new video.

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{campaignKey}`

### Path parameters

Parameter | Description
--------- | -----------
campaignKey | The ID of the campaign to add the video to.

### Request body parameters
Parameter | Default | Description
--------- | ------- | -----------
videoColor | #4054B2 | The color that the video's UI should be.
title | NECESSARY | The name of the video.
template | NECESSARY | How the video uses the images. 
music | AUTO | The song that plays when the video starts.
thumbnail | AUTO | The image that appears when the video hasn't been played yet.
imageSteps | NECESSARY | The images that you want the video to use.
textSteps | NECESSARY | The text that you want the video to use.

<aside class="warning">You need to make sure that the textSteps and imageSteps abide by the rules of the template you are using. If the template calls for 5 textSteps you need to give exactly 5 textSteps. Otherwise, it will throw an error.</aside>

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

##Publish a Video to Facebook

```shell
curl -X POST -H "Authorization: YOUR_KEY" "https://app.aymatic.com/api/v1/videos/{videoID}/publish/facebook"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');

let max = api.videos.publish.facebook("videoID");
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
  "successful": true,
  "postData":{

  }
}
```

This endpoint publishes a video to facebook.

<notice>Post data will just be whatever your provider sends back after posting.</notice>

<aside class="warning">You need to be authorized and logged in before making any publications. Please log in for your provider on our website.</aside>

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/publish/facebook`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to publish

##Publish a Video to Youtube

```shell
curl -X POST -H "Authorization: YOUR_KEY" "https://app.aymatic.com/api/v1/videos/{videoID}/publish/youtube"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');

let max = api.videos.publish.youtube("videoID");
```

> The above command returns JSON structured like this:

```json
{
  "videoID": "videoID",
  "successful": true,
  "postData":{

  }
}
```

This endpoint publishes a video to youtube.

<notice>Post data will just be whatever your provider sends back after posting.</notice>

<aside class="warning">You need to be authorized and logged in before making any publications. Please log in for your provider on our website.</aside>

### HTTP Request

`POST https://app.aymatic.com/api/v1/videos/{videoID}/publish/youtube`

### Path parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to publish

#Campaigns

## Get All or One Campaign(s)

```shell
curl "https://app.aymatic.com/api/v1/campaigns/{campaignKey}"
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
  "facebook":{
    "pageID":""
  }
  "instagram":{
    ...
  }
  "youtube":{
    ...
  }
  "platforms":["youtube","facebook"],
  "videos":["9988f741b8df8339fba9041cd58e507b3e3d8bb8a9b2a3a5baafa2e9e6b661d3", "7b3e3d8bb8a9b2a9988f741b8df8339fba9041cd58e503a5baafa2e9e6b661d3"],
  "hasPushed" : false,
  "key" : "61239a2b7877197e107b4a0ceb053288d77b9a243e57a46d66478d6bedd4b366",
  "playerControls" : [ false, false, false, false, false, false ],
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
  "successful" : "true"
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
  "facebook":{
    "pageID":""
  }
  "instagram":{
    ...
  }
  "youtube":{
    ...
  }
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoLogo": "",
  "platforms":["facebook"],
  "url": "https://www.aymatic.com/",
  "templates": ["template0","template1","template2"]
}' \
"https://app.aymatic.com/api/v1/campaigns/{campaignKey}"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let body = {
  "facebook":{
    "pageID":""
  }
  "instagram":{
    ...
  }
  "youtube":{
    ...
  }
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoLogo": "",
  "platforms":["facebook"],
  "url": "https://www.aymatic.com/",
  "templates": ["template0","template1","template2"]
}
let max = api.campaigns.update("campaignKey", body);
```

> The above command returns JSON structured like this:

```json
{
  "campaignKey": "campaignKey",
  "successful" : "true"
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
videoColor | The color that the video's UI should be.
title | The name of the video.
facebook | The data that is required to know what page you want your videos published to in facebook.
youtube | The data that is required to know where you want your videos published to in youtube.
instagram | The data that is required to know where you want you videos published to in instragram.
platforms | The platforms that you want your videos to automatically be posted to.
playerControls | The controls the video should have.
templates | List of ways that the videos should use the images.
url | The url of your website.
videoLogo | The logo used for branding on the video.

## Create a New Campaign

```shell
curl -X POST -H "Authorization: "YOUR_KEY", "Content-Type: application/json" \
--data '{
{
  "type": "blog"
  "title": "This is a new wacky title!",
  "playerControls": [false,false,false,true,false,true],
  "videoColor": "#72D85E",
  "videoLogo": "",
  "url": "https://www.aymatic.com/",
  "templates": ["template0","template1","template2"]
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
  "videoLogo": "",
  "url": "https://www.aymatic.com/",
  "templates": ["template0","template1","template2"]
}
let max = api.campains.create(body);
```

> The above command returns JSON structured like this:

```json
{
  "campaignKey": "newCampaignKey",
  "successful": true
}
```

This endpoint creates a new campaign.

### HTTP Request

`POST https://app.aymatic.com/api/v1/campaigns`

### Request body parameters
Parameter | Default | Description
--------- | ------- | -----------
type | NECESSARY | What kind of video is this? blog, product, or email?
videoColor | #4054B2 | The color that the video's UI should be.
title | NECESSARY | The name of the video.
playerControls | AUTO | The controls the video should have.
templates | NECESSARY | List of ways that the videos should use the images.
url | NECESSARY | The url of your website.
videoLogo | AUTO | The logo used for branding on the video.


#Templates and Music

## Get Templates

```shell
curl "https://app.aymatic.com/api/v1/templates/{type}"
  -X GET
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.templates.get("type");
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

## Get Music

```shell
curl "https://app.aymatic.com/api/v1/music"
  -X GET
  -H "Authorization: YOUR_KEY"
```

```javascript
const aymatic = require('aymatic');

let api = aymatic.authorize('YOUR_KEY');
let max = api.music.get();
```

> The above command returns JSON structured like this:

```json
{
  "premium" : [ "A Good Mood by Young Rich Pixies.mp3", "A Look Out by Appearing.mp3", "Altitude by Muted.mp3", "Atlas by Ethan Rank - Silent Dreams.mp3" ],
  "standard" : [ "All_This_Down_Time.mp3", "Big_Sky.mp3", "Friendly Ukulele.mp3", "GoPro Video FREE.mp3", "Higher.mp3", "Indie_Inspiring_Stirring.mp3", "Inspirational Life.mp3", "Inspiring Ambient.mp3", "On_the_Tip.mp3", "Pooka.mp3", "Sweet Ukulele.mp3" ]
}
```

This endpoint returns the music that you can use.

<notice>This is a premium user. He is allowed to see the premium songs.</notice>

### HTTP Request

`GET https://app.aymatic.com/api/v1/music`

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
   "likes" : 0,
   "plays" : 0
}
```

This endpoint retrieves insights about a specific video.

### HTTP Request

`GET https://app.aymatic.com/v1/insights/{videoID}`

### Path Parameters

Parameter | Description
--------- | -----------
videoID | The ID of the video to gain insights from.






