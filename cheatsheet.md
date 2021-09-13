# The gcloud tool cheat sheet

###  A roster of go-to commands for the gcloud command-line tool, the primary command-line tool for Google Cloud.


#### Cheat sheet

##### Getting started<br>
Get going with the gcloud tool.

`gcloud init`: Initialize, authorize, and configure the gcloud tool.<br>
`gcloud version`: Display version and installed components.<br>
`gcloud components install`: Install specific components.<br>
`gcloud components update`: Update your Cloud SDK to the latest version.<br>
`gcloud config set project`: Set a default Google Cloud project to work on.<br>
`gcloud info`: Display current gcloud tool environment details.


##### Help<br>
Cloud SDK is happy to help.


`gcloud help`: Search the gcloud tool reference documents for specific terms.<br>
`gcloud feedback`: Provide feedback to the Cloud SDK team.<br>
`gcloud topic`: Supplementary help material for non-command topics like accessibility, filtering, and formatting.<br>


##### Personalization<br>
Make the Cloud SDK your own; personalize your configuration with properties.

`gcloud config set`: Define a property (like compute/zone) for the current configuration.<br>
`gcloud config get-value`: Fetch the value of a Cloud SDK property.<br>
`gcloud config list`: Display all the properties for the current configuration.<br>
`gcloud config configurations create`: Create a new named configuration.<br>
`gcloud config configurations list`: Display a list of all available configurations.<br>
`gcloud config configurations activate`: Switch to an existing named configuration.<br>


##### Credentials<br>
Grant and revoke authorization to Cloud SDK

`gcloud auth login`: Authorize Google Cloud access for the gcloud tool with Google Cloud user credentials and set the current account as active.<br>
`gcloud auth activate-service-account`: Like gcloud auth login but with service account credentials.<br>
`gcloud auth list`: List all credentialed accounts.<br>
`gcloud auth print-access-token`: Display the current account's access token.<br>
`gcloud auth revoke`: Remove access credentials for an account.<br>


##### Projects<br>
Manage project access policies

`gcloud projects describe`: Display metadata for a project (including its ID).<br>
`gcloud projects add-iam-policy-binding`: Add an IAM policy binding to a specified project.<br>


##### IAM<br>
Configuring Identity and Access Management (IAM) preferences and service accounts

`gcloud iam list-grantable-roles`: List IAM grantable roles for a resource.<br>
gcloud iam roles create: Create a custom role for a project or org.<br>
gcloud iam service-accounts create: Create a service account for a project.<br>
gcloud iam service-accounts add-iam-policy-binding: Add an IAM policy binding to a service account.<br>
gcloud iam service-accounts set-iam-policy-binding: Replace existing IAM policy binding.<br>
gcloud iam service-accounts keys list: List a service account's keys.<br>


###### Docker & Google Kubernetes Engine (GKE)<br>
Manage containerized applications on Kubernetes

gcloud auth configure-docker: Register the gcloud tool as a Docker credential helper.<br>
gcloud container clusters create: Create a cluster to run GKE containers.<br>
gcloud container clusters list: List clusters for running GKE containers.<br>
gcloud container clusters get-credentials: Update kubeconfig to get kubectl to use a GKE cluster.<br>
gcloud container images list-tags: List tag and digest metadata for a container image.<br>


##### Virtual Machines & Compute Engine<br>
Create, run, and manage VMs on Google Cloud infrastructure

gcloud compute zones list: List Compute Engine zones.<br>
gcloud compute instances describe: Display a VM instance's details.<br>
gcloud compute instances list: List all VM instances in a project.<br>
gcloud compute disks snapshot: Create snapshot of persistent disks.<br>
gcloud compute snapshots describe: Display a snapshot's details.<br>
gcloud compute snapshots delete: Delete a snapshot.<br>
gcloud compute ssh: Connect to a VM instance by using SSH.<br>


##### Serverless & App Engine<br>
Build highly scalable applications on a fully managed serverless platform

gcloud app deploy: Deploy your app's code and configuration to the App Engine server.<br>
gcloud app versions list: List all versions of all services deployed to the App Engine server.<br>
gcloud app browse: Open the current app in a web browser.<br>
gcloud app create: Create an App Engine app within your current project.<br>
gcloud app logs read: Display the latest App Engine app logs.<br>


##### Miscellaneous<br>
Commands that might come in handy

gcloud kms decrypt: Decrypt ciphertext (to a plaintext file) using a Cloud Key Management Service key.<br>
gcloud logging logs list: List your project's logs.<br>
gcloud sql backups describe: Display info about a Cloud SQL instance backup.<br>
gcloud sql export sql: Export data from a Cloud SQL instance to a SQL file.<br>


##### Introductory primer<br>
A quick primer for getting started with the gcloud tool.


##### Installing the Cloud SDK <br>
Install the Cloud SDK with these installation instructions.

Flags, arguments, and other wondrous additions<br>
Arguments can be Positional args or Flags


Positional args: Set after command name; must respect order of positional args.<br>
Flags: Set after positional args; order of flags doesn’t matter.


#### A flag can be either a:

`Name-value pair` (--foo=bar), or<br>
`Boolean` (--force/no-force).<br>



#### Required

Optional: in which case, the default value is used, if the flag is not defined<br>


Global flags<br>
Some flags are available throughout the gcloud tool experience, like:

--help: For when in doubt; display detailed help for a command.<br>
--project: If using a project other than the current one.<br>
--quiet: Disabling interactive prompting (and applying default values for inputs).<br>
--verbosity: Can set verbosity levels at debug, info, warning, error, critical, and none.<br>
--version: Display gcloud version information.<br>
--format: Set output format as config, csv, default, diff, disable, flattened, get, json, list, multi, none, object, table, text, value, or yaml.


##### Cleaning up results<br>
Get the most from your output with the filter, format, limit, and sort-by flags.<br>


For Compute Engine instances with prefix us and not machine type f1-micro:


`gcloud compute instances list --filter="zone ~ ^us AND -machineType:f1-micro"`
For a list of projects created on or after 15 January 2018, sorted from oldest to newest, presented as a table with project number, project id and creation time columns with dates and times in local timezone:


gcloud projects list --format="table(projectNumber,projectId,createTime.date(tz=LOCAL))"
--filter="createTime>=2018-01-15T12:00:00" --sort-by=createTime
For a list of ten Compute Engine instances with a label my-label (of any value):


gcloud compute instances list --filter="labels.my-label:*" --limit=10
Understanding commands
The underlying patterns for gcloud tool commands; to aid self-discovery of commands.

Finding gcloud tool commands
The gcloud tool is a tree; non-leaf nodes are command groups and leaf nodes are commands. (Also, tab completion works for commands and resources!)

Most gcloud commands follow the following format:


gcloud + release level (optional) + component + entity + operation + positional args + flags
For example: gcloud + compute + instances + create + example-instance-1 + --zone=us-central1-a

Release level
Release Level refers to the command’s release status.

Example: alpha for alpha commands, beta for beta commands, no release level needed for GA commands.

Component
Component refers to the different Google Cloud services.

Example: compute for Compute Engine, app for App Engine, etc.

Entity
Entity refers to the plural form of an element or collection of elements under a component.

Example: disks, firewalls, images, instances, regions, zones for compute

Operation
Operation refers to the imperative verb form of the operation to be performed on the entity.

Example: Common operations are describe, list, create/update, delete/clear, import, export, copy, remove, add, reset, restart, restore, run, and deploy.

Positional args
Positional args refer to the required, order-specific arguments needed to execute the command.

Example: <INSTANCE_NAMES> is the required positional argument for gcloud compute instances create.

Flags
Flags refer to the additional arguments, --flag-name(=value), passed in to the command after positional args.

Example: --machine-type=<MACHINE_TYPE> and --preemptible are optional flags for gcloud compute instances create.
