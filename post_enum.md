```
# Look for flags on Windows boxes
powershell -c "dir -recurse | ? name -like *file-name-here* "
powershell -c "get-childitem -recurse | where-object { $_.Name -like '*file-name-here*' }" 
```
