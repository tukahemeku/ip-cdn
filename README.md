Securitytrails.com​
#ابتدا  لاگین کنید

<a>
https://securitytrails.com/list/apex_domain/buyyoutubviews.com
</a>

assetfinder

‍‍```
assetfinder buyyoutubviews.com | grep -s "buyyoutubviews.com" | sed '/*/d' | tr -d ' ' | sort -u >>  subs.txt
‍‍```

findomain

‍‍```
findomain -t buyyoutubviews.com​​ -q | sort -u | grep -vs '^$' >> subs.txt
‍‍```

subfinder

‍‍```
subfinder -d buyyoutubviews.com​ -silent -nc -o >> subs.txt
‍‍```


viewdns.info

‍‍```
https://viewdns.info/iphistory/?domain=buyyoutubviews.com ---> ips.txt
‍‍```


dnsx
```
cat subs.txt | dnsx --resp-only​ >> ips.txt
#removing dups

cat ips.txt | sort -u > temp
cat temp >  ips.txt
rm temp
```

nmap
example usaage for one ip

‍‍```
nmap -sS -Pn 188.114.99.228 -p 443 --script ssl-cert -T4
‍‍```

loop to check all ips
```
for ip in $(cat ips.txt);do​
    echo $ip | sed 's|^|https://|' | sed 's/$/ -->/' | tr -d "\n" >> output​
    nmap -sS -Pn $ip -p 443 --script ssl-cert -T4 | grep "Subject Alternative Name:" | tr " " "\n" | sed 's/DNS://g' | grep "\." | tr -d "\n" | sed -e '$a\' | tr "," " " >> output​done​; cat output | grep buyyoutubviews.com​
```
