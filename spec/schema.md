# Schema

### Blogs
Whole entire blogs.

```
- name
- description
- author_id    fk=authors.id
```

### Authors
People who write blogs and comment on them.

```
- name
- handle       alpha,unique
- email        email
- website      nullable
- signup_date  default=now
```

### Entries
Blog entries.

```
- title
- blog_id    fk=blogs.id
- post_time  default=now
- content
```

### Comments
Comments on blog entries

```
- post_time  default=now
- author_id  fk=authors.id
- entry_id   fk=entries.id
- content    text
```


