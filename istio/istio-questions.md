1️⃣ What problems does a service mesh solve that Kubernetes alone cannot?

Answer:

Kubernetes provides:

Service discovery

Load balancing

Basic networking

Istio adds:

L7 traffic management

mTLS security

Fine-grained authorization

Observability (metrics, traces, logs)

Resilience (retries, circuit breaking)

👉 Separates networking logic from application code.

2️⃣ Explain Istio architecture.

Answer:

Two main planes:

🔹 Data Plane

Envoy sidecar proxies injected into pods

Handle traffic routing, telemetry, security

🔹 Control Plane

Managed by **Istio components:

Pilot → Service discovery + config distribution

Citadel → Certificate management (mTLS)

Galley (deprecated) → Config validation

Istiod → Unified control plane (modern versions)

3️⃣ What is the role of Envoy proxy in Istio?

Answer:

Envoy handles:

Traffic interception

Routing rules

TLS termination

Retries & timeouts

Metrics collection

Policy enforcement

👉 All service-to-service traffic flows through Envoy.

4️⃣ Difference between Ingress Gateway and Kubernetes Ingress

Answer:

Istio Gateway:

L7 intelligent routing

TLS termination

Traffic shifting

Works with VirtualService

K8s Ingress:

Basic HTTP routing

Limited advanced control

5️⃣ What is a VirtualService?

Answer:

Defines traffic routing rules:

Path-based routing

Header-based routing

Traffic splitting

Canary deployments

6️⃣ What is DestinationRule?

Answer:

Controls traffic policies after routing decision:

Load balancing policy

Connection pool settings

TLS settings

Subsets (versions v1, v2)

7️⃣ How do VirtualService and DestinationRule work together?

Answer:

Flow:

Request → Gateway → VirtualService → DestinationRule → Pod


VirtualService → decides WHERE traffic goes
DestinationRule → decides HOW traffic is handled

8️⃣ Explain mTLS in Istio.

Answer:

Mutual TLS provides:

Encryption

Identity verification

Zero-trust networking

Modes:

STRICT

PERMISSIVE

DISABLE

Certificates issued automatically by Istio CA.

9️⃣ How is mTLS enabled cluster-wide?

Answer:

Using PeerAuthentication:

kind: PeerAuthentication
spec:
  mtls:
    mode: STRICT

## 🔟 What are Authorization Policies?

Answer:

Provide fine-grained access control:

Based on identity

Namespace

Labels

IP ranges

JWT claims

Replaces legacy RBAC policies.

## 1️⃣1️⃣ What is ServiceEntry?

Answer:

- Allows access to external services outside the mesh.

Example:

Calling external APIs (AWS, payment gateway, SaaS)

1️⃣2️⃣ What is Sidecar Injection?

Answer:

Automatic or manual addition of Envoy proxy to pods.

Enabled at namespace level:

istio-injection=enabled

1️⃣3️⃣ What happens if sidecar injection fails?

Answer:

Pod runs without mesh features:

No mTLS

No routing rules

No telemetry

Potential communication failures

1️⃣4️⃣ How does Istio achieve traffic shifting?

Answer:

Using VirtualService weight configuration:

route:
- destination:
    subset: v1
  weight: 80
- destination:
    subset: v2
  weight: 20


Used for:

Canary deployments

A/B testing

Blue-green deployments

1️⃣5️⃣ What is Circuit Breaking in Istio?

Answer:

Prevents cascading failures by limiting traffic.

Configured in DestinationRule:

Max connections

Pending requests

Retry budgets

1️⃣6️⃣ How does Istio provide observability?

Answer:

Integrated with:

Metrics (Prometheus)

Dashboards (Grafana)

Tracing (Jaeger)

Logs

1️⃣7️⃣ How do you troubleshoot traffic not reaching a service?

Answer (Sr SRE level):

Check:

Sidecar injection status

VirtualService rules

DestinationRule subsets

mTLS compatibility

Gateway configuration

Envoy config (istioctl proxy-config)

Service endpoints

Network policies

1️⃣8️⃣ What is an Istio Gateway vs VirtualService Gateway field?

Answer:

Gateway resource:

👉 Defines entry point (ports, TLS)

VirtualService gateway field:

👉 Attaches routing rules to that gateway

1️⃣9️⃣ How does Istio handle multi-cluster setups?

Answer:

Supports:

Multi-primary

Primary-remote

Shared control plane

Features:

Cross-cluster service discovery

mTLS across clusters

Failover routing

2️⃣0️⃣ What are common production challenges with Istio?

Answer:

Sr-level answer:

Increased latency

Resource overhead

Complex debugging

Certificate issues

Version compatibility

Config sprawl

Upgrade risks

Sidecar lifecycle management