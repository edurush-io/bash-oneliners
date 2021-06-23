# bash-oneliners
Useful bash one-liners

TCP memory used by the system
```bash
numpages=$(grep TCP /proc/net/sockstat | awk '{print $NF}'); pagesize=$(getconf PAGESIZE); echo "TCP memory used: "$((numpages * pagesize / 1024 ))" KB"
```

Top file descriptor consumer processes
```bash
lsof -n | awk '{ print $2 " " $1; }' | sort -rn | uniq -c | sort -rn | head -20
```
or use faster alternative with more useful info: [lsod.py](https://github.com/edurush-io/systools/blob/main/lsod.py)
