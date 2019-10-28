Terraform Remote State
=================================================

Create an S3 Bucket

Search for S3 in Find Services.
    
    Click Create Bucket.
    Enter a Bucket name. The bucket name must be unique.
    Make sure the Region is US East (N. Virginia) Click Next.
    Click Next again on the Configure options page.
    Click Next again on the Set permissions page.
    Click Create bucket on the Review page.
    
Add the Terraform Folder to the Bucket

    Click on the bucket name.
    Click Create folder.
    Enter terraform-aws-play for the folder name.
    Click Save.
    
Then Add Backend to Your Scripts

Go AWS folder

Set the Environment Variables

export AWS_ACCESS_KEY_ID="[ACCESS_KEY]"
export AWS_SECRET_ACCESS_KEY="[SECRET_KEY]]"
export AWS_DEFAULT_REGION="us-east-1"

Create terraform.tf:

    vi terraform.tf

terraform.tf contents:

    terraform {
      backend "s3" {
        key    = "terraform-aws/terraform.tfstate"
      }
    }

Initialize Terraform:

    terraform init -backend-config "bucket=[BUCKET_NAME]"

Validate changes:

    terraform validate

Plan the changes:

    terraform plan

Apply the changes:

    terraform apply -auto-approve

Destroy environment:

    terraform destroy -auto-approve

