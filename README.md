### [Kubernetes Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

#### Liveness Probe
- This probe determines when to re-start a container. It detects if application falls into broken states that cannot be recovered without restarting it. `kubelet` uses this probe to determine when to restart the container
- When liveness probe fails, kubelet restart the container.

#### Readiness Probe
- Determines when a container is ready to start accepting traffic. This probe runs periodically throughout container lifecycle.
- When containers are healthy but sometime applications running on it unable to serve traffic (One such case could be that application is waiting to get the response from an API). In such cases, we dont want to kill application or send request to application. Here, readiness probe can be configured. When readiness probe fails, the status of pod changes to NotReady. 

#### Startup Probe
- This probe verifies if the application within the container has started. This is only executed at startup. The liveness and readiness probe will only executed if this probe is executed successfully.
- For slow starting application, we can set a startup probe long enough to cover worst case startup.
- When startup probe fails, kubelet also kills the pod after grace period.
