# Secret
### PATH
* **kv/mkeys**
### Attribute
* repo-url
    * GithubからMkeysリポジトリをクローンするために使用
    * ```https://{USERNAME}:{TOKEN}@github.com/{REPOSITORY}.git```

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/mkeys"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/mkeys",
    "bound_service_account_names": "mkeys-sa",
    "bound_service_account_namespaces":"mkeys",
    "policies":"mkeys",
    "ttl":"24h"
}
```