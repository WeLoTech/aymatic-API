# Errors

<aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside>

The Aymatic API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The method requested is hidden for administrators only.
404 | Not Found -- The specified method could not be found.
405 | Method Not Allowed -- You tried to access media with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The media requested has been removed from our servers.
418 | Lacking permissions -- You do not have proper permissions to use this method.
420 | Not Yours -- The media you are trying to access is not yours.
429 | Too Many Requests -- You're calling too many methods! Slow down!
440 | Lacking Provider Credentials -- You need to authorize before using that provider.
454 | Incorrect arguements -- The arguements given were not what the method wanted. Please double check what you gave.
500 | Internal Server Error -- Someone's getting fired. We had a problem with our server! Try again later. 
503 | Service Unavailable -- Shhh, we're closed. Server is temporarily offline for maintenance. Please try again later.
