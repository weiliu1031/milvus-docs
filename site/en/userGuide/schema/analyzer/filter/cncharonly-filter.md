---
id: cncharonly-filter.md
title: Cncharonly​ Filter
summary: The `cnalphanumonly` filter removes tokens that contain any characters other than Chinese characters, English letters, or digits.​
---

# Cncharonly​

The `cncharonly` filter removes tokens that contain any non-Chinese characters. This filter is useful when you want to focus solely on Chinese text, filtering out any tokens that contain other scripts, numbers, or symbols.​

## Configuration​

The `cncharonly` filter is built into Milvus. To use it, simply specify its name in the `filter` section within `analyzer_params`.​

```python
analyzer_params = {​
    "tokenizer": "standard",​
    "filter": ["cncharonly"],​
}​
```

The `cncharonly` filter operates on the terms generated by the tokenizer, so it must be used in combination with a tokenizer.

After defining `analyzer_params`, you can apply them to a `VARCHAR` field when defining a collection schema. This allows Milvus to process the text in that field using the specified analyzer for efficient tokenization and filtering. For details, refer to [Example use](analyzer-overview.md#Example-use).​

## Example output​

Here’s an example of how the `cncharonly` filter processes text:​

**Original text**:​

```python
"Milvus 是 LF AI & Data Foundation 下的一个开源项目，以 Apache 2.0 许可发布。"​
```

**Expected output**:​

```python
["是", "下", "的", "一个", "开源", "项目", "以", "许可", "发布"]​
```