---
title: Allocate device core and memory to container
---

To allocate a specific part of device resources, you need to specify both `cambricon.com/mlu370.smlu.vmemory` and `cambricon.com/mlu370.smlu.vcore`
in the container's resource limits, along with the number of MLUs requested using `cambricon.com/vmlu`.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: binpack-1
  labels:
    app: binpack-1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: binpack-1
  template:
    metadata:
      labels:
        app: binpack-1
    spec:
      containers:
        - name: c-1
          image: ubuntu:18.04
          command: ["sleep"]
          args: ["100000"]
          resources:
            limits:
              cambricon.com/vmlu: "1"
              cambricon.com/mlu370.smlu.vmemory: "20"
              cambricon.com/mlu370.smlu.vcore: "10"
```
