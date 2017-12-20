## Some bin/bash/unix stuff

### Recursively Remove .DS_Store
```
cd to/directory
find . -name '.DS_Store' -type f -delete
```

### Get IP address
```
ipconfig getifaddr en0
```

### Compress and extract
```
gzip -k stuff.json
gunzip -k files.json.gz
```
