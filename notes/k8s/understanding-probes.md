# Understanding Kubernetes probes

### startupProbe + livenessProbe

`startupProbe` works only with `livenessProbe`. Nothing will happen if you specify just this probe without `livenessProbe`.
If both probes are specified `livenessProbe` starts working if `startupProbe` succeeded.

### readinessProbe

`readinessProbe` is independent from `startupProbe` and `livenessProbe`. It decides whether network traffic is allowed to be routed to a container and that's all it does.
`livenessProbe` might not be fine and the target container thus will be restarted but if `readinessProbe` is ok then traffic will be routed to the container anyway.
