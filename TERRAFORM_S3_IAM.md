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

Only allow certain public or private IP ranges or IP's to access a bucket:


```


variable "whitelist_s3_ips" {
  type = list(string)

  default = [
    "10.0.0.1/24",
    "192.168.0.1/24",

  ]
}


resource "aws_s3_bucket" "some-bucket" {
  bucket        = "some-bucket-${terraform.workspace}"

}

data "aws_iam_policy_document" "some-bucket-policy" {


  # Allow from IPS

  statement {

    sid = "IPAllow"

    effect = "Allow"

    actions = ["s3:GetObject"]

    resources = [
      "${aws_s3_bucket.some-bucket.arn}/*",
    ]

    condition {
      test     = "IpAddress"
      variable = "aws:SourceIp"

      values = concat(
        var.whitelist_s3_ips,

      )
    }


    principals {
      type        = "*"
      identifiers = ["*"]
    }

  }



resource "aws_s3_bucket_policy" "some-bucket-policy" {
  bucket = aws_s3_bucket.some-bucket.id
  policy = data.aws_iam_policy_document.some-bucket-policy.json
}

```