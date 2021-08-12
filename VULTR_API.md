# Vultr API v1 (Deprecated)

More details about how to use could be find in https://www.vultr.com/api/

The information related here is to explain in a quick way how you can get the references
used to deploy new servers, and addapt your env on your requirements

* Ensure to exported your api key:
```bash 
export VULTR_API_KEY='ABCDEFGHIJKLMNOPQRS0123456789'
```

* vultr_region
```bash 
curl -s "https://api.vultr.com/v1/regions/list" -X GET | jq '.[] | { id: .DCID, name: .name } '
curl -s "https://api.vultr.com/v1/regions/list" -X GET | jq '.[] | select( .country | contains("DE")) | { id: .DCID, name: .name }'
```

* vultr_planid
```bash 
curl -s "https://api.vultr.com/v1/plans/list?type=vc2" | jq '.[] | select ( .ram == "8192" ) '
```

* vultr_osid
```bash 
curl -s "https://api.vultr.com/v1/os/list" -X GET | jq '.[] | select ( .family | contains("ubuntu"))'
```

* vultr_sshkeyid:
```bash 
curl -s "https://api.vultr.com/v1/sshkey/list" -X GET -H "API-Key: ${VULTR_API_KEY}" | jq '.[]'
```

* snapshotid:
```bash 
curl -s "https://api.vultr.com/v1/snapshot/list" -X GET -H "API-Key: ${VULTR_API_KEY}" | jq '.[]'
```
