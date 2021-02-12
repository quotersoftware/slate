# HTTP Response Codes

The Quoter API use conventional HTTP response cods to indicate whether an API request succeeded or failed.

| HTTP Code | Meaning                                                                                                                      |
| --------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 200       | Success -- Your request was successfully processed; the result is included in the response body. For POST requests.          |
| 204       | No Content -- You request was successfully processed; call a GET to retrieve the updated results. For PATCH/DELETE requests. |
| 400       | Bad Request -- Your request is invalid.                                                                                      |
| 401       | Unauthorized -- Your API credentials are invalid.                                                                            |
| 404       | Not Found -- The specified resource could not be found.                                                                      |
| 422       | Unprocessable Entity -- The request format is incorrect. See error content for details.                                      |
| 429       | Too Many Requests -- You've reached your rate limit. Try again later.                                                        |
| 500       | Internal Server Error -- We had a problem with our server. Try again later.                                                  |
