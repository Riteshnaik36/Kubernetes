What is Liveness probe? 
- A Liveness Probe is a check that helps determine if a container in a Pod is still running and working properly. 
- If the probe fails, Kubernetes will mark the container as "failed" and try to restart it according to the Pod's restart settings. 
- This ensures that the applications in containers are being monitored and stay healthy.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Purpose
------------
Liveness probes help detect when an application is running but is stuck or not working properly (for example, the app might be running but not responding). 
If the liveness probe fails, Kubernetes will try to restart the container to fix the problem, which makes the application more reliable.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Example of Liveness Probe in a Pod Spec:
Here’s an example of how a Liveness Probe might be configured in a Kubernetes Pod definition:
----------------------------------------------------------
apiVersion: v1
kind: Pod
metadata:
  name: my-app
spec:
  containers:
    - name: my-container
      image: my-image:latest
      livenessProbe:
        httpGet:
          path: /healthz ------------ # Check the /healthz endpoint
          port: 8080   -------------- # Port 8080 on the container
        initialDelaySeconds: 5 ------ # Wait 5 seconds before the first probe
        periodSeconds: 10 ----------- # Probe every 10 seconds
        timeoutSeconds: 3 ----------- # Timeout after 3 seconds
        failureThreshold: 3 --------- # Restart container after 3 consecutive failures

In this example:
------------------
The probe performs an HTTP GET request to /healthz on port 8080.
The first probe is delayed by 5 seconds after the container starts (initialDelaySeconds).
It probes every 10 seconds (periodSeconds).
If the probe takes more than 3 seconds to respond, it will fail (timeoutSeconds).
If the probe fails 3 times consecutively, Kubernetes will restart the container (failureThreshold).
----------------------------------------------------------
Benefits of Liveness Probes:
1>>>> Automatic Recovery: If a container becomes unresponsive or enters a failure state, the liveness probe ensures that Kubernetes will automatically restart it, improving availability.
2>>>> Reduced Downtime: By automatically detecting and recovering from failures, liveness probes minimize application downtime.
3>>>> Improved Monitoring: They provide a built-in way for Kubernetes to actively monitor the health of running containers.
