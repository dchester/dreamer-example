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
- signup_date
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
- post_time
- author_id
- entry_id
- content   text
```

