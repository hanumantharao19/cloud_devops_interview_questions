## Script1 Disk Usage Alert Script
```
#!/bin/bash
THRESHOLD=85

df -h | awk 'NR>1 {print $5 " " $6}' | while read output; do
  usage=$(echo $output | awk '{print $1}' | sed 's/%//')
  mount=$(echo $output | awk '{print $2}')

  if [ $usage -ge $THRESHOLD ]; then
    echo "ALERT: $mount is ${usage}% full"
  fi
done

```
## CPU Usage Monitor
```
#!/bin/bash
CPU=$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | sed 's/%us,//')

echo "CPU Usage: $CPU%"
```
## Memory Usage Alert
```
#!/bin/bash
THRESHOLD=80

MEM=$(free | awk '/Mem:/ {printf("%.0f"), $3/$2 * 100}')

if [ "$MEM" -gt "$THRESHOLD" ]; then
  echo "WARNING: Memory usage is ${MEM}%"
fi
```

## Service Health Check (Auto Restart)
```
#!/bin/bash

SERVICE=nginx

if ! systemctl is-active --quiet $SERVICE; then
  echo "$SERVICE is down — restarting"
  systemctl restart $SERVICE
else
  echo "$SERVICE is running"
fi
```
## Website Health Check
```
#!/bin/bash

URL="https://example.com"

STATUS=$(curl -o /dev/null -s -w "%{http_code}" $URL)

if [ "$STATUS" != "200" ]; then
  echo "Site is DOWN — Status: $STATUS"
else
  echo "Site is UP"
fi
```

## Log Cleanup Script
```
#!/bin/bash

LOG_DIR="/var/log/myapp"
find $LOG_DIR -type f -name "*.log" -mtime +7 -delete

echo "Old logs cleaned"
```
## Process Monitor
```
#!/bin/bash

PROCESS="java"

if pgrep $PROCESS > /dev/null; then
  echo "$PROCESS is running"
else
  echo "$PROCESS is NOT running"
fi


```
## Backup Script
```
#!/bin/bash

SRC="/data"
DEST="/backup/data_$(date +%F).tar.gz"

tar -czf $DEST $SRC

echo "Backup completed: $DEST"
```
## Kubernetes Pod Check Script

#!/bin/bash

kubectl get pods --all-namespaces | grep -v Running | grep -v Completed

## Failed Login Alert
```
#!/bin/bash

grep "Failed password" /var/log/auth.log | wc -l

```
