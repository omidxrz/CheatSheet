# CheatSheet
some cheat sheet for bash &amp; etc.

## Verify Domains :
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
