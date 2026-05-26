```dataview
TABLE title, status, file.cday AS "created_at", file.mday AS "updated_at"
FROM "wiki/comparisons"
SORT status DESC
```
