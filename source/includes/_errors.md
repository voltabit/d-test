# Errors

The Phone Number Storer API uses the following error codes:

Error Code | Error Name | Meaning
---------- | ------- | -------
400 | Bad Request | Your request is invalid.
401 | Unauthorized | Your API key is wrong.
403 | Forbidden | The phone number requested is hidden for administrators only.
404 | Not Found | The specified phone number could not be found.
405 | Method Not Allowed | You tried to access a phone number with an invalid method.
406 | Not Acceptable | You requested a format that isn't json.
410 | Gone | The phone number requested has been removed from our servers.
429 | Too Many Requests | You're making too many requests! Slow down!
500 | Internal Server Error | We had a problem with our server. Try again later.
503 | Service Unavailable | We're temporarily offline for maintenance. Please try again later.
1010 | Invalid phone number | The phone number you provided is not valid.
1011 | Phone number exists | You are trying to add phone number that already exists in your phone book.