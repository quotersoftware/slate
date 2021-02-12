# Pagination

List endpoints support pagination via the `page` and `limit` query parameters.
For example, if you want get the first 10 items, specify as `https://api.quoter.com/v1/items?page=1&limit=10` ,
then the next 10 items as `https://api.quoter.com/v1/items?page=2&limit=10`.

The list response contains two fields: `data`, which contains a list of the resources, and `has_more`, which is a boolean value that indicates whether there is more data in the next page.
