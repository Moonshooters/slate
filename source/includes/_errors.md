# HTTP Error Codes

The FindEmails API returns the following HTTP status codes for faulty queries:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- There was a problem with your API key.
404 | Not Found -- The resource you requested could not be found.
406 | Not Acceptable -- You requested a format that isn't compatible with our API.
500 | Internal Server Error -- We had an unexpected problem with your request.
