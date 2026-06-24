# Secret
### PATH
* **kv/terraform**
### Attribute
* api-token
    * TerraformがProxmoxを操作するためのAPIキー
    * ```{TOKEN_ID}={TOKEN_SECRET}```
* endpoint
    * ProxmoxノードのURL
* repo-url
    * Terraform Podにリポジトリをクローンするために使用する
    * Terraformリソース定義ファイルのリポジトリのURL
    * ```https://{USER}:{TOKEN}@gitlab.newvia.net/{REPOSITORY}.git```
* ssh-username
    * ProxmoxノードにSSH接続するためのユーザのユーザ名
* ssh-password
    * ProxmoxノードにSSH接続するためのユーザのパスワード
* vm-username
    * Proxmox上に建てられたVMの、Cloud-initで作成されるユーザのユーザ名
* vm-password
    * Proxmox上に建てられたVMの、Cloud-initで作成されるユーザのパスワード

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/terraform"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/terraform",
    "bound_service_account_names": "terraform-sa",
    "bound_service_account_namespaces":"terraform",
    "policies":"terraform",
    "ttl":"24h"
}
```