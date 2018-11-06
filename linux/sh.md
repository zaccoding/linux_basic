## Shell script 

- <a href="">for </a>  


---  

> ### reset.sh  

```
#!/usr/bin/env bash

if [ -z "$1" ]; then
 echo 'empty args'
 exit 1
fi

for port in $@;
do
 url=http://localhost:$port/reset
 echo 'curl >> '$url 
 curl -XGET $url;
done
```
