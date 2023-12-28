
## Description

This document is Flutter List to Map and Map to List 🥰.

## Convert json to list

```bash
final data = res.data['data']
            .map((json) => Post.fromJson(json as Map<String, dynamic>))
            .toList()
            .cast<Post>() as List<Post>;
```
## Convert json to map
```bash
final data = Post.fromJson(res.data['data']);
```
## Convert list to map
```bash
final data = services.map((e) => e.toJson()).toList();
```


