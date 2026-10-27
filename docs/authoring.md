# Write and check a recipe

Install Cube from source using its
[installation guide](https://github.com/cubearc/cube/blob/main/docs/installation.md).
This original example encodes bytes as hexadecimal and decodes them again.
Save it as `roundtrip.json` in a scratch directory:

```json
{
  "format_version": 1,
  "engine_api": 1,
  "input": {"source": "slot", "name": "payload", "type": "bytes"},
  "output": {"type": "bytes"},
  "steps": [
    {"operation": "encoding.hex.encode", "version": 1},
    {"operation": "encoding.hex.decode", "version": 1}
  ]
}
```

Validate the plan, run it with two explicit bytes, then compare the typed result:

```sh
cube recipe validate roundtrip.json
cube recipe run roundtrip.json --hex payload=00ff --format raw --output result.bin
cube recipe check roundtrip.json --hex payload=00ff --expect '{"type":"bytes","base64":"AP8="}'
```

`result.bin` contains the two bytes `00 ff`. Choose a new output path.
The [Cube pipeline guide](https://github.com/cubearc/cube/blob/main/docs/guides/pipelines.md)
shows other bindings and composed inspections.
Validation checks the plan; a compatibility check executes it and compares its
typed output with a supplied expected value.

## Document a contribution

State the task, inputs and prerequisites before the steps. Include one minimal
invocation, expected output, relevant limits and the exact engine/adapter versions
used. Keep shared operation semantics in the Cube reference.

Use known original fixtures. An incompatible expected result must fail the check.
Recipe versions and adapter versions are separate compatibility contracts from a
package release. See the [recipe reference](https://github.com/cubearc/cube/blob/main/docs/reference/topics/compose-operations.md#recipe-files)
for the supported format and limits.
