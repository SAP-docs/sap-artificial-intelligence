<!-- loiobb3d4f87034e4995b5f17d3f2acc090e -->

# Variable Mapping

Variable mapping enables you to align variable names between prompts and test datasets, ensuring correct data flow even when attribute names differ. Use this feature to resolve naming mismatches and maintain consistency in automated prompt optimization workflows.

Variable mappings map properties in the prompt optimization configuration to attributes in the test data set. By default, variable names in the prompt templates are matched against the attribute names in the test dataset. Where variable names and test data attribute names are mismatched, mapping is required.

In the following example, the keys `user_query` and `context` reference items in a prompt, and values `input_text` and `background_info` reference dataset fields. These are mapped through key-value pairs.

Variable mappings are provided as a JSON dictionary in the following format:

```
{"user_query": "input_text", "context": "background_info"}
```

