# Server

Url: wuchg.top:8080

Encoding: application/x-www-form-urlencoded

Method: Post


# Download file

Url: /get

argument:
 - path: path to the file

return value: file's octet-stream

# List files

Url: /ls

argument:
 - path: path to the directory ("." if home)

return value: json

sample: {"file": ["file1"], "dir": ["dir1"]}

# Check if file exists

Url: /exists

argument:
 - path: path to the file/directory ("." if home)

return value: "not exists", "file" or "dir"

# Upload file

First get upload token

Url: /token

argument:
 - path: path to the file
 - slice_cnt: the all number of slices of the file sliced

return value: the token. The token will last 10 minutes.

Then upload the slices

Url: /upload

argument: 
 - token: token got
 - file: the file's data
 - seq: the sequence number of the slice (0 to slice_cnt-1)

return value: "success" or "timeout or finished"