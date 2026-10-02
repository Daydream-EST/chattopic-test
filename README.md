# ChatTopic TASK012 remote fixtures

Public experimental data for the VRChat ChatTopicSystem feasibility study.
These files are not a production endpoint or a change to the offline Prefab.

- `latest.json`: initial manifest locks new instances to experimental version 300.
- `slots/slot-0-*.json`: immutable version 300, 150 approved topics.
- `slots/slot-1-*.json`: immutable version 301, 149 topics (last topic excluded in this experiment only).
- `fixed/*.json`: each language retains both complete versions.
- `stages/latest-301.json`: promotion fixture; copy to latest.json only during the controlled update test.
- `cache-probe.json`, `stages/cache-probe-2.json`: controlled same-URL cache test.
- `failures/`: deliberately invalid digest/version examples. A missing path tests HTTP 404.

Existing instances must retain their selected version, slot and contentHash. Do not replace/delete a slot while an old instance may use it. The fixed route must retain all referenced versions as well.

Packet contentHash is SHA-256 of the canonical full five-language source records (UTF-8, sorted JSON keys, compact separators, ID ascending). payload is a JSON string containing one language's ordered ID/category/text records. payloadDigest is decimal FNV-1a 32 over UTF-16LE bytes of that string and is also bound in the manifest. It detects accidental inconsistency and is not a cryptographic security mechanism. All traffic uses HTTPS; hostile-source authentication is outside this experiment.

Content texts are copied from the user's reviewed topic pack. No application code, fonts, Unity project settings or credentials are published here.
