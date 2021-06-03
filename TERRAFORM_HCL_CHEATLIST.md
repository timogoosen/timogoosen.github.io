## Cheatlist in HCL:

Don't create resource for workspace/environment.
For example don't create for prod:

```

count = terraform.workspace != "prod" ? 1 : 0

```

Use that in resource so for example:

```
resource "aws_sns_topic" "main" {
  count = terraform.workspace != "prod" ? 1 : 0
  name              = "${var.app_name}.fifo"
  fifo_topic        = true

}

```

Using count in IAM policy document:

```

data "aws_iam_policy_document" "sqs_policy" {
  count = terraform.workspace != "prod" ? 1 : 0

  statement {
    actions = ["SQS:SendMessage"]

    principals {
      type        = "*"
      identifiers = ["*"]
    }

    resources = [aws_sqs_queue.main[count.index].arn]

    condition {
      test     = "ArnEquals"
      variable = "aws:SourceArn"
      values   = [aws_sns_topic.main[count.index].arn]
    }
  }
}

```