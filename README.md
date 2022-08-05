# devops-cornerstone-project
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.27"
    }
  }

  required_version = ">= 0.14.9"
}



resource "aws_instance" "TomcatServer" {
  ami            = "ami-090fa75af13c156b4"
  instance_type  = "t2.micro"
  key_name       = "DevopsKP"
  security_groups = ["WideOpen-sg"]

  tags = {
    Name = "TomcatServer-Terraform"
  }
  user_data = file("tomcat-install.sh")
}
