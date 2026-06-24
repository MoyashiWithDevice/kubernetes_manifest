# Secret
### PATH
* **kv/keycloak**
### Attribute
* kc-admin-username
    * Keycloakセットアップ時の初期ユーザのユーザ名
* kc-admin-password
    * Keycloakセットアップ時の初期ユーザのパスワード
* kc-db-username
    * KeycloakのDBのユーザ名
* kc-db-password
    * KeycloakのDBのパスワード

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/keycloak"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/keycloak",
    "bound_service_account_names": "keycloak-sa",
    "bound_service_account_namespaces":"keycloak",
    "policies":"keycloak",
    "ttl":"24h"
}
```