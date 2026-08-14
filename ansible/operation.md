# Secret
### PATH
* **kv/ansible**
### Attribute
* repo-url
    * Githubからansibleリポジトリをクローンするために使用
    * ```https://{USERNAME}:{TOKEN}@github.com/{REPOSITORY}.git```

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/ansible"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/ansible",
    "bound_service_account_names": "ansible-sa",
    "bound_service_account_namespaces":"ansible",
    "policies":"ansible",
    "ttl":"24h"
}
```
