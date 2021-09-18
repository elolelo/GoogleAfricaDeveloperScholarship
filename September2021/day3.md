Welcome to Cloud Shell! Type "help" to get started.
Your Cloud Platform project in this session is set to my-tutor-d4133.
Use “gcloud config set project [PROJECT_ID]” to change to a different project.
lelonompumelelo@cloudshell:~ (my-tutor-d4133)$ ls
README-cloudshell.txt
lelonompumelelo@cloudshell:~ (my-tutor-d4133)$ mkdir day1
lelonompumelelo@cloudshell:~ (my-tutor-d4133)$ cd day1/
lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$ LS
-bash: LS: command not found
lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$ ls
lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$ gcloud auth list
Credentialed Accounts

ACTIVE: *
ACCOUNT: lelonompumelelo@gmail.com

To set the active account, run:
    $ gcloud config set account `ACCOUNT`

lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$ gcloud config list project
[core]
project = my-tutor-d4133

Your active configuration is: [cloudshell-18437]
lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$ gcloud compute machine-types list
API [compute.googleapis.com] not enabled on project [636818248877].
Would you like to enable and retry (this will take a few minutes)?
(y/N)?  y

Enabling service [compute.googleapis.com] on project [636818248877]...
ERROR: (gcloud.compute.machine-types.list) FAILED_PRECONDITION: Billing account for project '636818248877' is not found. Billing must be enabled for activation of service(s) 'compute.googleapis.com,compute.googleapis.com,compute.googleapis.com' to proceed.
Help Token: Ae-hA1Pi5952P9YxjK7YSRNk5jaYXQE3FqYpK7pTNylIZOy7Up3Q-KLD6GXd-POx84K0k2AjmkUfT2aZ_j1ycRONafWa4JNblQvk_EdfKHhE1r-I7Feez74=
- '@type': type.googleapis.com/google.rpc.PreconditionFailure
  violations:
  - subject: ?error_code=390001&project=636818248877&services=compute.googleapis.com&services=compute.googleapis.com&services=compute.googleapis.com
    type: googleapis.com/billing-enabled
- '@type': type.googleapis.com/google.rpc.ErrorInfo
  domain: serviceusage.googleapis.com/billing-enabled
  metadata:
    project: '636818248877'
    services: compute.googleapis.com,compute.googleapis.com,compute.googleapis.com
  reason: UREQ_PROJECT_BILLING_NOT_FOUND
lelonompumelelo@cloudshell:~/day1 (my-tutor-d4133)$
