1. Credentialを定義したJSONファイルを作成
```yaml: cred.yaml
---
- name: discord_webhook_url
  value: https://...
```

2. 以下のコマンドを実行し、Credentialをデータストアにロード
```bash
st2 key load cred.yaml
```
