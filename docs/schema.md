# Schema

### Blogs
Whole entire blogs.

```
- name
- description
- author_id
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
- blog_id
- post_time
- content
```

### Comments
Comments on blog entries

```
- post_time  default=now
- author_id
- entry_id
- content    text
```

