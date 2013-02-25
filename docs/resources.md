# Routes

***

### POST /authors

Create a new author

###### Request Parameters

name | required? | description
-----|-----------|------------
name | required | Full legal name
email | required | Email address
handle | required | Author handle
website | optional | Author website

***

### POST /authors/:author_id

Update details about an author

###### Request Parameters

name | required? | description
-----|-----------|------------
name | required | Full legal name
email | required | Email address
website | optional | Author website

***

### GET /authors/:author_id

Get details about an author

***

### POST /blogs

Create a new blog

###### Request Parameters

name | required? | description
-----|-----------|------------
name | required | Name of the blog
author_id | required | Author of the blog
description | optional | Description of the blog

***

### GET /blogs

###### Example Response
```json
[
  {
    "id": 1000,
    "name": "The trials of being James"
  }
]
```

***

### GET /blogs/:blog_id

Get details about a blog

###### Example Response
```json
{
  "id": 1000,
  "name": "The trials of being James",
  "description": "If a cat could type anything other than F7 all the time...",
  "author": {
    "name": "James Cooper",
    "email": "jimz@jimzindustries.biz"
  }
}
```

***

### POST /blogs/:blog_id

Edit details about a blog

###### Request Parameters

name | required? | description
-----|-----------|------------
name | required | Name of the blog
description | optional | Description of the blog


***

### POST /blogs/:blog_id/entries

Create a new blog entry

###### Request Parameters

name | required? | description
-----|-----------|------------
title | required | Blog entry title
content | required | Blog entry content

***

### POST /blogs/:blog_id/entries/:id

Edit an existing blog entry

###### Request Parameters

name | required? | description
-----|-----------|------------
title | required | Blog entry title
content | required | Blog entry content

***

### GET /blogs/:blog_id/entries

Get the entries for a blog

###### Example Response
```json
[
  {
    "id": 1000,
    "title": "Eighteen Hundred Hours",
    "post_time": "2012-01-01 14:27:03"
  }
]
```

***

### GET /blogs/:blog_id/entries/:entry_id

Get details about a blog entry

###### Example Response
```json
{
  "id": 1000,
  "title": "Eighteen Hundred Hours",
  "content": "Here's what I want to tell you ...",
  "post_time": "2012-01-01 14:27:03",
  "comments": [
    {
      "id": 2000,
      "content": "good post!"
    }
  ]
}
```

***

### POST /blogs/:blog_id/entries/:entry_id/comments

Post a new comment

###### Request Parameters

name | required? | description
-----|-----------|------------
author_id | required | Author of the comment
content | required | Comment content

***

### GET /blogs/:blog_id/entries/:entry_id/comments

Get comments for a blog post

###### Example Response
```json
[
  {
    "author_id": 1000,
    "post_time": "2012-01-01 15:32:02",
    "content": "Very interesting post!"
  }
]
```

