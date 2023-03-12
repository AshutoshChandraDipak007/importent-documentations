
Configuration pros for creating ci/cd pipeline on aws.

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR_S3_BUCKET_HERE/*"
        }
    ]
}

[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "POST",
            "GET",
            "PUT"
        ],
        "AllowedOrigins": [
            "*"
        ]
    }
]



version: 0.2

phases:
  pre_build:
    commands:
      - npm install
  build:
    commands:
      - npm run build

artifacts:
  files:
    - '**/*'
  discard-paths: no
  base-directory: build
