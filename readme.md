File utama:

1. player.py ==> enkapsulasi player. semua logika player ada disini
2. main_singleplayer ==> buat test game tanpa butuh server.
3. main_multiplayer ==> implementasinya mirip yang pac, dimana harus enter id pemain buat masuk dulu. karena belum ada server, belum pernah dicoba.

Yang harus diimplementasi di server:

```python
    def get_all_player_ids(self):
        command = "get_players"
        result = self.send_command(command)
        if result and result.get('status') == 'OK':
            return result.get('players', [])
        return []

    def get_player_state(self, player_id):
        command = f"get_player_state {player_id}"
        return self.send_command(command)

    def set_player_state(self, player_id, state):
        # Ubah state dict menjadi string JSON yang aman untuk URL
        state_json_string = json.dumps(state)
        command = f"set_player_state {player_id} {state_json_string}"
        self.send_command(command)
```

