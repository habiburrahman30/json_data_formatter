
## Description

This document is Express JS app.js file configuration and many more 🥰.

## convert json to list

```bash
final data = res.data['data']
            .map((json) => Post.fromJson(json as Map<String, dynamic>))
            .toList()
            .cast<Post>() as List<Post>;
```
## convert json to map
```bash
final data = Post.fromJson(res.data['data']);
```
## convert list to map
```bash
final data = services.map((e) => e.toJson()).toList();
```


