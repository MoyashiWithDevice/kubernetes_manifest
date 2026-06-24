# Secret
### PATH
* **kv/cloudflare-tunnel**
### Attribute
* token
    * Cloudflare Tunnelのコネクタ登録時に表示されるトークンを格納

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/cloudflare-tunnel"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/cloudflare",
    "bound_service_account_names": "cloudflare-sa",
    "bound_service_account_namespaces":"cloudflared",
    "policies":"cloudflare",
    "ttl":"24h"
}
```