# Sparks

> Spark is a way of engineering the context of a project or a repository in such a fashion that makes the information have three things that current approaches to context management don't have.

## Background

The point of Spark is to improve context engineering in three ways that no existing paradigm achieves.

### Human prose is primary

#### User and human prose

There's a lot of craft encoded in the prose of highly technical or skilled humans, and the more of this voice exists in the context window of an agent working on any task, the better the agent adheres to desired behaviors.

One of the shortcomings of current approaches to context management is that the sources of context that are created, whether they are AGENTS.md files, some other kind of knowledge store, or even documentation, is not written by the engineers who commissioned the creation of such documents by agents. This is degenerate; because a human being passes understanding to agents in the form of prose which is then compiled into context files by an agent. This process is doubly lossy:

1. Summarization and paraphrasing are always lossy.

2. The assumptions and understandings underpinning the assertions themselves are typically not preserved by agents when creating or maintaining docs because *agents care more about what is than how it became*.

This is problematic because the same state in two projects, if a change needs to be made, are not treated the same by each team if the paths to that same state were radically different.

> Understanding how things came to be the way that they are is important for projecting current truth onto future action.

Spark addresses this in 2 ways.

### 1. Spark is verbatim-driven

The verbatim prose of a human being is an asset. Spark persists context as user prose, whether out of written session transcripts or voice session transcripts over calls. The prose itself is elicited out of the user by specific means or mined  from transcripts and discussed cooperatively. 

Spark leans on the human practitioner to give clear, unambiguous and confident statements about the project. In so doing, *it demands more of the user than any other framework*.

> Agents tend to copy the conventions, rigor, and semantics of surrounding code when working in code. Since they think in *prose*, surround them with yours.

### 2. Spark encodes context as Question-Answer pairs

Spark makes pieces of context and truths about the project easier to correlate by representing them as QA pairs. Existing context-management paradigms give an agent information, but because the agent does not know what gave it rise, it does not act on it desirably when judgment in correlating facts is required at implantation time. By representing context as QA pairs, Spark natively binds rules to rationale, decisions to their assumptions, and facts to their relevance.


## How Spark works

By grouping context into categories and question answer pairs, it makes it easier for the agent to determine what matters. Spark is highly opinionated about what it is that matters. It also makes it easier for the agent to elicit such things from the user.

### sparks.json

Spark files represent context as question and answer pairs. The question can be asked by an agent or seeded by a human to encode even more intent.

sparks.json files in any directory apply globally to a project by default. The user decides if and how to scope them.

A sparks.json includes any number of entries, json objects with a type of "s", "p", "a", "r", or "k".

### entry types

#### S: Stack

The S stands for stack, and Spark entries of type S address the actual stack constituents, the tooling, the dependencies; they answer architecture questions too. They're question answer pairs relating to the stack of the project. Ideally, in a given directory, the sparks .json, the sparks file should hold question answer pairs that pertain to stack questions in that particular directory. Again, optional.


#### P: Productization

How is this packaged, branded, presented and shipped? Why, when, who, where <all of those things>?

#### A: Art and design

Facts about the sensory footprint of the project.

#### R: Risks and rumblings

In an ever-changing world, every project is at some risk.

R is questions pertaining to how the ever-changingness of the world has implications on the project. If, for example, I was working on an open source version of TypeSafe AI's Jev model, then something appropriate to put in this field would be some notes about what other competitors are doing. But it's also a good place to put questions about changes and developments in the domain of the project that might have some implication on the project lifecycle.

#### K: Knowledge sources

K is the last one. And K is one of the most powerful types of SPARK entry. K is knowledge sources. It doesn't just enumerate knowledge sources and leave the agent to do with them what it will. No. K is very useful because it allows a knowledge source to be assigned more than one job, but for that to be done very gracefully and depending on the question and the QA pair that holds a knowledge source. The agent will know how to query a particular knowledge source for a particular task at that particular moment in time. It will increase the accuracy of when agents pull context from non-SPARK sources, and it will also improve how agents query those sources once they get to them, which is way better than using index files, which most context management systems rely on right now.

### Five or six types of data

Spark also helps to keep a project on the rails because it unironically does encompass the six things that are most important about project management. It's five types or six types of data at large that together make up pretty much all the domains of data that a project needs to have.

## Install

Clone the repository.

```bash
git clone https://github.com/gdsrvnt/spark.git
cd spark
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

The id rules and the `bin/spark` placeholder are in [Format](docs/format.md).

## Contributing

Questions go to [GitHub issues](https://github.com/gdsrvnt/spark/issues). Pull requests are accepted.

Before you open a pull request, run both checks in Usage. When a record fails, fix the record. When the id rule changes, change `spark_id.py` in the same pull request.

## License

License: not yet chosen.

The SPDX license identifier is UNLICENSED. No license owner is named.
