# Spark _(pspark)_

Question and answer records with ids that any machine can recompute.

Spark is for a person or an agent who keeps context in a file next to the code. Each record is one question and one answer. The id is the last 16 characters of a SHA-256 hash of one JSON object. That object holds the answer, the question, and the type, with keys in alphabetical order and no extra whitespace. Use Spark when the question and the answer identify the note, and the file may move between directories.

The repository is named pspark. The format is named Spark. This repository is the remaining copy. The earlier spark repositories were deleted.

## Install

Clone the repository.

```bash
git clone https://github.com/gdsrvnt/pspark.git
cd pspark
```

### Dependencies

Install [uv](https://docs.astral.sh/uv/getting-started/installation/). uv installs a Python interpreter that satisfies the `requires-python` line in `spark_id.py`.

## Usage

### CLI

From the repository root, check that every stored id matches its question and answer.

```bash
uv run spark_id.py spark.json
```

Exit code 0 and no output means the file matches. The sample record id is `107ee97d1abd8e36`.

Check `spark.json` against `spark.schema.json`.

```bash
uvx check-jsonschema --schemafile spark.schema.json spark.json
```

Run the placeholder binary. It exits 0 and writes nothing.

```bash
bin/spark
```

## Format

`spark.json` is a JSON array. Each object has four keys.

| Key | Rule |
| --- | --- |
| `type` | The string `SPARK` |
| `question` | A string |
| `answer` | A string |
| `id` | 16 lowercase hexadecimal characters |

`spark_id.py` hashes `question` and `answer` only. It writes one JSON object with the keys `answer`, `question`, and `type`, in alphabetical order, with no extra whitespace. The bytes are UTF-8. `spark_id.py` does not trim strings, and it does not apply Unicode normalization. The `id` is the last 16 characters of the SHA-256 hexadecimal digest. The stored id is not one of the hashed bytes.

The same question and answer produce the same id on every machine. `connect` in `spark_id.py` unions records that `load` already returned. It does not walk a directory. The same id with a different question or answer is an error.

`spark.schema.json` checks the array shape. The hash check stays in `spark_id.py`. The schema `$id` is `https://raw.githubusercontent.com/gdsrvnt/pspark/main/spark.schema.json`.

`bin/spark` is a placeholder. It has no features.

`SKILL.md` is an agent skill that uses the name SPARK. That file is not a `spark.json` record.

## Contributing

Questions go to [GitHub issues](https://github.com/gdsrvnt/pspark/issues). Pull requests are accepted.

Before you open a pull request, run both checks in Usage. When a record fails, fix the record. When the id rule changes, change `spark_id.py` in the same pull request.

## License

License: not yet chosen.

The SPDX license identifier is UNLICENSED. No license owner is named.
