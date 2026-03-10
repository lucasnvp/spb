# Terraform

## Alias in my Zshconfig

```
alias tfi="terraform init"
alias tfp="terraform plan"
alias tfa="terraform apply"
```

## Modules

## Import from created resources

This is a resume for delete the terraform state and import the resource again. 
That happend when the resource is change in the UI and you need to replecated in the terraform files.

`tfp <resource>`
`terraform state rm <resource>`
`terraform import <module name terraform file> <reource name in AWS>`
