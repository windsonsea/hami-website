---
title: 分配AWS Neuron核心资源
---

如需分配1/2个neuron设备，您可以通过分配neuroncore来实现，如下例所示：

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: npod
spec:
  restartPolicy: Never
  containers:
    - name: npod
      command: ["sleep","infinity"]
      image: public.ecr.aws/neuron/pytorch-inference-neuron:1.13.1-neuron-py310-sdk2.20.2-ubuntu20.04
      resources:
        limits:
          cpu: "4"
          memory: 4Gi
          aws.amazon.com/neuroncore: 1
        requests:
          cpu: "1"
          memory: 1Gi
```
