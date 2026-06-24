# Secret
### PATH
* **kv/gitlab**
### Attribute
* k8s-repo-url
    * Daemonsetで全ノードで同期するために使用する
    * KubernetesマニフェストリポジトリのURL
* runner-registration-token
* runner-token
    * Gitlab-Runnerを動かすために使用する

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/gitlab"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/gitlab",
    "bound_service_account_names": "gitlab-sa",
    "bound_service_account_namespaces":"gitlab",
    "policies":"gitlab",
    "ttl":"24h"
}
```