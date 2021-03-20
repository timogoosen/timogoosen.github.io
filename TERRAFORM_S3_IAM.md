## Terraform IAM Examples for AWS:

Public bucket no dir listing. Only allow bucket access over SSL:

```

resource "aws_s3_bucket" "images-bucket" {
  bucket        = "images-bucket-${terraform.workspace}"   # If run on stage images-bucket-staging

}

data "aws_iam_policy_document" "images-bucket-policy" {

  statement {
    sid = "AllowSSLRequestsOnly"

    effect = "Allow"

    actions = ["s3:GetObject"]

    resources = [
      "${aws_s3_bucket.images-bucket.arn}/*",

    ]

    condition {
      test     = "Bool"
      variable = "aws:SecureTransport"
      values = [
        "true",
      ]
    }

    principals {
      type        = "*"
      identifiers = ["*"]
    }

  }
}

resource "aws_s3_bucket_policy" "images-bucket-policy" {
  bucket = aws_s3_bucket.images-bucket.id
  policy = data.aws_iam_policy_document.images-bucket-policy.json
}

```