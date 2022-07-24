Print just the value for a field:
```
jq -c '.fieldname'
```

Create a dictionary of one or more fields:
```
jq -c '{fieldname, fieldname2}'
```

Get true/false if field value is greater than/equal to/less than a value:
```
jq -c '.fieldname < #'
```

Keep only lines that match filter of a field:
```
jq -c '. | select(.fieldname >= #)'
```

Keep only lines and values that match filter of a field:
```
jq -c '.fieldname | select(. >= #)'
```