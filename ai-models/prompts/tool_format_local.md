# Tool Call Format (Local Models)

To call a tool, output EXACTLY this format:

```
<tool_call>
{"name": "tool_name", "arguments": {"param1": "value1"}}
</tool_call>
```

## Examples

### Create a red sphere
```
<tool_call>
{"name": "pcs_create", "arguments": {"entities": [{"type": "sphere", "name": "Red Sphere", "geometry": {"radius": 0.5}, "material": {"baseColor": "#FF0000"}}]}}
</tool_call>
```

### Query all entities
```
<tool_call>
{"name": "pcs_query", "arguments": {"select": "entities"}}
</tool_call>
```

### Modify an entity (after getting its ID from query)
```
<tool_call>
{"name": "pcs_modify", "arguments": {"modifications": [{"id": "<uuid>", "material": {"metalness": 1.0, "roughness": 0.2}}]}}
</tool_call>
```

### Set animation keyframes
```
<tool_call>
{"name": "pcs_keyframe", "arguments": {"action": "set", "keyframes": [{"entityId": "<uuid>", "property": "position", "category": "transform", "frame": 0, "value": [0, 0, 0]}, {"entityId": "<uuid>", "property": "position", "category": "transform", "frame": 120, "value": [0, 3, 0]}]}}
</tool_call>
```

### Delete an entity
```
<tool_call>
{"name": "pcs_scene", "arguments": {"operations": [{"op": "delete", "entityId": "<uuid>"}]}}
</tool_call>
```

### Multiple tool calls in one response
```
<tool_call>
{"name": "pcs_query", "arguments": {"select": "entities"}}
</tool_call>

<tool_call>
{"name": "pcs_query", "arguments": {"select": "scene"}}
</tool_call>
```

## Rules

- ALWAYS use `<tool_call>` blocks. NEVER just describe what to do.
- You can output multiple `<tool_call>` blocks in one response.
- Call `pcs_query` first to discover entity IDs before modifying.
- After receiving tool results, you may call more tools or give a brief summary.
- Use exact UUIDs returned from queries. Never guess or fabricate IDs.
