# valorant_offsets

These are all the offsets you need for creating a valorant cheat with esp and aimbot.

For world decryption include https://github.com/zieserl/valorant_offsets/blob/main/uworld_decryption.h and add this method to your main, call it with the process id and base address of valorant and you get the decrypted uworld ptr.
```cpp
uintptr_t decrypt_uworld(uintptr_t pid, uintptr_t val_base) {
	const auto key = read_memory<uintptr_t>(pid, val_base + uworld_key);
	struct State
	{
		uintptr_t keys[7];
	};
	const auto state = read_memory<State>(pid, valBase + uworld_state);
	const auto uworld = decrypt_uworld(key, (const uintptr_t*)&state);
	return read_memory<uintptr_t>(pid, uworld);
}
```
