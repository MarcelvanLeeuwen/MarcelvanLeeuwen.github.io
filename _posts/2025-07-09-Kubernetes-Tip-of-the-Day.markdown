---
layout: post
title:  "Kubernetes Tip of the Day"
date:   2025-07-09 15:16:04 +0200
categories: Kubernetes Tip of the Day
---
Today during my CKA training on KodeKloud I came across a very useful feature again: You can assign resources to your Pods, just like you would with virtual machines. Kubernetes lets you set

✅ Requests — the minimum amount of CPU and memory a container is guaranteed
✅ Limits — the maximum amount it’s allowed to use

This helps the scheduler place pods efficiently and ensures your apps don’t hog more resources than they should. 🔒

It’s small details like these that show how powerful Kubernetes is when it comes to fine-grained resource control.

Every day I’m learning something new—and I love how Kubernetes combines flexibility with stability. 🙌

#Kubernetes #CKA #DevOps #CloudNative #LearningByDoing
<br>
<br>
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: resource-demo-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: resource-demo
  template:
    metadata:
      labels:
        app: resource-demo
    spec:
      containers:
      - name: demo-container
        image: nginx:stable
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
```

