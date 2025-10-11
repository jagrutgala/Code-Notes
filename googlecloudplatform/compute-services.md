# Google Cloud Compute Services
Google Cloud provides multiple services with varying amount of flexibility and control. Some of the important ones are Compute Engine, Google kubernetes Engine, Cloud Function, etc...

List of Googles Compute Services (covered here):
1. [Compute Engine]()
1. [Google Kubernetes Engine]()
1. [App Engine]()
1. [Cloud Functions]()
1. [Cloud Run]()


## Terminology

- **Machine-Family**: Set of similar Machines/Systems all optimized for a specific need
- **Machine-Type**: Machines/Systems with predefined specs (i.e. vCpu, Memory, & other configurations)
- **Image**: It is a software snapshot of your Operating System and other softwares installed on the machine



## Compute Engine
Compute Engine is a service that provides an API to provision and manage VM Instances. Features of Compute-Engine include:
- VM Instances
- Instance Templates
- Instance Groups
- Snapshots
- Images
- Health Checks
- Sole-Tenant Nodes
- Preemptible VM
- Spot VM
- Billing & Discounts


### VM Instances
Compute Engine VM Instances allow you to create & manage VM Instances. To create a VM instance you need a to know the following:
- Zone of the instance
- Machine-Type (vCpu + Memory)
- Disk Storage
- Image
- Network (VPC + Subnet)

Operations you can do with `gcloud compute instances`

1. **Create VM instance** <br>
    [`gcloud compute instances create`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create) is used to create VM instances.
    ```
    $ gcloud compute instances create '<instance-name>' [--zone=<zone_value>] \
    [--machine-type=<machine_type_value>] [image=<image_name_value> | --image-family=<image_family_value>] \
    [--network=<vpc_network_value>] [--subnet=<region_subnet_value>]
    ```
    Available zone_value: `gcloud compute zones list` <br>
    Available machine_type_value: `gcloud compute machine-types list` <br>
    Available image_family_value: `gcloud compute images list` <br>
1. **List VM instance** <br>
    [`gcloud compute instances list`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/list) is used to list available active or inactive VM instances.
    ```
    $ gcloud compute instances list [--regexp=<regexp_value>, -r <regexp_value>] [--zones=zone_value,[zone_value,…]] [--filter=<expression_value>] [--limit=<limit_value>] [--uri]
    ```
    `--uri --format=table` is a commonly used to list out instances with the accessible url for that instance in a nicely organized table format.
1. **Start/Stop VM instance** <br>
    [`gcloud compute instances start`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/start) is used to activate VM instances.
    ```
    $ gcloud compute instances start '<instance-name>' ['<instance-name>'...] [--zone=<zone_value>]
    ```
    [`gcloud compute instances stop`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/stop) is used to deactivate VM instances. Also alternatively you can use `gcloud compute instances suspend` to put the VM instance in sleep/hibernate or standby mode.
    ```
    $ gcloud compute instances stop '<instance-name>' ['<instance-name>'...] [--zone=<zone_value>]
    ```
1. **Update VM instance** <br>
    [`gcloud compute instances update`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update) is used to update or remove labels on VM instances. If you want a new VM instance configurations, use [`gcloud compute instances update-from-file`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update-from-file) or use cloud console.
    ```
    $ gcloud compute instances update <instance-name> --zone=<zone_value> --update-labels=k0=value1,k1=value2 --remove-labels=k3
    ```
1. **Delete VM instance** <br>
    [`gcloud compute instances delete`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/delete) is used to stop and delete VM instances. It will permanently stop and remove the VM instance.
    ```
    $ gcloud compute instances delete <instance-name> [<instance-name> ...] [--zone=zone_value] [--delete-disks=all|boot|data] [--keep-disks=all|boot|data]
    ```
    `--delete-disks` and `--keep-disks` are mutually exclusive options.


### Instance Groups
### Snapshots
### Images
### Health Checks
### Sole-Tenant Nodes



## Google Kubernetes Engine



## App Engine



## Cloud Functions



## Cloud Run

