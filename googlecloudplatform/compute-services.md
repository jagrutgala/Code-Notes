# Google Cloud Compute Services
Google Cloud provides multiple services with varying amount of flexibility and control. Some of the important ones are Compute Engine, Google kubernetes Engine, Cloud Function, etc...

List of Googles Compute Services (covered here):
1. [Compute Engine](#compute-engine)
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
- Zone
- Machine-Type (vCpu + Memory)
- Disk Storage
- Image
- Network (VPC + Subnet)

We can use the Cloud Console to create and manage (update, start, stop, delete) VM instances or also use gcloud CLI. When we want to create multiple VM instances with little changes it is easier to do using gcloud CLI. Some of the common compute commands you are:
1. Creating VM instances using `gcloud compute instances create`. Example command:
    ```
    $ gcloud compute instances create example-instance --image-family=rhel-8 --image-project=rhel-cloud --zone=us-central1-a
    ```
    For full documentation on `gcloud compute instances create` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create)

1. Listing out available instances to see and perform further action using instance details. Below are couple examples with commonly used flags.
    ```
    $ gcloud compute instances list --zones=us-central1-a,us-central1-b,us-central1-c --format=table

    $ gcloud compute instances list --filter=machineType~'f1-micro' --limit=10 --sort-by=name --format=table

    $ gcloud compute instances list --filter=name~'*-developer' --uri --format=table
    ```
    `--uri` is a commonly used to list out instances with the accessible url for that instance. <br>
    For full documentation on `gcloud compute instances list` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/list)

1. We can use the start and stop commands to boot-up and shut-down the VM. Example command:
    ```
    $ gcloud compute instances stop example-instance --zone=us-central1-a

    $ gcloud compute instances start example-instance --zone=us-central1-a
    ```
    Also alternatively you can use `gcloud compute instances suspend` to put the VM instance in hibernate or standby mode. <br>
    For full documentation on `gcloud compute instances start` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/start) <br>
    For full documentation on `gcloud compute instances stop` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/stop) <br>
    For full documentation on `gcloud compute instances suspend` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/suspend)

1. Now to update the VM instance configuration you would think `gcloud compute instances update` is how you do it, but the actually you can only update the labels and Cpu Platform using it. <br>
    To actually update the VM instance and upgrade you instance configuration use `gcloud compute instances update-from-file`.
    ```
    $ gcloud compute instances update-from-file example-instance --source=example-instance-config.yaml
    ```
    **vm-instance-config.yaml**
    ```yaml
    <!-- TODO - Add sample yaml file for VM instance configuration -->
    ```
    For full documentation on `gcloud compute instances update-from-file` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update-from-file)

1. After you are done with your VM instance you want to delete it.
    When deleting it you have option to keep the disk and the data associated with the instance, using the `--keep-disks=all|boot|data` flag or choose to delete it disk using `--delete-disks=all|boot|data` flag.
    `--delete-disks` & `--keep-disks` are mutually exclusive options.
    ```
    $ gcloud compute instances delete example-instance --zone=us-central1-a [--delete-disks=all|boot|data] [--keep-disks=all|boot|data]
    ```
    PS. if you choose to keep the data you would still be charged for the disk storage. But you can reuse that disk to spin up a new VM instance with the persistent data intact. <br>
    For full documentation on `gcloud compute instances delete` [click here](https://cloud.google.com/sdk/gcloud/reference/compute/instances/delete)


### Instance Templates
Let's say you need to create a new VM instance with a exact same configuration every time you hire a new developer. What do you do ? D you memorize each and every detail in the configuration ?

You can create a "Instance Template" that when applied to instances creates a reliable way to create replicable VM instances. You can use the Cloud Console to create a new instance template or convert an existing VM to create a template based on that.

Some commands example commands you can use to do the same using gcloud CLI:
1. Create a new "Instance Template" using a source VM instance
    ```
    $ gcloud compute instance-templates create my-custom-instance-template --source-instance=example-instance
    ```
1. List available "Instance Templates"
    ```
    $ gcloud compute instance-templates list --format=table
    ```
1. Delete "Instance Template"
    ```
    $ gcloud compute instance-templates delete my-custom-instance-template
    ```


### Instance Groups
In compute engine you can create compute instance groups to organize and manage multiple VM instances together. There are 2 types of instance groups: Managed & Unmanaged Instance Groups.

Managed instance group is a instance group created using a "Instance Template" and all the instances in the group are managed and auto automatically handled via the group configuration. All instances in the group are identical in configuration.

Unmanaged instance group is a instance group created without using a Instance Template. All instances in the group are not necessary to be identical in configuration.

Feature of Managed Instance Group:
- **Auto Scaling**: automatic adjustment to the number of instances based on the load.
- **Auto Healing**: automatic health-check and relaunch defective instances.
- **Rolling Update**: gradual update of instances in an instance group to a new template without downtime.
- **Canary Testing Support**: when you test update a percentage of instances to new template to do test before rolling it out to 100% of instances.

<!-- TODO - Managed Instance Groups CLI commands -->
<!-- Operations (create, list, resize, restart, set instance-template) -->

### Health Checks
In Compute Engine managed instance group allow you to setup health checks for your instances. A "Health Check" is a ping to your service that would determine if the service is healthy and can keep serving traffic or if unhealthy needs to be replaced.

Health Checks along with "Auto Healing" creates a robust collection of instances that can self-repair automatically and continue serving traffic indefinitely.


Let's see how you would set up "Auto Scaling" & "Health Check" for a Managed Instance Group (MIG)
<!-- TODO - managed instance group set autoscaling, healthcheck commands -->


### Images
Images store the boot disk capturing the OS and any other softwares installed and data stored on it. We can use it to create a "Custom Image" with all the software and data preinstalled needed for any member in organization.

It is quick to create a VM using a custom image and saves a lot of time customizing and reinstalling all the software again and again.

<!-- TODO - Images & Managing Images in gcloud CLI -->

What we can do is take this further with "Machine Images". Machine Images not only store the OS and software installed on the boot disk, but also the VM configuration, metadata and permissions. Making it very easy to replicate a particular VM over and over again.

<!-- TODO - Images & Managing Images in gcloud CLI -->


### Snapshots
Snapshots take a incremental point in time of the disk attached to VM generally the boot disk. It can be scheduled to be taken automatically.

Covered in more detail with [Persistent Disks in Storage Services](./storage-services.md/#persistent-disks).


### Sole-Tenant Nodes
Sole-Tenants are dedicated computers that you can rent out. Sole-Tenants are more expensive than regular VMs, but you get to keep the rights to the resources for the duration of the rent-out.

Important thing to note is that sole tenants cost you event if the node is down because you are reserving the resources for the node which costs the money, It is not pay as you use!


## Google Kubernetes Engine



## App Engine



## Cloud Functions



## Cloud Run

