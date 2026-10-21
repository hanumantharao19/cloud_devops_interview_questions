## Health Check Script for a URL
```
import requests

url = "https://example.com"

try:
    r = requests.get(url, timeout=5)
    if r.status_code == 200:
        print("Service is UP")
    else:
        print(f"Service returned status {r.status_code}")
except Exception as e:
    print("Service is DOWN:", e)
```
## Monitor Disk Usage
```
import shutil

total, used, free = shutil.disk_usage("/")

percent = used / total * 100

print(f"Disk Usage: {percent:.2f}%")

if percent > 80:
    print("WARNING: Disk usage above 80%")

```
## CPU & Memory Monitoring

```
import psutil

cpu = psutil.cpu_percent(interval=1)
memory = psutil.virtual_memory().percent

print(f"CPU Usage: {cpu}%")
print(f"Memory Usage: {memory}%")

if cpu > 80 or memory > 80:
    print("High resource usage detected!")
```
## Parse Log File for Errors
```
error_count = 0

with open("app.log") as f:
    for line in f:
        if "ERROR" in line:
            error_count += 1

print("Total Errors:", error_count)
```
## Check If Process Is Running
```
import psutil

process_name = "nginx"

for p in psutil.process_iter(['name']):
    if p.info['name'] == process_name:
        print("Process is running")
        break
else:
    print("Process not running")
```
## Read JSON Config File
```
import json

with open("config.json") as f:
    data = json.load(f)

print(data["database"]["host"])

```
## Execute Shell Command
```
import subprocess

result = subprocess.run(["df", "-h"], capture_output=True, text=True)

print(result.stdout)
```
## Retry Logic for Unstable Service
```
import requests
import time

url = "https://example.com"

for i in range(5):
    try:
        r = requests.get(url)
        if r.status_code == 200:
            print("Success")
            break
    except:
        print("Retrying...")
        time.sleep(2)
```
## Simple TCP Port Check
```
import socket

host = "google.com"
port = 80

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.settimeout(2)

result = sock.connect_ex((host, port))

if result == 0:
    print("Port is open")
else:
    print("Port is closed")

sock.close()
```


