---
title: Spread schedule policy
---

To allocate metax device with best performance, you need to only assign `metax-tech.com/gpu` with annotations `hami.io/node-scheduler-policy: "spread"`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: gpu-pod1
  annotations: 
    hami.io/node-scheduler-policy: "spread" # when this parameter is set to spread, the scheduler will try to find the best topology for this task.
spec:
  containers:
    - name: ubuntu-container
      image: cr.metax-tech.com/public-ai-release/c500/colossalai:2.24.0.5-py38-ubuntu20.04-amd64 
      imagePullPolicy: IfNotPresent
      command: ["sleep","infinity"]
      resources:
        limits:
          metax-tech.com/gpu: 4 # requesting 4 metax GPUs
```
