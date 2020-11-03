## Load Secrets manager secrets from KMS:

If you don't want to load secrets in plaintext into your state then
you can use secrets in KMS to create aws secrets manager secrets.
Here is an example:


```

variable "dd_api_key" {
  type = string
}


# Then put the encrypted secret in a file like app/prod.tfvars
# in this format inside the file:
# dd_api_key = "ENCRYPTED SECRET GOES HERE"

data "aws_kms_secrets" "datadog" {
  secret {
    name    = "apikey"
    payload = var.dd_api_key
  }


}

resource "aws_ssm_parameter" "dd_api_key" {
  name   = "/${terraform.workspace}/${var.app_name}/datadog/apikey"
  type   = "SecureString"
  value  = data.aws_kms_secrets.datadog.plaintext["apikey"]
  key_id = data.terraform_remote_state.env.outputs.kms_params_arn

  tags = local.tags
}




resource "aws_secretsmanager_secret" "dd_api_key" {
  name = "datadog_api_key-${terraform.workspace}"
  description = "Encrypted Datadog API Key"
  recovery_window_in_days = 0
}

resource "aws_secretsmanager_secret_version" "dd_api_key" {

  secret_id = aws_secretsmanager_secret.dd_api_key.id
  secret_string = data.aws_kms_secrets.datadog.plaintext["apikey"]
}


```