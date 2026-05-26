```dataview
TABLE type, status, check, related_papers, file.cday AS "created_at", file.mday AS "updated_at"
FROM "wiki/gaps"
SORT type ASC, status ASC
```
