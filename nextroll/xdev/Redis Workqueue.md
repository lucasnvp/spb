`redis-cli -p 6380 -h localhost -c`

```bash
localhost:6380> keys *:contacts*
1) "deadletter_retries:contacts_v1"
2) "workqueue:contacts_v1"
3) "deadletter:contacts_v1"
```

Para buscar en la Workqueue
`zscan workqueue:contacts_v1 0 MATCH f56e30f4b180acbeebfcd69a7f8ffd08`

Para buscar en la DLQ
`zscan deadletter:contacts_v1 0 MATCH f56e30f4b180acbeebfcd69a7f8ffd08`

Para buscar en la retries queue
`hget deadletter_retries:contacts_v1 e158c66d50411d5ecc329a6c0a081b70`

Para saber el size en la block_identifiers queue 
`LLEN block_identifiers`

