# AngularAws project setup

# Install the angular cli
npm install -g @angular/cli

# Setup/Create the project 
ng new angular-aws

# Test if the project is working
ng serve

# Bucket policy used:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::bucket-name/*"
        }
    ]
}

# Update the IAM policy to be used by Codebuild service role.

{
    "Effect": "Allow",
    "Action": [
        "s3:PutObject",
        "s3:GetObjectAcl",
        "s3:GetObject",
        "s3:DeleteObjectVersion",
        "s3:GetObjectVersionAcl",
        "s3:ListBucket",
        "s3:DeleteObject",
        "s3:PutObjectAcl",
        "s3:GetObjectVersion",
        "s3:ListObject*"
    ],
    "Resource": [
        "arn:aws:s3:::bucket-name/*",
        "arn:aws:s3:::bucket-name"
    ]
}
