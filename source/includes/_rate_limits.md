# Rate Limits

To ensure stability of the API for all users, Quoter enforces rate-limiting of 10 requests per second per access credential.
Requests that exceed this limit will receive a `429: Too many requests` error code.
