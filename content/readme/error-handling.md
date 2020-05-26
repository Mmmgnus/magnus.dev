---
title: "Error Handling"
date: 2020-04-15T18:22:00+02:00
draft: false
Intro: The goal of Error codes is to communicate ***what***, and ***why*** something went wrong.
---

- Errors need to be readable by both computers and humans.
- Error codes must give context to the problem.

## Good Error Code
Error codes should contain:

- An HTTP Status Code, so that the source and realm of the problem can be ascertained with ease;
- An Internal Reference ID for documentation-specific notation of errors. In some cases, this can replace the HTTP Status Code, as long as the internal reference sheet includes the HTTP Status Code scheme or similar reference material.
- Human readable messages that summarize the context, cause, and general solution for the error at hand.

I really like the structure Bing and the [RFC7807 standard](https://tools.ietf.org/html/rfc7807) uses, they use a link for the user to find out more information on how to solve the problem.

**Bing has `help_link`:**
```json
{
	"Errors":[{
		"Code": 1001,
		"Message":"Required parameter is missing.",
		"Parameter": "SearchRequest.AppId",
		"HelpUrl":"http\u003a\u002f\u002fmsdn.microsoft.com\u002fen-us\u002flibrary\u002fdd251042.aspx"
	}]
}
```

**And, RFC7807 uses URI as the `type`:**
```json
{
	"type": "https://example.com/probs/out-of-credit",
	"title": "You do not have enough credit.",
	"detail": "Your current balance is 30, but that costs 50.",
	"instance": "/account/12345/msgs/abc",
	"balance": 30,
	"accounts": [
		"/account/12345",
		"/account/67890"    
	]
}
```

## Links
- https://medium.com/@iaincollins/error-handling-in-javascript-a6172ccdf9af
- https://levelup.gitconnected.com/the-definite-guide-to-handling-errors-gracefully-in-javascript-58424d9c60e6
- https://www.toptal.com/abap/clean-code-and-the-art-of-exception-handling
- https://tools.ietf.org/html/rfc7807
- https://nordicapis.com/best-practices-api-error-handling/