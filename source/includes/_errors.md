# Errors

<!-- <aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside> -->

The Contextgrid API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks.
403 | Forbidden -- The API requested is Unauthorized.
404 | Not Found -- The specified API could not be found.
405 | Method Not Allowed -- You tried to access a beacon with an invalid method.
406 | Not Acceptable -- You requested a format not valid.
500 | Internal Server Error -- We had a problem with our server. Try again later.
