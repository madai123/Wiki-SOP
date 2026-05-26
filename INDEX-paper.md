```dataview
TABLE title, source_id, year, status, file.cday AS "created_at", file.mday AS "updated_at"
FROM "wiki/papers"
SORT file.cday DESC
```
