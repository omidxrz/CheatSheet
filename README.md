# CheatSheet
some cheat sheet for bash &amp; etc.

#### Verify Domains :
```
while read line; do whois "$line" | awk -F: '/^Registrant Organization/ { print $2 }' | xargs -0 printf "$line: %s"; done < domains.txt
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
while read line; do if whois "$line" | grep -q "company"; then echo "$line"; fi; done < dnsx
```
#### Get Domains:
```
cat list.txt | rev | cut -d . -f 1,2 | rev | sort -u cat subdomain.txt | rev | cut -d . -f 2 | rev
```
#### Add HTTPS :
```
sed -i 's/^/https:\\\\\\\\/\\\\\\\\//' file1
```
#### Shodan :
```
shodan parse out.txt.json.gz --fields ip_str,port --separator : http.favicon.hash:-832558600
```
#### Regex :
- URL
```
(?:https?:\\\\/\\\\/)?(?:www\\\\d?\\\\.)?(?:[a-zA-Z0-9][-a-zA-Z0-9%_\\\\+~#=]*\\\\.)+[a-zA-Z][a-zA-Z0-9]{0,6}(?:/[a-zA-Z0-9_%+=~\\\\-#@]+(?:\\\\.[a-zA-Z0-9_%+=~\\\\-@]+)*)*\\\\/?(?:\\\\?(?:[a-zA-Z][a-zA-Z0-9]*=[a-zA-Z0-9+\\\\.\\\\-%]*&)*(?:[a-zA-Z][a-zA-Z0-9]*=[a-zA-Z0-9+\\\\.\\\\-%]*))?
```
#### Grep:
```
grep -v "$varName" config.txt > $$ && mv $$ config.txt
```
#### Find Origin IP
```
for ip in $(cat cidr.txt);do echo $ip &&  ffuf -w ./subdomains.txt -u http://$ip -H "Host: FUZZ" -s -mc 200; done
```
#### 401 Bruteforce 
```
ffuf -w ~/WordList/mylist/combo.txt -u https://staging.walmartvriddhi.org/wp-content/uploads/2022/07/Mask-Group-15.png -H "Authorization: Basic FUZZ" -fc 401
```
#### Bash for make Combo List
```
for user in $(cat ~/WordList/mylist/user.txt);do for pass in $(cat ~/WordList/mylist/password.txt); do echo -n "$user:$pass" | base64; done; done > combo.txt
```
#### Tools Install
```
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt install golang-go
pip3 install dnsgen
go install github.com/projectdiscovery/shuffledns/cmd/shuffledns@latest
go install github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
go install github.com/projectdiscovery/dnsx/cmd/dnsx@latest
go install github.com/projectdiscovery/mapcidr/cmd/mapcidr@latest
go install github.com/projectdiscovery/notify/cmd/notify@latest
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install github.com/nscuro/fdnssearch/cmd/fdnssearch@latest
go install github.com/hakluke/hakrevdns@latest
go install github.com/tomnomnom/assetfinder@latest
go install github.com/bp0lr/gauplus@latest
go install github.com/nscuro/fdnssearch/cmd/fdnssearch@latest
go install github.com/tomnomnom/unfurl@latest
go install github.com/d3mondev/puredns/v2@latest
go install github.com/tomnomnom/waybackurls@latest
go install github.com/jaeles-project/gospider@latest
go install github.com/Josue87/gotator@latest
go install github.com/tomnomnom/gf@latest
go install github.com/projectdiscovery/naabu/v2/cmd/naabu@latest
go install github.com/tomnomnom/meg@latest
go install github.com/ffuf/ffuf@latest
go install github.com/OWASP/Amass/v3/...@master
go install github.com/projectdiscovery/shuffledns/cmd/shuffledns@latest
go install github.com/KathanP19/Gxss@latest
go install github.com/projectdiscovery/katana/cmd/katana@latest
go install github.com/hahwul/dalfox/v2@latest
go install github.com/Emoe/kxss@latest
go install github.com/projectdiscovery/pdtm/cmd/pdtm@latest
go install github.com/projectdiscovery/asnmap/cmd/asnmap@latest
go install github.com/projectdiscovery/tlsx/cmd/tlsx@latest
export PATH="$PATH:/root/go/bin"

```
