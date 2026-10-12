## Bug Bounty Shortcuts:


#### dirsearch:

```

python3 dirsearch.py -u "https://www.zooplus.co.uk" -t 5 -w ~/SecLists/Discovery/Web-Content/merged.txt -e jsp,jspx -x 400 2>&1 | tee results1.tx


```


#### knock/knockpy:

```

python3 knockpy.py -d uberinternal.com --wordlist ~/SecLists/Discovery/DNS/merged.txt --

```
