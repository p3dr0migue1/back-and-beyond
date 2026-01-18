# Back And Beyond

A simple blog with notes and tips collected throughout the years.

## Start server
```
hugo server
```

Possible arguments:
* `-DF` - The `-D` will publish posts that are still in draft mode, and the `F` will publish posts that have dates in the future.
* `--noHTTPCache` - Ensures that all changes are picked up and nothing is cached.

Example usage:
```
hugo server -DF --noHTTPCache
```

## Adding a new post
```
hugo new content posts/<post-title>.md
```

## Making a post visible
To make a post visible simply change:
```markdown
draft = true
```
To:
```markdown
draft = False
```
The post will then be visible
