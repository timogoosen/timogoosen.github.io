### Notes on GCP

Some notes on GCP.


### KMS

KMS Secret Terraform Provider

* [KMS Secret Terraform Provider](https://registry.terraform.io/providers/hashicorp/google/latest/docs/data-sources/kms_secret)

KMS Encrypt secret on the CLI:

```
echo -n my-secret-password | gcloud kms encrypt \
> --project my-project \
> --location us-central1 \
> --keyring my-key-ring \
> --key my-crypto-key \
> --plaintext-file - \
> --ciphertext-file - \
> | base64
CiQAqD+xX4SXOSziF4a8JYvq4spfAuWhhYSNul33H85HnVtNQW4SOgDu2UZ46dQCRFl5MF6ekabviN8xq+F+2035ZJ85B+xTYXqNf4mZs0RJitnWWuXlYQh6axnnJYu3kDU=

```