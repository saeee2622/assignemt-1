# define the provider
provider "aws" {
 region = "us-east-1" # change into your desired state
 }

 # create a vpc
 resource "aws_vpc" "my_vpc" {
  cidr_bblock = "10.0.0.0/16"
  }

  # create a public subnet
resource "aws_subnet" "public_subnet" {
vpc_id = "06e22be9dfab4eac"
cidr_block = "10.0.0.0/24"
}
   # create a private subnet
 resource "aws_subnet" "private_subnet" {
 vpc_id = "06e22be9dfab4eac"
 cidr_block = "10.0.1.0/24"
  }
     # create a EC2 instance
 resource "aws_instance" "my_instance"
 ami = "ami-oc55b159cbfafe1f0"  # replace with your desired ami
 instance_type = "t2.micro"
 subnet_id = aws_subnet "06e22be9dfab4eac"

  root_block_device {
  volume_size = 8
  volume_type = "gp2"
  }

  tags = {
   Name = "myinstance"
   purpose = "assignment"
   }
   }
  # create a security group
  resource "aws_security_group"
  "my_security_group" {
    name_prefix = "093b4253344c20801"

   ingress {
    from_port = 22
    to_port = 22
    protocol = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
    }
    egress {
     from_port = 0
     to_port = 0
     protocol = "-1"
     cidr_blocks = ["0.0.0.0.0"]
    }
    }
    # attach the security group to the EC2 instance
    resource "aws_network_interface_sg_attachment"
    
