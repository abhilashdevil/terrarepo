# this file consists of code for instance and sg
provider "aws" {
region = "ap-south-1"
access_key = "AKIATGRQRTHKM5OU5MNJ"
secret_key = "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"
}

resource "aws_instance""one"{
ami             ="ami-0b08bfc6ff7069aff"
instance_type   ="t2.micro"
key_name        ="keypair1"
vpc_security_group_ids = "sg-08c65b9a16eb33ff6"
availability_zone = "ap-south-1a"
user_data      = <<EOF
#!/bin/bash
sudo -i
yum install httpd -y
systemctl start httpd
chkconfig httpd on
echo "hai all this is my app created by terraform infrastructure by abhilash server-1" > /var/www/html/index.html
EOF
  tags = {
  Name = "server-1"
 }
}
 
resource "aws_instance" "two" {
  ami           = ""
  instance_type = "t2.micro"
  key_name      = "eks"
  vpc_security_group_ids = [aws_security-group.three.id]
  availability_zone = "ap-south-1b"
  user_data     = <<EOF
#!/bin/bash
sudo -i-2-
yum install httpd -y
systemctl start httpd
chkconfig httpd on
echo "hai all this my website created by terraform infrastructure by abhilash server-2 > /var/www/html/index.html
EOF
  tags = {
   Name = "server-2"
  }
}
  
  resource "aws_security_group" "three" {
   name = "elb-sg"
   ingress {
    from_port  = 22
    to_port    = 22
    protocol   = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
  
  ingress {
    from_port  = 80
    to_port    = 80
    protocol   = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
  
  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
  
resource ="aws-s3_bucket" "four" {
  bucket = "abhilashdevil
}
  
resource "aws-iam_user" "five" {
name = ""
}
  
resource "aws_ebs_volume" "six" {
 availability_zone = "ap-south-1b"
  size = 40
  tags {
    Name = "ebs-001"
 }
}
