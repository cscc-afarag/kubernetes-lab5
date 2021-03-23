
# Deployments

### refresher
Like ReplicaSet but has additional functionality, like rollback. Also allows for more fine grained control of pods.

 
## Task 2 (Create a Deployment)

In this task we will make a `Deployment` similar to the replica set we made in task 1.

visit [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) for more information

1. In a new manifest file called `deployment_1.yml` create a `Deployment` with name 'nginx-deployment'
2. The deployment should have 2 `replicas` and the `revisionHistoryLimit` set to 3
3. under [strategy](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy) we wil use the `RollingUpdate` strategy, with `maxSurge` = 1 and `maxUnavailable` = 0
4. Use the same `template` from task 1 for the pods and the same selector
5. Create the manifest using `kubectl create`. Make sure to use the `--record` flag so we keep the command as an annotation
6. Use the `kubectl get` command to list the `ReplicaSet` that this deployment created with all its labels.
7. What do you notice about the `ReplicaSet` - what is this used for? Write down your answer in the `workload_tasks.md`
8. Try scaling the deployment like we did for `ReplicaSet`

## Task 3 (Update the Deployment)

1. Add some labels to the pod template to the deployment from Task 2
   - make sure to apply the changes with `--record` using the `apply` command
2. Write down what labels changes in the `workload_tasks.md` file. 
3. Run the command `kubectl rollout history deployment nginx-deployment` - and notice the revisions
4. In your worksheet - write down the commands I would use to rollback a deployment to a specific revision.
   -  see [here](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-back-a-deployment) for help
5. Now that we are done - delete the deployment with `kubectl delete deploy nginx-deployment`

---