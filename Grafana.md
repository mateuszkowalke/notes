# Grafana

### Variables

To create key-value pairs based on id and name columns of some table we need to use query and regex similar to the one below: 

```sql
SELECT concat('name="', name, '"id="', id, '"') FROM objects;
```

```regex
/name="(?<text>[^"]+)|id="(?<value>[^"]+)/g
```