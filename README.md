# application
community application release
## configuration
If any pairs don't apply, comment them out.
### aws
Certain _key:value_ pairs can be configured per project. Others should remain fixed for all projects.

These values should remain unchanged.

    cloud: aws
Replace TENANT with the name of the AWS_PROFILE environment variable. 
    
    tenant: TENANT
Replace PROJECT_NAME with the name of the project hosting the instances. 

    project: PROJECT_NAME
Replace DOMAIN with a `production` or `development` (or another value of your choosing).

    domain: DOMAIN
These values should remain unchanged.
    
    application: application
Replace REGION with your desired AWS region such as `us-east-1` or `ap-southeast-2`.

    region: REGION    
The following settings are optional. If not defined, they will be replaced with the string `none`.

    cluster: a
    role: none
    dataflow: none
Replace REPLICA with a `yes` or `no` to indicate whether you want a standalone server or master/replica pair.

    replica: yes
Replace USER with `centos` for CentOS or `redhat` for RHEL.

    user: USER
Replace AMI with the AMI ID in the region you wish to deploy; Centos 7.3 or RHEL 7.3 are supported. If commented out or removed, CentOS 7.3 will be booted.

    image: AMI
Replace SIZE with  `t2.micro`, `t2.small`, `t2.medium`, `t2.large`, `t2.xlarge`, `t2.x2large`,  or another value from [here](https://aws.amazon.com/ec2/instance-types/).

    type: SIZE
Replace SIZE with the size of the root or data volume in GB, e.g, `20` for 20gig or `2000` for 2TB. `11` is a reasonable value for the root volume.

    root_volume: SIZE
    data_volume: SIZE
Replace CIDR_BLOCK and SUBNET with the values in the VPC, e.g., 172.31.0.0/16, 172.31.1.0/24, 172.31.2.0/24. The internal subnet is private and non-routable, the external subnet will outbound routing.
    
    cidr_block: CIDR
    internal_subnet: SUBNET
    external_subnet: SUBNET
(if needed) Replace  PROXY with `yes` or `no` if there is an HTTP proxy involved in getting to the internet.
 
    http_proxy: http://USER:PASSWORD@DOMAIN:PORT

### azure
Certain _key:value_ pairs can be configured per project. Others should remain fixed for all projects.

These values should remain unchanged.

    cloud: azure
Replace TENANT with the name of the AWS_PROFILE environment variable. 
    
    tenant: TENANT
Replace PROJECT_NAME with the name of the project hosting the instances. 

    project: PROJECT_NAME
Replace DOMAIN with a `production` or `development` (or another value of your choosing).

    domain: DOMAIN
These values should remain unchanged.
    
    application: application
Replace REGION with your desired AWS region such as `eastus` or `southcentralus`.

    region: REGION    
The following settings are optional. If not defined, they will be replaced with the string `none`.

    role: none
    dataflow: none
Replace USER with `centos` for CentOS or `redhat` for RHEL.

    user: USER
Replace IMAGE with the  ID in the region you wish to deploy `Standard_A0`, `Standard_D8_v3`, or another value from [here](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes).

    image: IMAGE
Replace SIZE with the size of the root or data volume in GB, e.g, `20` for 20gig or `2000` for 2TB. `11` is a reasonable value for the root volume.

    data_volume: SIZE
Replace CIDR_BLOCK and SUBNET with the values in the VPC, e.g., 172.31.0.0/16, 172.31.1.0/24, 172.31.2.0/24. The internal subnet is private and non-routable, the external subnet will outbound routing.
    
    cidr_block: CIDR
    internal_subnet: SUBNET
    external_subnet: SUBNET
(if needed) Replace  PROXY with `yes` or `no` if there is an HTTP proxy involved in getting to the internet.
 
    http_proxy: http://USER:PASSWORD@DOMAIN:PORT
    
### osp
Certain _key:value_ pairs can be configured per project. Others should remain fixed for all projects.

These values should remain unchanged.

    cloud: osp
Replace TENANT with the name of the configure OSP tenant. 

    tenant: TENANT
Replace PROJECT_NAME with the name of the project hosting the instances. 
    
    project: PROJECT
Replace DOMAIN with a `production` or `development` (or another value of your choosing).

    domain: DOMAIN
These values should remain unchanged.

    application: application
Replace REGION with your configured OSP region.

    region: OSP_REGION
The following settings are optional. If not defined, they will be replaced with the string `none`.

    cluster: a
    role: none
    dataflow: none
Replace REPLICA with a `yes` or `no` to indicate whether you want a standalone server or master/replica pair.

    replica: REPLICA
Replace USER with `centos` for CentOS or `redhat` for RHEL.

    user: USER
Replace IMAGE_UUID with the UUID of the image you wish to boot.

    image: IMAGE_UUID
Replace SIZE with  configured virtual machine size.

    type: TYPE
Replace SIZE with the size of the root or data volume in GB, e.g, `20` for 20gig or `2000` for 2TB. `11` is a reasonable value for the root volume. If booting from an image, this is ignored.

    root_volume: SIZE
    data_volume: SIZE
Replace POOL with any configured block pool, e.g., ScaleIO or Ceph.

    block_pool: POOL
Replace  SUBNET with the configured values, e.g., 172.31.1.0/24, 172.31.2.0/24. The internal subnet is private and non-routable, the external subnet will outbound routing.
    
    internal_subnet: SUBNET
    external_subnet: SUBNET
Replace  FLOAT with the floating IP pool, e.g., external. 
    
    float_pool: FLOAT
Replace SUBNET_UUID with the UUID's of the internal and external subnets.

    internal_uuid: SUBNET_UUID
    external_uuid: SUBNET_UUID
Replace ZONE with the configured OSP zone.

    zone: ZONE 
(if needed) Replace USER, PASSWORD, DOMAIN, PORT with the necessary values.

    http_proxy: http://USER:PASSWORD@DOMAIN:PORT
    
## deployment
### amazon web services
You will  want to set your AWS_PROFILE to your preferred credentials.

Assuming `aws.yml` is the name of the inventory configuration file.  To deploy the full application:

    ./deploy aws.yml

Expected running times:

* approximately 5minutes 

### azure
You will  want to set your AWS_PROFILE to your preferred credentials.

Assuming `azure.yml` is the name of the inventory configuration file.  To deploy the full application:

    ./deploy azure.yml

Expected running times:

* approximately 5 minutes 

### openstack
Assuming `osp.yml` is the name of the inventory configuration file.  To deploy the full application:

    ./deploy osp.yml

Expected running times:

* approximately 5 minutes 