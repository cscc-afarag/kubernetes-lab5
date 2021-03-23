# Jobs

see [here](https://kubernetes.io/docs/concepts/workloads/controllers/job/) for more information on Jobs

### refresher
Jobs ensure that pods run and successfully terminate, where jobs do one task. Acts like an executor with tasks/pods able to be run in parallel.

## Task 6 (Create a Job)

1. create a file called `job.yml` and copy the following into it:
   
```
apiVersion: batch/v1
kind: Job
metadata:
  name: batch-app
spec:
  backoffLimit: 4
  completions: 8
  parallelism: 2
  template:
    spec:
      containers:
      - name: job
        image: alpine:latest
        command: ["/bin/sh", "-c"]
        args: ["echo running job from $HOSTNAME!"]
      restartPolicy: Never
```

2. Apply the manifest and observe the behavior. Observe how many pods are active at one time.
3. create a new `cron_job.yml` and make the `Job` above a `CronJob` that runs with the following `schedule` : "*/1 * * * *" and has name `cron-app`
4. set  `successfulJobsHistoryLimit` to 3 and `failedJobsHistoryLimit` to 3
5. Wait and observe what happens