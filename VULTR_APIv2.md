# Vultr API (2.0)

More details about how to use could be find in https://www.vultr.com/api/

The information related here is to explain in a quick way how you can get the references
used to deploy new servers, and addapt your env on your requirements

* Ensure to exported your api key:
```bash 
export VULTR_API_KEY='ABCDEFGHIJKLMNOPQRS0123456789'
```

* vultr_region
```bash 
curl -s "https://api.vultr.com/v2/regions" -X GET | jq '.regions[] | { id: .id, name: .city } '
curl -s "https://api.vultr.com/v2/regions" -X GET | jq '.regions[] | select( .country | contains("DE")) | { id: .id, name: .city }'
```

* vultr_planid
```bash 
curl -s "https://api.vultr.com/v2/plans" -X GET | jq '.plans[] | select( .locations[] | contains("fra")) | select ( .ram == 8192 ) | select ( .type == "vc2" ) '
```

* vultr_osid
```bash 
curl -s "https://api.vultr.com/v2/os" | jq '.os[] | select ( .family | contains("ubuntu"))'
```

* vultr_sshkeyid:
```bash 
curl -s "https://api.vultr.com/v2/ssh-keys" -X GET -H "Authorization: Bearer ${VULTR_API_KEY}" | jq '.ssh_keys[]'
```

* List snapshots
```bash 
curl -s "https://api.vultr.com/v2/snapshots" -X GET -H "Authorization: Bearer ${VULTR_API_KEY}" | jq '.snapshots[]'
```

* List startup scripts 
```bash 
curl -s "https://api.vultr.com/v2/startup-scripts" -X GET -H "Authorization: Bearer ${VULTR_API_KEY}" | jq '.startup_scripts[]'
```

* List instances 
```bash 
curl -s "https://api.vultr.com/v2/instances" -X GET -H "Authorization: Bearer ${VULTR_API_KEY}" | jq '.instances[]'
```
