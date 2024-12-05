### Main branch

## Title
"AWS CLI Microk8s"

## Description
This project is designed to create an EC2 instance in AWS, via the AWS CLI, and install microk8s. It includes 3 files:
- A shell script which contains the AWS CLI code itself,
- A 'device_mapping.json' file which describes the EBS volume to be used by the instance, setting it to 50GB,
- A 'microk8s_script.txt' file, which runs the commands in the EC2 instance to install microk8s.
There should be a default VPC, as well as AWS Security Group with desired access settings (HTTP, HTTPS, SSH) already in place.

## Installation
Clone the repository and place all files into a folder. 
Place the AWS keypair '.pem' file into the folder as well, and amend the 'aws_cli_microk8s.sh' script to use this name in the '--key-name' parameter. Note the '.pem' extension should be removed from this parameter in the script.
Amend the 'image-id' and 'security-group' IDs as needed.
Make the shell script file executable.
Run: 
```
./aws_cli_microk8s.sh
```

When the command is run, it'll produce JSON output, among this will be the `instance-id`. Query this to get the public IP address:

```
aws ec2 describe-instances --instance-id <instance-id-goes-here>
```

## Termination

```
aws ec2 terminate-instances --instance-id <instance-id-goes-here>
```


### Terraform branch

## Description
Creates an AWS EC2 instance with microk8s package installed, in the same way the AWS CLI commands would, using Terraform.

## Installation
Clone the repository.
Run the terraform commands:
```
terraform init
terraform validate
terraform plan
terraform apply
```
The terraform code has an output which will show its public IP address.

## Termination

```
terraform destroy
```
