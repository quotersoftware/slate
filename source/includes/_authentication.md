# Authentication

The Quoter API uses the Client Credentials Flow of OAuth 2.0 for authentication:

1. Users of the API must first create an OAuth client ID and secret from the Quoter application.
2. Using the client ID and secret, as well as setting `grant_type: client_credentials`, send a request to the `/auth/oauth/authorize` endpoint to obtain an `access_token` and a `refresh_token`. See description on the endpoint for a more detailed example.
3. Use the `access_token` value as a bearer token (set header "Authorization: Bearer `access_token`") to send an authenticated request to the different endpoints.
4. The access token is valid for 1 hour. Beyond that, use `/auth/refresh` for getting a new access/refresh token pair from the refresh token. The refresh token is valid for 24 hours.
