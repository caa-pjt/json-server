# Simple JSON server

## Install

`npm install`

## USAGE

Create a db.json

```bash
{
  "users": [
    {
      "id": 1,
      "firstname": "John",
      "lastname": "Doe",
      "email": "john.doe@example.com",
      "age": 25,
      "companyId": 1
    }
  ],
  "companies": [
    {
      "id": 1,
      "name": "Apple",
      "description": "Apple est une multinationale américaine spécialisée dans l'informatique et l'électronique. L'entreprise propose des produits tels que des ordinateurs personnels et ses dérivés et des logiciels informatiques. Parmi les plus connus figurent les ordinateurs Macintosh, les iPod, iPhone ou iPad et le lecteur iTunes."
    }
  ]
}
```

### Run server projet

`npm run json:server`

### Routes

Based on the example db.json, you'll get the following routes:

```bash
GET    /users
GET    /users/:id
POST   /users
PUT    /users/:id
PATCH  /users/:id
DELETE /users/:id

# Same for companies
GET   /companies
PUT   /companies
PATCH /companies
```

### EXAMPLES OF USE

Show a single companie:
`http://localhost:3000/companies/1`

Get all users for one company
`http://localhost:3000/companies/1/users`

Filter companies by name
`http://localhost:3000/companies?name=Microsoft`
`http://localhost:3000/companies?name=Microsoft&name=Apple`

Pagination and limit
`http://localhost:3000/companies?_page=1&_limit=2`

Sorting
`http://localhost:3000/companies?_sort=name&_order=desc`

User by age range
`http://localhost:3000/users?age_gte=30`
`http://localhost:3000/users?age_gte=30&age_lte=40`

Full text search
`http://localhost:3000/users?q=John`

### Usage with POSTMAN

To import the Postman collection and test from `Simple REST API with JSON server.postman_collection.json`, get further information from this page :
https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/

### Params

#### Conditions

```bash
  → ==
lt → <
lte → <=
gt → >
gte → >=
ne → !=
```

#### Range

- start
- end
- limit

```bash
GET /users?_start=1&_end=3
GET /users?_start=2&_limit=5
```

#### Paginate

- page
- per_page (default = 10)

`GET /users?_page=1&_per_page=25`

#### Sort

. \_sort=f1,f2

`GET /users?_sort=id,-views`

### Embed

```bash
GET /companies?_embed=users
```

### Delete

```bash
DELETE /users/1
DELETE /users/1?_dependent=companies
```
