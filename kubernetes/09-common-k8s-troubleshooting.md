
### Question  
Your Kubernetes pod is stuck in the `CrashLoopBackOff` state. How would you troubleshoot and resolve this issue?

### Answer  
To troubleshoot a `CrashLoopBackOff`, I would check pod logs, container events, and resource limits. Common causes include application bugs, incorrect configs, failed dependencies, or OOM errors. I’d resolve the root cause based on these findings.


#### 1. 🔎 Check Pod Status and Reason

```bash
kubectl get pod <pod-name> -n <namespace>
kubectl describe pod <pod-name> -n <namespace>
```

Look under **"Last State"**, **"Exit Code"**, and **"Events"** to understand what’s causing the container crash.

---

#### 2. 📄 View Container Logs

```bash
kubectl logs <pod-name> -c <container-name> --previous -n <namespace>
```

Use `--previous` to see logs from the last failed attempt. You’ll often find stack traces, errors like:

- `Connection refused`
- `File not found`
- `Segmentation fault`
- `Permission denied`

---

#### 3. ⚙️ Check for Configuration or Secret Issues

- Did the pod mount a ConfigMap or Secret that’s missing or misconfigured?
- Are environment variables or command-line arguments set incorrectly?

```bash
kubectl describe pod <pod-name>
```

---

#### 4. 📦 Check for Missing Dependencies

- Is the container trying to connect to a service that’s not running?
- Is a database unavailable or unreachable?
- Are DNS entries resolving?

---

#### 5. 💽 Check Resource Constraints

```bash
kubectl describe pod <pod-name>
```

If it shows:
```
Reason: OOMKilled
```
Then the container exceeded memory limits. You’ll need to increase memory in the spec or optimize the application.

---

#### 6. 🐛 Check Image, CMD, ENTRYPOINT

Sometimes the crash is because of:

- Wrong image version
- Entry command missing a binary
- Script missing execute permissions

You can test locally with Docker or `kubectl run` to isolate the issue.

---

#### 7. 🧪 Use Ephemeral Container for Debugging (K8s v1.23+)

```bash
kubectl debug -it <pod-name> --image=busybox --target=<container-name>
```

You can inspect volumes, paths, env variables while the pod crashes repeatedly.

---

## Question
## Your Deployment Has `replicas: 3`, but Only 1 Pod Is Running — What Could Be Wrong?

### Answer  
There could be several reasons: resource constraints on nodes, scheduling issues, crashlooping pods, or affinity/taint restrictions that prevent pods from starting.


#### ✅ 1. **Check Pod Statuses**

Run:
```bash
kubectl get pods -l app=my-app
```

You might see:
- 1 Running
- 2 Pending / CrashLoopBackOff / ImagePullBackOff

---

#### ✅ 2. **Describe the Deployment and Pods**

```bash
kubectl describe deployment my-deployment
kubectl describe pod <pod-name>
```

Look for:
- Events at the bottom (e.g., “failed scheduling”)
- Volume mounting errors

---

#### ✅ 3. **Check Node Capacity**

Maybe the other pods can’t be scheduled due to insufficient **CPU/memory**.

Run:
```bash
kubectl describe nodes
```

If the nodes are out of resources, new pods won’t start.

---
