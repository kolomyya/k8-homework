# k8-homework

1.)This cronjob will run one job every 1 minutes (using a cron format for scheduling) and display “Hello” and complete within 10 second
To launch this job you just need to run the following command

###kubectl apply -f cronjob.yaml

2.)To check that the cronjob was created just use 

###kubectl get cronjob

3.)So cronjob was named “homework” based on the metadata.name value. As a default function the job will run, so suspend value is False. There is currently no task running it (we didn’t plan it yet).If we check the status of our scheduled jobs after 1 minutes,  we’ll see that job completed within 10s.That will show the number of times the job has been restarted, full config of the job and the pod created.


###kubectl describe job or kubectl describe cronjob
