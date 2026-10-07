
### Five connected clients and broadcast — 2026-10-07
Environment: CentOS, TCP port 10754.
Connected users: alice, bob, carol, dave and erin.
Alice's LIST response included all five users with NID:5847.
Alice sent BCAST Five-client test IT23584754 and received OK SENT.
Bob, Carol, Dave and Erin each received the matching MSG BCAST.
Result: PASS for five simultaneous connections and broadcast delivery.

### Port and connection evidence — 2026-10-07
ss confirmed server_4754 listening on 0.0.0.0:10754 and five established server-side TCP connections.
Result: PASS.

### Binary room transfer and isolation — 2026-10-07
erin, dave and Carol joined binarylab; alice and bob remained outside.
erin sent room_binary_4754.bin containing 4754 bytes, including all byte values from 0 to 255.
dave and carol each received 4754 bytes. cmp confirmed that the server copy and both recipient copies matched the original.
alice and bob displayed no file receipt, and neither had the file in their receive directory.
Result: PASS.

### Abrupt disconnect and room membership cleanup — 2026-10-07
Carol's client was stopped with Ctrl+C while joined to binarylab.
Alice received MSG INFO carol LEFT, and LIST showed only alice,bob,dave,erin.
Carol reconnected and registered successfully. RMSG binarylab returned ERR 005 NOT_IN_ROOM, confirming that the old membership was removed.
After JOIN binarylab, Carol's room message reached Alice and Bob. Dave and Erin received presence notifications but no room message.
Result: PASS.
