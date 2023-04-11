# CheatSheet
some cheat sheet for bash &amp; etc.

### Verify Domains :
```
while read line; do whois "$line" | awk -F: '/^Registrant Organization/ { print $2 }' | xargs -0 printf "$line: %s"; done < domains.txt
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
```
## Get Domains:
```
cat list.txt | rev | cut -d . -f 1,2 | rev | sort -u cat subdomain.txt | rev | cut -d . -f 2 | rev
```
### Add HTTPS :
```
sed -i 's/^/https:\\\\\\\\/\\\\\\\\//' file1
```
### Shodan :
```
shodan parse out.txt.json.gz --fields ip_str,port --separator : http.favicon.hash:-832558600
```
### Regex :
- URL
```
(?:https?:\\\\/\\\\/)?(?:www\\\\d?\\\\.)?(?:[a-zA-Z0-9][-a-zA-Z0-9%_\\\\+~#=]*\\\\.)+[a-zA-Z][a-zA-Z0-9]{0,6}(?:/[a-zA-Z0-9_%+=~\\\\-#@]+(?:\\\\.[a-zA-Z0-9_%+=~\\\\-@]+)*)*\\\\/?(?:\\\\?(?:[a-zA-Z][a-zA-Z0-9]*=[a-zA-Z0-9+\\\\.\\\\-%]*&)*(?:[a-zA-Z][a-zA-Z0-9]*=[a-zA-Z0-9+\\\\.\\\\-%]*))?
```
### Grep:
```
grep -v "$varName" config.txt > $$ && mv $$ config.txt
```
### Find Origin IP
```
for ip in $(cat cidr.txt);do echo $ip &&  ffuf -w ./subdomains.txt -u http://$ip -H "Host: FUZZ" -s -mc 200; done
```
### 401 Bruteforce 
```
ffuf -w ~/WordList/mylist/combo.txt -u https://staging.walmartvriddhi.org/wp-content/uploads/2022/07/Mask-Group-15.png -H "Authorization: Basic FUZZ" -fc 401
```
** Bash for make Combo List
```
for user in $(cat ~/WordList/mylist/user.txt);do for pass in $(cat ~/WordList/mylist/password.txt); do echo -n "$user:$pass" | base64; done; done > combo.txt
```
