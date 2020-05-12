Months ago I deleted default taint `node-role.kubernetes.io/master` and after upgrading k8s from 1.16 to 1.17 got stuck with pending nginx ingress pod.
It has these tolerations:
```
Tolerations:     node-role.kubernetes.io/master:NoSchedule
                 node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
```
At the same time I had on the master `k8s-m1 node-role.kubernetes.io/master=true:NoSchedule` taint.

To restore the defaults on your master Kubernetes node run the following command:
```bash
$ # k8s-m1 is the name of your master node
$ kubectl taint nodes k8s-m1 node-role.kubernetes.io/master=true:NoSchedule-
$ kubectl taint nodes k8s-m1 node-role.kubernetes.io/master="":NoSchedule
```
