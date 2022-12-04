# CheatSheet
some cheat sheet for bash &amp; etc.

## Verify Domains :
```
while read line; do whois "$line" | awk -F: '/^Registrant Organization/ { print $2 }' | xargs -0 printf "$line: %s"; done < domains.txt
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
```
