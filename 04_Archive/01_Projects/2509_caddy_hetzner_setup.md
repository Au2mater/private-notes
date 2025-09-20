## Remove or lock down the `:80` generic site.
* There's a port 80 blovk in Caddyfile that 
	* That block serves **all traffic on port 80**, regardless of hostname. Two problems:
		- It may intercept requests to domains you didn’t intend.
	    - It serves unencrypted HTTP without a redirect.
```shell
# root@ubuntu-4gb-nbg1-1
caddy stop
systemctl stop caddy
pkill caddy
nano /etc/caddy/Caddyfile
```
* comment out `:08 {...}` block
```
# root@ubuntu-4gb-nbg1-1
systemctl stop caddy
nano /etc/caddy/Caddyfile
```
* `systemctl status caddy` ensure caddy is running and enabled
   
##  Confirm port 443 is open on Hetzner firewall/security groups.
* [Firewalls · Hetzner Console](https://console.hetzner.com/projects/11751517/firewalls/2394254/rules)
* done
##  Verify Let’s Encrypt cert issuance (`caddy list-modules | grep tls` and check logs).
```
root@ubuntu-4gb-nbg1-1:~#caddy list-modules | grep tlss caddy.listeners.tls
```
* ensure that tls.issuance.acme is listed
* Now check the logs:
`journalctl -u caddy --no-pager | grep 'certificate'`

* You should see lines like:
`server.go: Validating certificate for translate.fjeldmann.dk server.go: Certificate obtained successfully`

👉 If you see errors (rate limits, DNS issues), you’ll know immediately.
##  Enable **DNSSEC** at simply.com for fjeldmann.dk.
* `dig +dnssec fjeldmann.dk` result shows: `flags: qr rd ra`
	* But **no `ad` (Authenticated Data) flag** was returned. That means **DNSSEC is not enabled** for `fjeldmann.dk`.  
	* If DNSSEC were active and validating, you’d see something like: `flags: qr rd ra ad`
### How to enable DNSSEC at simply.com:
1. Log in to the **Simply.com control panel**.
2. Go to **Domains → DNS settings**.
3. Look for a **DNSSEC** toggle/section.
    - Some registrars let you enable DNSSEC with one click (they handle keys + DS records).
    - If Simply.com requires manual DS record entry, they will provide instructions (you’ll generate DS from your DNS host).


## 5. Keep Caddy Updated (TLS 1.3 + CVE patches)

Caddy packages are updated frequently. On Ubuntu, you can add a **cron job** to update it:

**Script: `/usr/local/bin/update-caddy.sh`**

```
#!/bin/bash set -e  
# Update apt repos 
apt-get update -y  
# Upgrade only Caddy 
apt-get install --only-upgrade -y caddy  
# Restart service if updated 
systemctl restart caddy
```
* Make it executable:
```
chmod +x /usr/local/bin/update-caddy.sh
```

* Add a cronjob (`crontab -e` as root):
```shell
crontab -e
```
paste this into the crontab
```text
0 4 * * 0 /usr/local/bin/update-caddy.sh >> /var/log/caddy-update.log 2>&1
```
* This will run every Sunday at 4AM.

* To check what cron jobs are set up for your user, run the following command in your terminal:
```
crontab -l
```
---

    
##  Consider monitoring logs for anomalies (failed ACME renewals, brute force attempts, etc.).
## 👁️ 6. Monitoring Logs

- **Where logs are:**  
    Caddy logs are in `journald`:
    `journalctl -u caddy --no-pager -f`
    (`-f` = follow live logs)
    
- **What to look for:**
    - `tls.obtain` errors (certificate renewal failures).
    - Repeated 401/403/429 errors (could be scanning or brute force).
    - ACME rate-limit messages.
    - Any backend errors (502, 503).
        
- **How often:**
    - At least once after setup (to confirm certs are issued).
    - Then maybe once a week, unless you set up log monitoring.
        

**Tip:**  
You can filter for TLS/ACME issues:

`journalctl -u caddy | grep 'tls' journalctl -u caddy | grep 'acme'`

If you want something more advanced, you can integrate with `fail2ban` or push logs into a monitoring system (Prometheus + Grafana, Loki, etc.).