# MTA-STS Policy — carwise.com.uy

This repository hosts the [MTA-STS](https://datatracker.ietf.org/doc/html/rfc8461) policy file for `carwise.com.uy` via GitHub Pages.

MTA-STS instructs sending mail servers to use TLS when delivering email to this domain, preventing downgrade attacks on inbound mail.

## Policy file

Served at: `https://mta-sts.carwise.com.uy/.well-known/mta-sts.txt`

## Updating the policy

1. Edit `.well-known/mta-sts.txt`
2. Update `mta_sts_policy_id` in `environments/prod/main.tf` (terraform repo) to signal the change
3. Run `terraform apply` on prod to update the `_mta-sts` TXT record

## DNS records (managed in Terraform)

| Record | Type | Value |
|--------|------|-------|
| `_mta-sts.carwise.com.uy` | TXT | `v=STSv1; id=<policy_id>` |
| `mta-sts.carwise.com.uy` | CNAME | `carwiseuy.github.io` |
