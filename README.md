# multicloud-scenario
A scenario that use service component and composition of  for DB, LB and application across different private and public clouds- Azure, AWS, Openstack


this service composition of multi-cloud scenario is taking several existing blueprints and handle them as independent component using Servicecomponent type.
it creates an application with 3 tiers-
DB, LB and frontend, and based on the composition, it statge the tiers on different cloud infrastructures.

multicloud-openstack-aws.yaml- creates the DB, LB on AWS (with VPC network), stage a kubernetes on Openstack and isnatll a wordpress app as docker on kubernetes
multicloud-openstack-azure.yaml- creates the DB, LB on AZURE (with azure network), stage a kubernetes on Openstack and isnatll a wordpress app as docker on kubernetes
multicloud-openstack.yaml- creates the DB, LB , kubernetes on Openstack and isnatll a wordpress app as docker on the kubernetes


requires the below secrets created on the manager (masked values for privacy)-

=====================================================================OPENSTACK
cfy secrets create openstack-external-network -s XXXXXXXX
cfy secrets create keystone_password -s xxxxxxxxxx
cfy secrets create keystone_region -s RegionOne
cfy secrets create keystone_tenant_name -s xxxxxxxxxxx
cfy secrets create keystone_url -s https://xxxxxx:5000/v3
cfy secrets create keystone_username -s xxxxxxx
cfy secrets create centos_image_id -s xxxxxxxxxxx
cfy secrets create centos_flavor_id -s xxxxx

=====================================================================AWS
#create aws secrets-
cfy secrets create aws_access_key_id -s xxxxxxxxxx
cfy secrets create aws_secret_access_key -s xxxxxxxxxxxx
cfy secrets create ec2_region_name -s xxxxxxx
cfy secrets create ec2_region_endpoint -s xxxxxxxxxxx
cfy secrets create availability_zone -s xxxxxxxxx
cfy secrets create aws_availability_zone -s xxxxxxx
cfy secrets create aws_region_name -s xxxxxxx

=====================================================================AZURE

cfy secrets create azure_client_id -s <azure_client_id>
cfy secrets create azure_client_secret -s <azure_client_secret>
cfy secrets create azure_subscription_id -s <azure_subscription_id>
cfy secrets create azure_tenant_id -s <azure_tenant_id>
cfy secrets create azure_location -s <azure_location>
