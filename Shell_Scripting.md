## PARSING

### Parsing IPs
```
ip_validation=$(jq -r '.net_ip' ipcon.json | sed 's/\.[0-9]\+$/\.1/')
if echo "$ip_validation" | grep -Eq '^([0-9]{1,3}\.){3}[0-9]{1,3}$'; then
    echo "IP OK: $ip_validation"
else
    echo "Value wrong: $ip_validation"
fi
```
---

### Delete too many files##

````
for file in /path/*.ext; do sudo rm -f "$file"; done
````
