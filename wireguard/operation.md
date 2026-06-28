# Secret
### PATH
* **kv/wireguard**
### Attribute
* private_key
    * WireguardクライアントのInterfaceに設定する秘密鍵
* public_key
    * PeerとなるWireguardサーバの公開鍵
* server_ip
* server_port
    * PeerとなるWireguardサーバのエンドポイントを指定する
    * ```Endpoint = ${server_ip}:${server_port}     # /config/wg_confs/wg0.conf``` 

# Vault
### policy
```hcl:vault-policy.hcl
path "kv/data/wireguard"{
    capabilities = ["read", "list"]
}
```

### role
```json:role.json
{
    "description": "vault write auth/kubernetes/role/wireguard",
    "bound_service_account_names": "wireguard-sa",
    "bound_service_account_namespaces":"wireguard",
    "policies":"wireguard",
    "ttl":"24h"
}
```