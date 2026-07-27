# Monster Remote compatibility profiles

`watch_requests_offsets.json` is the exact profile document bundled into the
Android Helper and iOS app. Its `.sig` sidecar is an Ed25519 signature over the
unchanged JSON bytes.

Publish only with:

```sh
python3 tools/publish_offset_profiles.py \
  --profiles app/src/main/assets/watch_requests_offsets.json \
  --private-key /secure/path/monster_remote_profile_signing_private.pem \
  --output-dir remote
```

Never commit the private key. The app rejects a changed JSON document unless
its signature verifies against the pinned public key.
