GDScript client library for [SimpleNetSyncServer](https://github.com/GeeTwentyFive/SimpleNetSyncServer)


# Usage example

```py
var sns: SimpleNetSync
var local_client_state := 0


func _ready() -> void:
	sns = SimpleNetSync.create("::1", 55555)
	print("Local ID: " + str(sns.local_id))

func _process(_delta: float) -> void:
	print(sns.states)
	local_client_state += 1
	sns.send(str(local_client_state))
	await get_tree().create_timer(0.1).timeout
```


# API

- Constructor: `var sns = SimpleNetSync.create(server_ip, server_port)`
- State of all clients (as `{int: str}` dictionary, where `int` is client ID, and `str` is state): `sns.state`
- Local client ID: `sns.local_id`
- Update local client's state on server: `sns.send(LOCAL_STATE)`