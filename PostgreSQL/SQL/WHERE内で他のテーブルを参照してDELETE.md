# WHERE内で他のテーブルを参照してDELETE

## USINGを使って
#sh(sql){{

```clike
DELETE FROM player p USING team t 
WHERE p.team_id = t.team_id AND t.team_name = 'AC Milan'
```

}}
### INを使って同じ結果を得るには
#sh(sql){{

```clike
DELETE FROM player WHERE team_id IN ( SELECT team_id FROM team WHERE team_name = 'AC Milan' )
```

}}
